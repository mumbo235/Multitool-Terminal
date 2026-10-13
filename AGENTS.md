# Multitool Terminal Guidelines

### Pro Tier Priority & Fallback Policy
- When configuring or calling Gemini models for Pro subscribers, default to `gemini-2.5-pro` with Pro tier priority.
- Resilient Fallback: Handle HTTP 429 (`RESOURCE_EXHAUSTED` / rate limits) and HTTP 503 (`UNAVAILABLE` / high demand capacity surges) by routing requests seamlessly to priority fallback `gemini-3.8-flash` (and `gemini-2.5-flash`), with clear user notification.
- Maintain Pro priority across requests; temporary demand failovers must not permanently demote the user's default configuration.

### Session Auto-Login Policy
- Default `autoLogin` to `true` whenever user credentials exist.
- Eliminate repeated login prompts on reload; require manual authentication only when explicitly requested via `logout`.

### Deprecated Model Policy (Gemini <= 3.6)
- Gemini versions <= 3.6 (e.g. `gemini-3.6-flash`, `gemini-3.5-flash`, `gemini-3.5-flash-lite`, `2.0`, `1.5`, `1.0`; excluding production `2.5`) are defunct and must not be used.
- Automatically intercept and upgrade legacy model references to `gemini-2.5-pro` (under Pro priority) or `gemini-3.8-flash`.
