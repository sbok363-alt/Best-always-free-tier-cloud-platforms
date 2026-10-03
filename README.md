# Best actually-useful free cloud platforms — 2026

This fork trims the original 2021 list down to services that are still worth considering today.

**Last screened:** 2026-10-03  
**Goal:** free-first hosting/infrastructure for side projects, small apps, APIs and experiments, with as little unnecessary DevOps and lock-in as practical.

> The upstream README is historically useful, but several of its quotas and recommendations are no longer current. The original version remains available in Git history.

## Shortlist

| Rank | Platform | Verdict | Best for | Main catch |
|---|---|---|---|---|
| 1 | **Cloudflare Workers** | **STRONG KEEP** | Edge APIs, static/full-stack apps, lightweight server logic, cron/proxy/auth, some AI workloads | Free Worker CPU is only 10 ms/request |
| 2 | **Netlify** | **KEEP** | React/Vite sites, deploy previews, functions, small web apps | Free plan has a hard 300-credit/month cap; projects pause when exhausted |
| 3 | **Google Cloud Run** | **KEEP — situational** | Real containerized backends and services that need more freedom than edge/serverless hosts | Requires an active Cloud Billing account; more billing/infra complexity |
| 4 | **Vercel Hobby** | **KEEP — personal only** | Personal web apps and prototypes with excellent deployment UX | Hobby is restricted to personal/non-commercial use |
| 5 | **Oracle Cloud Always Free** | **KEEP — niche** | A real $0 VM, storage and database resources | Card normally required; idle resources/accounts can be reclaimed/suspended |

## Why these survive

### 1. Cloudflare Workers — strongest free-first option

Current Free limits/features include:

- **100,000 Worker requests/day**
- **10 ms CPU time/request**, 128 MB memory
- **Static asset requests are free and unlimited**
- **3,000 build minutes/month**
- **Hyperdrive:** 100,000 database queries/day on Free
- **Workers AI:** 10,000 Neurons/day free allocation

Caveat: some more expensive Workers AI models require the paid Workers plan even though many models remain available on Free.

Official docs:
- https://developers.cloudflare.com/workers/platform/limits/
- https://developers.cloudflare.com/workers/static-assets/billing-and-limitations/
- https://developers.cloudflare.com/workers/ci-cd/builds/limits-and-pricing/
- https://developers.cloudflare.com/hyperdrive/platform/pricing/
- https://developers.cloudflare.com/workers-ai/platform/pricing/

### 2. Netlify — still a very useful zero-cost web platform

Current Free plan:

- **$0 forever**
- **300 credits/month** with a hard limit
- Git/API deploys and deploy previews
- Functions and AI models
- Netlify Database and Blob storage
- Custom domains + SSL
- Global CDN

When the Free credit limit is reached, projects pause until the next billing cycle. That makes cost behavior predictable, but it also makes Netlify less suitable for unexpected traffic spikes.

Official docs:
- https://www.netlify.com/pricing/
- https://docs.netlify.com/manage/accounts-and-billing/billing/billing-for-credit-based-plans/credit-based-pricing-plans/

### 3. Google Cloud Run — best escalation path to a normal backend

Why it stays:

- **2 million requests/month free** under the current free allowance
- Scales to zero
- Supports normal languages/frameworks and containers
- Container build is optional for supported source deployments

Caveat: Google Cloud Free Tier requires an active Cloud Billing account. Self-serve billing accounts require a valid payment method even if usage remains within free limits.

Official docs:
- https://cloud.google.com/run
- https://cloud.google.com/run/pricing
- https://docs.cloud.google.com/free/docs/free-cloud-features

### 4. Vercel Hobby — excellent, but only for personal/non-commercial use

Why it stays:

- **$0/month** Hobby plan
- Very easy Git-based deploys
- Automatic CI/CD, CDN, WAF and managed web deployment

Hard limitation: Vercel states that Hobby is for **personal or non-commercial use**. If a project may become commercial, do not make Hobby the long-term infrastructure assumption.

Official docs:
- https://vercel.com/pricing
- https://vercel.com/legal/terms

### 5. Oracle Cloud Always Free — unusual but genuinely useful VM option

Always Free resources currently include, among other things:

- Up to **two AMD micro VMs**
- Ampere A1 allowance equivalent to **2 OCPUs + 12 GB RAM** in an Always Free tenancy
- **200 GB** combined boot/block volume storage
- Always Free database/networking resources

Caveats:

- Most users need a phone number and credit/debit card for verification.
- Oracle may reclaim Always Free compute that remains under its inactivity thresholds.
- Accounts idle for 30+ days may be treated as abandoned and become eligible for suspension/termination.

Official docs:
- https://docs.oracle.com/en-us/iaas/Content/FreeTier/freetier.htm
- https://docs.oracle.com/en-us/iaas/Content/FreeTier/freetier_topic-Always_Free_Resources.htm
- https://www.oracle.com/cloud/free/faq/

## Situational — useful only for a specific reason

### AWS

**HOLD, not default.** New users can receive $100 in credits plus up to another $100 from activities, a Free account plan for up to six months, and access to 30+ services with always-free monthly allowances.

Use it when learning AWS or when a project specifically needs the AWS ecosystem. For a small free-first app, the operational/billing surface is larger than the shortlist above.

- https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/free-tier.html

### Azure

**HOLD, not default.** Azure currently advertises 65+ always-free services, plus new-customer offers. The free account needs payment verification and requires moving to pay-as-you-go to continue beyond the initial 30-day/credit stage.

Use it when an Azure-specific service is valuable; otherwise it is more platform than a small side project usually needs.

- https://azure.microsoft.com/en-us/pricing/purchase-options/azure-account

### IBM Cloud

**HOLD, not default.** IBM still offers 40+ Lite/always-free products, but new accounts are Pay-As-You-Go accounts with card verification. Lite service instances can be deleted after 30 days without development activity.

Worth using only for IBM-specific services or experiments.

- https://www.ibm.com/products/cloud/free
- https://cloud.ibm.com/docs/account?topic=account-accounts

## Removed from the useful shortlist

### Fly.io — DROP

The old **3 free VMs** claim is obsolete. The current free trial is only **2 total VM hours or 7 days**, whichever comes first.

- https://fly.io/docs/about/free-trial/

### Heroku — DROP

Free dynos ended on **2022-11-28**. The current Eco dyno plan costs **$5/month** for 1,000 shared dyno hours.

- https://devcenter.heroku.com/changelog-items/2502
- https://www.heroku.com/pricing/

## Practical pick order

1. **Cloudflare Workers** — investigate first for new free-first projects.
2. **Netlify** — great for simple web apps and especially sensible when already deployed there.
3. **Cloud Run** — move here when you need a conventional backend/container.
4. **Vercel Hobby** — great for personal experiments, not a commercial foundation.
5. **Oracle Always Free** — use when you specifically need a real VM for $0.
6. **AWS / Azure / IBM** — choose only for ecosystem-specific reasons.

For the evidence and caveats behind the filtering, see [`SCREENING-2026.md`](./SCREENING-2026.md).
