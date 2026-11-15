# Platform Publishing Integration Notes

Use official APIs and current platform documentation. API availability, account eligibility, permissions, quotas and review requirements change; verify them before implementation.

## YouTube
Target: YouTube Shorts via the official YouTube Data API video upload flow. Use OAuth 2.0, upload processing status checks and confirmed video IDs/URLs. Verify current Shorts specifications and API quota rules.

## Instagram
Target: Instagram Reels and, where supported, image publishing through the official Instagram professional-account publishing API. Confirm eligible Business/Creator account, linked assets, permissions, media-container processing and publish status.

## Facebook
Target: Facebook Page video/Reel and image publishing through the official Meta Graph API. Confirm Page role, app permissions, token validity and media publishing endpoint.

## LinkedIn
Target: member or organisation posts with native video/image media through official LinkedIn APIs. Confirm the intended identity, product access and required permissions.

## Common safety requirements
- Never request or store a user's password.
- Use OAuth and minimum required scopes.
- Keep tokens out of source control, logs and prompts.
- Keep separate credentials per platform and environment.
- Check rate limits and quotas.
- Use idempotency/deduplication to prevent duplicate publishing.
- Treat upload accepted, upload processing and post published as distinct states.
- Save the returned post ID and canonical URL only after confirmation.
- If a permission or app review is pending, mark integration as blocked; do not simulate success.
