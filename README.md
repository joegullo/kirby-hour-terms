# Hour Terms

> A self-hosted freelancer workspace, shipped as a single Kirby plugin.
> **Set the boundaries. Get to the things that matter most.**

Hour Terms turns your Kirby installation into a complete operations layer for solo freelance work — tasks, projects, time tracking, contracts, invoicing, client messaging, scheduling, and a branded client portal. Drop-in install. No database. No build step. Your data stays on your server.

**[Buy a license →](https://hourterms.com/#pf-pricing)** **[Try the demo →](https://hourterms.com/demo)** **[Read the docs →](https://hourterms.com/docs/)**

---

## What it does

A single Kirby plugin that powers both an **admin shell** for the freelancer and a **branded client portal** for each of their clients.

**For the freelancer (admin shell at `/hour-terms`):**

- Tasks & Projects — unified workspace with priorities, subtasks, drag-and-drop, scope tracking, budget alerts
- Time Tracking — sidebar timer, break tracking, manual entries, CSV export, invoice-ready PDF reports
- Expenses — categorised, tax-deductible flag, attached to client/project, rolled into the accountant export
- Calendar — month/week/day/agenda views, recurring events, subscribe to external iCal feeds
- Contracts & Signing — generate from templates, digital signature with SHA-256 document hash + audit trail (IP, user agent, timestamp), countersign workflow, PDF export
- Quoting & Invoicing — saved quotes, recurring invoices (with MRR forecast tile), multi-currency, public invoice links, Stripe Checkout
- Client Management — relationship health scoring, follow-up reminders, revenue tracking
- Quiet Coach & Smart Nudges — scope-creep detection, stale-quote follow-ups, "Do this next" dashboard panel ranking the day's most actionable items
- Weekly Reflection — weekly review prompts, goals tracker, "proud of" list

**For your clients (portal at `/hour-terms/portal/{token}`):**

- View project health, approve or decline quotes and agreements, send messages
- Book meetings; the freelancer accepts/declines from their inbox
- Pay invoices and deposits via Stripe Checkout
- Sign contracts in-browser (audit-trailed)
- All via a secure magic link — no account creation, no password

**Built in from line one:**

- WCAG 2.2 AAA contrast in both light and dark themes; AA-level overall conformance (see Accessibility statement at hourterms.com/accessibility.html for the partial-AAA detail)
- GDPR right-to-erasure with anonymization for tax records
- Six authentication contexts — admin Panel session, PWA cookie, portal magic-link, public invoice token, booking widget secret, collab token — each with a documented threat model
- AES-256-GCM encryption for sensitive fields at rest

---

## Pricing & licensing

Hour Terms is commercial software. The full source code is not distributed publicly — buy a license to install on your server.

| Tier | Price | Includes |
|---|---|---|
| **Freelancer** | €99 one-time | One install. Every feature unlocked. 12 months of free updates. Keep your version forever after. |
| **Agency** | €249 one-time | Up to 5 named freelancers within one organization. Priority email support. |
| **Managed Install** | €299 setup + €49/mo | I install and operate Hour Terms on your hosting. Capped at 30 active clients per install. (Waitlist-only.) |

**Buy at [hourterms.com](https://hourterms.com/#pf-pricing).** Payments processed by Stripe. 14-day refund window. Invoices issued by Joe Gullo Digital B.V. (KVK 98746375, Pieterskerk-Choorsteeg 15, 2311 TR Leiden, NL).

A free public **demo** is available at <https://hourterms.com/demo>.

---

## Requirements

- **Kirby 5.0 or higher**
- **PHP 8.2 or higher**
- **PHP-FPM** runtime (the default on virtually all shared hosting)
- **SMTP credentials** recommended for reliable email delivery
- **A valid Hour Terms license key**

---

## Installation

After purchase, you receive a download link by email containing `hour-terms.zip`.

1. Unzip into `site/plugins/` so the result is `site/plugins/hour-terms/` (the unzipped folder must contain `index.php` directly)
2. Reload any admin page once. The Hour Terms admin shell will be available at `/hour-terms`
3. Open the admin shell, navigate to **Settings → License**, and enter your license key
4. Complete the rest of first-run setup (profile, billing, SMTP, integrations)

That's it. No Composer, no database, no build step. The ZIP contains everything needed. See the [full Docs & Install Guide](https://hourterms.com/docs/) for host-specific walkthroughs and troubleshooting.

---

## Updates

Hour Terms receives free updates for 12 months from your purchase date. New versions are distributed through:

- **This GitHub repo's [Releases page](https://github.com/joegullo/kirby-hour-terms/releases)** — license-gated download links
- **Email notifications** when major releases ship (if you opted in)

Kirby's built-in update check will surface new versions in your Panel's **System** view. To update:

1. Download the latest `hour-terms.zip`
2. Delete the old `site/plugins/hour-terms/` directory
3. Unzip the new version in its place
4. Reload — your data and settings persist automatically

Hour Terms also includes a built-in **Check for updates** button in **Settings → License** — it checks hourterms.com for a newer version and flags PHP/Kirby compatibility before you upgrade.

After your 12-month window expires, you keep your installed version indefinitely; further updates require renewal at the current renewal rate.

---

## Documentation

Documentation lives at **<https://hourterms.com/docs/>** — installation, licensing, host walkthroughs, updating, and troubleshooting. More reference material is added there as it's written.

---

## Support

- **General questions, refunds, GDPR / data requests:** email <hello@hourterms.com>
- **Bug reports + security issues:** email <support@hourterms.com> — typical reply within 5 business days during your 12-month support window. Agency-tier customers get priority routing on the same queue.
- **Status page:** <https://joegullo.github.io/hourterms-status>

**Issues on this repository are disabled.** Hour Terms is commercial software with private development. Bug reports and feature requests come through email, not through public issues.

---

## Versioning

Hour Terms follows [semantic versioning](https://semver.org/):

- **Patch releases** (1.0.x) — security fixes and bug fixes, free for all license holders
- **Minor releases** (1.x.0) — new features, free during your 12-month update window
- **Major releases** (x.0.0) — significant changes, free during your update window; upgrade pricing applies after

See [CHANGELOG.md](./CHANGELOG.md) for the full release history.

---

## Why "Hour Terms"?

The name has two halves. **Hour** — your time, the literal unit of freelance work. **Terms** — the conditions you set for how your time gets used. Together: the terms of your hours, the contract you make with yourself about how your work will run.

That's the product in two words.

---

## Credits & seller information

Hour Terms is built and maintained by **Joe Gullo Digital B.V.** — a Dutch private limited company (KVK 98746375), based in Leiden, NL. Founded and operated by [Joe Gullo](https://joegullo.com).

Built for the [Kirby CMS](https://getkirby.com) by Bastian Allgeier and the Kirby team.

---

## License

Commercial — see [LICENSE](./LICENSE) for full terms.

Hour Terms is licensed, not sold. You may use it on the number of installs your license permits, modify it for your own use, and keep using your licensed version indefinitely. You may not redistribute it, sublicense it, or use it without a valid license key.

The source code is not publicly available. The repository exists for distribution metadata, version detection, and release artifacts. To buy a license or evaluate the product, visit <https://hourterms.com>.
