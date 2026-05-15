# Changelog

All notable changes to Hour Terms are documented here.

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and Hour Terms adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

This changelog is the public record of releases. Customer-facing release notes with additional context (migration guides, breaking-change explanations) are published at <https://hourterms.com/changelog>.

---

## [Unreleased]

### Planned for v1.1

- Audit log feature: customer-visible record of admin actions on managed installs
- Improved first-run onboarding

---

## [1.0.0] — 2026-05-14

Initial public release.

### Added

**Core workspace**
- Unified Tasks + Projects view with priorities, subtasks, drag-and-drop, scope tracking, budget alerts, weighted completeness
- Time tracking with sidebar timer, break tracking, project-level breakdowns, CSV export, invoice-ready PDF reports
- Expenses with categories, billable + tax-deductible flags, receipt attachment, attached to client or project, rolled into the accountant export at year-end
- Weekly Reflection: weekly review prompts, goals tracker, "proud of" list, streaks

**Client operations**
- Client management with relationship health scoring, follow-up reminders, revenue tracking, scope alerts, performance ratings
- Per-client messaging threads with rich text compose, system notifications, inbound-email piping
- Approval workflows for quotes and project changes with bidirectional admin/portal sync

**Billing & contracts**
- Saved quotes and invoices with multi-currency support
- Recurring invoices with end-date scheduling and an MRR forecast tile
- Contract templates with digital signature (SHA-256 verification) and countersign workflow
- Public invoice links with Stripe Checkout integration

**Calendar & scheduling**
- Month/week/day/agenda calendar views, recurring events with RRULE, subscribe to external iCal feeds
- Booking widget with per-meeting-type duration + price, server-computed checkout amount, rate-limited public endpoint

**Client portal**
- Branded portal at `/hour-terms/portal/{token}` with magic-link auth (no password, no account creation)
- Optional per-portal device-verification 2FA (8-char one-time code emailed to the client's contact address)
- Light/dark theme toggle

**Productivity helpers**
- Quiet Coach + Smart Nudges: scope-creep detection, stale-quote follow-ups, "Do this next" dashboard panel ranking the day's most actionable items
- Smart Prioritization factoring due dates, client value, project health, availability

**Operations & compliance**
- Single `pf_send_email()` helper with automatic SMTP / `mail()` fallback and structured error logging
- License activation and one-click "Check for updates" in admin, with new-version notifications and PHP/Kirby compatibility warnings
- Six authentication contexts — admin Panel session, PWA cookie, portal magic-link, public invoice token, booking widget secret, collab token — each with a documented threat model
- O(1) token reverse-index for portal/invoice/booking auth lookups
- Rate limiting on every state-changing endpoint
- AES-256-GCM encryption for sensitive fields at rest
- WCAG 2.2 AAA contrast in light and dark themes (admin and portal); AA-level overall conformance with documented exceptions in the accessibility statement
- Full keyboard navigation
- GDPR right-to-erasure with one-call sweep, two erasure modes, and hashed-identifier receipts
- European Accessibility Act ready

### Known limitations

- Optimized for traditional PHP-FPM. Long-running runtimes (RoadRunner, Swoole, Octane) require additional integration — see customer docs

### Configuration flags

These options live in `site/config/config.php` and matter on first install.
See the [Docs & Install Guide](https://hourterms.com/docs/) for full setup detail.

- `joegullo.project-flow.trustedProxy` (boolean, default `false`) — enable when your site sits behind Cloudflare, ploi.io's nginx, a load balancer, or any CDN. Without it, rate limits see your proxy's IP on every request and contract-signing audit records show the proxy IP rather than the signer's.

- `joegullo.project-flow.inboundEmailPipe` (boolean, default `false`) — enable to allow `pipe.php` to ingest replies from your MTA. Also requires the sentinel file `.userdata/.inbound-mail-enabled` containing `ENABLE-INBOUND-PIPE-v1`. See install docs for full setup.

- `joegullo.project-flow.bookingOrigins` (array, default `[]`) — list of origins permitted to call the public booking widget. `['*']` is no longer accepted; provide explicit origins like `['https://yourcompany.com']`.

- `joegullo.project-flow.cronToken` (string, no default) — required to enable the recurring-invoice cron at `/api/cron/recurring-invoices`. Set a long random value and configure your cron runner to pass it in `X-PF-Cron`.

- `joegullo.project-flow.writeRoles` (array, default `[]`) — when set, only Kirby user roles in this list can call state-mutating routes. Empty array (default) allows every authenticated user. Set explicitly on multi-role installs where some users should be read-only.

- `joegullo.project-flow.debugLogs` (boolean, default `false`) — set to `true` in development to surface detailed error messages in API responses. Leave off in production.

### Changed (documentation, pre-launch)

- README requirements aligned to Kirby 5 / PHP 8.2+ canonical (DOC1)
- WCAG AAA framing narrowed to contrast-only with AA overall conformance (DOC4)
- Configuration flags documented under v1.0.0 release notes (DOC10)
- Stripe terminology corrected on landing: "Direct Stripe integration" not "Stripe Connect" (DOC12)
