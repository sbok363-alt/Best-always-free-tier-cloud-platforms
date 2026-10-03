# 2026 screening — actually useful free cloud platforms

Verified against official provider pages on 2026-10-03. The upstream README was written around 2021, so its quotas and conclusions should not be treated as current.

## Keep / useful

### 1. Cloudflare Workers — STRONG KEEP
**Best current general-purpose always-free option in this repo.**

Why it survives:
- Workers Free: 100,000 requests/day.
- Static assets are free and unlimited.
- 3,000 build minutes/month.
- Hyperdrive is available on Free, with 100,000 database queries/day.
- Workers AI includes 10,000 Neurons/day at no charge.

Caveats:
- Free Worker CPU time is tight (10 ms/request), so this is better for edge APIs, routing, lightweight server logic, auth/proxy layers, cron-style jobs and static/full-stack edge apps than CPU-heavy workloads.

Official sources:
- https://developers.cloudflare.com/workers/platform/limits/
- https://developers.cloudflare.com/workers/platform/pricing/
- https://developers.cloudflare.com/workers/static-assets/billing-and-limitations/
- https://developers.cloudflare.com/workers-ai/platform/pricing/

### 2. Netlify — KEEP
**Still a good zero-cost web-app platform, especially if a project is already deployed there.**

Current Free plan:
- $0 forever.
- 300 usage credits/month.
- Git/API deploys, deploy previews, Functions, AI models, Netlify Database, Blob storage, custom domains/SSL and CDN.
- Hard cap on Free: when credits are exhausted, projects pause until the next cycle.

Verdict: Good default for small React/Vite apps and lightweight server functions. Do not migrate away just because another platform has a larger headline quota.

Official sources:
- https://www.netlify.com/pricing/
- https://docs.netlify.com/manage/accounts-and-billing/billing/billing-for-credit-based-plans/credit-based-pricing-plans/

### 3. Google Cloud Run — KEEP, SITUATIONAL
**Best candidate here when a lightweight serverless host stops being enough and you need a real containerized backend.**

Current free usage includes:
- 2 million requests/month under request-based billing.
- Free CPU and memory allowances every month.
- Scales to zero.
- Supports normal languages/frameworks and containers.

Caveats:
- Requires a Google Cloud billing account; signup requires a valid payment method.
- More infrastructure/billing complexity than Netlify or Cloudflare.

Verdict: Strong escalation path, not the first choice for a small project.

Official sources:
- https://cloud.google.com/run
- https://cloud.google.com/free/docs/free-cloud-features

### 4. Vercel Hobby — KEEP FOR PERSONAL PROJECTS
**Technically strong free tier, but the license/plan restriction matters.**

Current Hobby allowances include:
- $0/month.
- 1,000,000 function invocations/month.
- 4 CPU-hours and 360 GB-hours provisioned memory.
- Built-in CI/CD, CDN, HTTPS and previews.

Major caveat:
- Hobby is restricted to non-commercial personal use. Commercial projects require Pro or Enterprise.

Verdict: Excellent for personal experiments; weak primary choice for anything that may become commercial.

Official sources:
- https://vercel.com/docs/plans/hobby
- https://vercel.com/docs/limits/fair-use-guidelines

### 5. Oracle Cloud Always Free — KEEP AS A NICHE OPTION
**Still one of the few ways to get genuinely always-free VM-style infrastructure.**

Why it survives:
- Always Free services have no fixed end date.
- Includes AMD and Arm/Ampere compute plus storage/database/network services within limits.

Caveats:
- Requires credit/debit card verification.
- Accounts inactive for 30+ days can be treated as abandoned and may be suspended/terminated.
- More setup/ops burden than modern serverless platforms.

Verdict: Worth remembering specifically when a real VM is needed for $0. Not a default app-hosting recommendation.

Official sources:
- https://www.oracle.com/cloud/free/
- https://www.oracle.com/cloud/free/faq/

## Hold / only when there is a specific reason

### AWS — HOLD
AWS changed its free program substantially. New customers can get up to $200 in credits and a Free account plan for up to 6 months, plus 30+ services with always-free monthly allowances.

This is useful for learning AWS or temporarily testing AWS-specific services, but it is not a clean replacement for an always-free app host. The operational surface is also much larger than Cloudflare/Netlify/Vercel.

Official sources:
- https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/free-tier.html
- https://aws.amazon.com/free/free-tier-faqs/

## Remove from an "always free hosting" shortlist

### Fly.io — REMOVE
The old README's "3 free VMs" claim is obsolete.

Current trial:
- 2 total VM hours OR 7 days, whichever comes first.
- After the trial, a payment method is required and Machines are billed.

Official sources:
- https://fly.io/docs/about/free-trial/
- https://fly.io/docs/about/pricing/

### Heroku — REMOVE
Free dynos ended on 2022-11-28. The cheapest current Eco dyno plan is $5/month for 1,000 shared dyno hours.

Official sources:
- https://devcenter.heroku.com/changelog-items/2502
- https://www.heroku.com/pricing/

### IBM Cloud — REMOVE AS A DEFAULT RECOMMENDATION
IBM still has Lite/Free service plans, but current signup asks for credit-card information and the platform is positioned mainly for free POCs/learning. It offers no compelling advantage here over the surviving options.

Official source:
- https://cloud.ibm.com/docs/overview?topic=overview-tutorial-try-for-free

### Azure — REMOVE AS A DEFAULT RECOMMENDATION
Azure has 65+ always-free services and a new-customer free offer, but continuing past the initial free-account period requires moving to pay-as-you-go, and card verification is part of signup. For the use cases covered by this repo, it adds complexity without a unique advantage over the shortlist above.

Official source:
- https://azure.microsoft.com/en-us/pricing/purchase-options/azure-account

## Practical ranking

1. **Cloudflare Workers** — best new free-first platform to investigate.
2. **Netlify** — best if already using it / for simple web + functions.
3. **Google Cloud Run** — best escalation path for a normal backend/container.
4. **Vercel Hobby** — excellent personal-project tier; avoid as the base for a future commercial product.
5. **Oracle Always Free** — best $0 VM option when you specifically need a VM.
6. **AWS** — useful lab/ecosystem access, not a default free host.

## Bottom line

The original repo is useful as historical discovery material, not as a current recommendation list. In 2026 the strongest genuinely useful candidates from it are **Cloudflare Workers, Netlify, Cloud Run, Vercel Hobby and Oracle Always Free**. Fly.io and Heroku should no longer appear as always-free hosting recommendations.