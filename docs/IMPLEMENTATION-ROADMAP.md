# Implementation Roadmap

## Phase 0 — Repository and skill
- Maintain the public repository `global-media-operations`; keep secrets, real brand configuration, and private knowledge files out of version control.
- Add the skill at `.claude/skills/media-operations/SKILL.md` and its reference playbooks.
- Open the repository in Claude Code and verify the skill is discovered.
- Keep ADMINX credentials and source code out of this project.

## Phase 1 — Local foundation and operations
- Inspect available machine/runtime and choose a supported local development setup.
- Add Node.js project structure for Remotion.
- Add FFmpeg checks and a reproducible render command.
- Add n8n Community Edition deployment instructions.
- Add structured package storage, run logs, configuration validation and a kill switch.
- Add cost, quota, storage and job-health tracking.
- No social credentials; no live publishing.

## Phase 2 — Research, trend and competitor intelligence
- Implement candidate discovery adapters and source ledger.
- Implement trend scoring, freshness, momentum and saturation signals.
- Implement an approved public competitor watchlist and observation log.
- Identify content gaps without copying protected creative work.
- Implement topic scoring and claim verification workflow.
- Add tests for stale sources, unsupported claims, weak trend evidence and duplicate topics.

## Phase 3 — Editorial, creative direction and audience intelligence
- Implement editorial brief, audience hypothesis and creative brief schemas.
- Add format selection, storyboard and platform-specific narrative adaptation.
- Add audience feedback/theme analysis using permitted aggregated or authorised data.
- Add accessibility checks for captions, contrast, readability and plain language.
- Require human review for high-risk subjects.

## Phase 4 — Multimedia production studio
- Build approved visual system and reusable SVG/React templates.
- Generate poster, infographic and thumbnail assets.
- Build a 30-second Remotion composition and reusable scene components.
- Add optional narration adapter and subtitle generation.
- Store editable source projects and asset provenance/licences.
- Add render validation, audio checks and preview-frame inspection.

## Phase 5 — Publishing integrations
- Implement one official platform integration at a time.
- Use OAuth, least-privilege scopes and protected secret storage.
- Test with private/unlisted or otherwise non-public test flows where supported.
- Verify actual returned post IDs and URLs.
- Enable live publishing only after explicit user confirmation and successful end-to-end tests.

## Phase 6 — Growth and analytics
- Collect permitted platform metrics and retain metric definitions.
- Build daily/weekly reports and platform-specific performance views.
- Implement controlled experiments for hooks, formats, timing and creative treatments.
- Add learning notes that influence future recommendations only when supported by sufficient data.
- Prohibit purchased engagement, spam and manipulative growth tactics.

## Phase 7 — Revenue intelligence
- Research official platform monetisation eligibility and terms.
- Add sponsorship/affiliate/partnership opportunity research with fit and conflict checks.
- Add disclosure tracking and editorial-commercial separation.
- Keep outreach, applications, contracts, purchases and monetisation activation disabled until explicitly approved.

## Phase 8 — Always-on community management
- Verify official API capability, account eligibility, app review and permissions for each platform surface.
- Implement webhook receivers and permitted polling adapters, durable queues, deduplication and idempotent sends.
- Build the versioned brand knowledge base, FAQ store, approved/rejected response examples and escalation policies.
- Implement intent classification, confidence/risk gates, approval queue and per-platform reply adapters.
- Add 24/7 process supervision, health checks, alerts, global/per-platform pause and credential revocation.
- Add encrypted audit logs, privacy controls, retention/deletion workflows and response-time reporting.
- Test platform-specific limitations; do not use scraping or unsupported inbox automation.
- Begin in draft-only mode, then enable auto-replies only for explicitly approved low-risk categories after supervised testing.

## Phase 9 — Seven-day supervised pilot
- Run daily production with publishing disabled or in test mode.
- Review topic quality, source traceability, visual quality, video quality and operational costs.
- Test failure recovery, duplicate prevention, kill switch and token revocation procedure.
- Fix defects and document actual capability boundaries.
- Only then consider automatic publishing for approved low-risk categories.

## Acceptance criteria
- One daily package can be generated end-to-end.
- Trend and competitor observations have source links, dates and confidence labels.
- Source claims are traceable.
- Creative brief, poster and video are actual validated files.
- Video target is met within a documented tolerance.
- Audience insights distinguish observed data from assumptions.
- Growth recommendations are based on recorded platform-specific metrics.
- Revenue research does not trigger unauthorised outreach, spending or contracts.
- Each platform's publish status is independently confirmed.
- Supported social events are monitored by an always-on runtime with uptime and failure alerts.
- Every auto-reply uses approved, versioned brand knowledge and passes confidence/risk gates.
- Sensitive, uncertain and commitment-making conversations enter the approval queue.
- Platform-specific inbox limitations and API permissions are documented and verified.
- No duplicate publication on retries.
- Costs, quotas and operational failures are logged.
- Emergency stop and credential revocation procedures are documented and tested.
- Secrets are absent from repository history.
- High-risk topics are held for human review.
- The system reports failures honestly.
