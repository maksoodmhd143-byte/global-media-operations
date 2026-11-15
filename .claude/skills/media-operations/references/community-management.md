# Community Management Specification

## Objective
Operate a reliable 24/7 social community desk for the brand, using only official platform interfaces and user-approved response policy. This specification is an implementation target, not proof that the integrations already exist.

## Supported event types
- Direct messages/inbox events where official API permissions allow them.
- Comments and replies on the brand's content.
- Mentions, tags and notifications where exposed by the API.
- Delivery, moderation and account events where available.

Maintain a capability matrix for each platform: account type, supported event types, API endpoints, required scopes, app-review status, messaging windows, rate limits, webhook support, polling fallback, and last verification date. Never assume API parity. YouTube general private DMs are not available as a normal brand inbox; monitor supported comments/mentions. LinkedIn messaging automation is restricted and may require partner approval; never scrape personal inboxes. Meta Instagram/Facebook messaging access depends on account type, permissions and app review. Verify all current rules before enabling.

## Knowledge base and training
Suggested structure:
- `knowledge/brand-facts.yml` — approved facts and official links.
- `knowledge/faq.yml` — question, canonical answer, evidence/source, locale, approval date.
- `knowledge/voice-and-tone.md` — tone, vocabulary, language and formatting.
- `knowledge/approved-replies.yml` — examples approved by the user.
- `knowledge/rejected-replies.yml` — examples to avoid and reason.
- `knowledge/escalation-policy.yml` — risk categories, approvers and response targets.
- `knowledge/platform-rules.yml` — per-platform restrictions and response windows.

Each record must include status (draft/approved/retired), version, owner/approver and effective date. Retrieve only approved, current records for live replies. This is retrieval-based operational guidance, not model-weight training.

## Intent taxonomy
`greeting`, `thanks`, `faq`, `content_feedback`, `complaint`, `support_request`, `refund_or_dispute`, `sales_lead`, `partnership`, `sponsorship`, `press`, `employment`, `spam`, `abuse`, `safety_or_crisis`, `legal`, `privacy_request`, `security`, `unknown`.

## Default action policy
| Category | Default action |
|---|---|
| Greeting, thanks, approved FAQ | Auto-reply after test and confidence gate |
| Simple public information with approved source | Auto-reply after confidence gate |
| Content feedback | Auto-reply only if low-risk and contextual |
| Complaint, support, refund, dispute | Draft and queue for approval |
| Sales, sponsorship, partnership, press, employment | Draft and queue; no commitment |
| Legal, medical, financial, crisis, threat, personal-data or security issue | Escalate; no autonomous substantive answer |
| Spam or abuse | Apply only approved moderation policy |
| Unknown or low confidence | Ask for clarification only if safe; otherwise queue |

## Confidence and risk gates
Configure thresholds in environment/config, not hardcoded assumptions. A reply may be sent only if all are true:
1. Event and account are authentic and authorised.
2. Category is explicitly allowlisted for auto-reply.
3. Required answer is supported by current approved knowledge.
4. Confidence meets configured threshold.
5. No sensitive data, legal/financial/medical advice, allegation, crisis or commitment is involved.
6. Platform policy, messaging window and rate limits permit the reply.
7. The event has not already been answered.

If any check fails, queue for human approval. Never hallucinate missing policies or facts.

## Runtime architecture
- Webhook receiver for platforms that provide supported event subscriptions.
- Scheduled polling adapter only where officially permitted and necessary.
- Durable event queue and dead-letter queue.
- Normalisation layer with platform, account, event ID, conversation ID, author, timestamp and content.
- Deduplication and ordering controls.
- Intent/risk classifier and approved knowledge retrieval.
- Reply policy engine and draft generation.
- Human approval queue and authorised send adapter.
- Encrypted audit store and retention/deletion workflow.
- Health checks, alerts, per-platform pause and global kill switch.

Use idempotency keys based on platform event/message IDs. If send status is uncertain, reconcile with platform state before retrying. Apply exponential backoff and respect rate limits. Keep platform tokens in a secret manager or protected environment variables; never commit secrets.

## Training and correction loop
1. User supplies or edits a response example.
2. Store it as draft.
3. User approves or rejects it and optionally supplies a reason.
4. Approved examples become versioned retrieval material.
5. Future drafts retrieve relevant approved examples.
6. Track corrections and recurring failure types.
7. Do not silently convert an unreviewed conversation into a policy rule.

## Privacy and security
Minimise collected data, encrypt in transit and at rest, restrict access, log access, define retention periods, support deletion requests where possible, and do not repurpose private messages for public content or audience profiling without separate explicit approval and a lawful basis. Never request passwords, OTPs, full card details or unnecessary sensitive personal information.

## User controls
Provide: global pause, per-platform pause, auto-reply category toggles, confidence threshold, business-hours/quiet-hours settings, retention period, escalation destinations, approved knowledge editor, and an audit log. Legal, platform-policy, privacy and security safeguards cannot be disabled.

## Required metrics
Events received, unique conversations, category counts, auto-replies, approval-queue size, escalations, moderation actions, median/95th-percentile response time, uptime, API errors, rate limits, duplicate prevention events and unsupported surfaces.
