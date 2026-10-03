# 2026 screening — useful free cloud platforms

**Verified:** 2026-10-03  
**Method:** current official provider documentation/pricing only. The upstream repository was last materially written around 2021, so old quotas and conclusions were treated as discovery leads, not current facts.

## Decision table

| Platform | Decision | Free value | Friction / risk | Best use |
|---|---|---|---|---|
| Cloudflare Workers | **STRONG KEEP** | Excellent | Tight Free CPU; some AI models require Paid | Default free-first edge/full-stack option |
| Netlify | **KEEP** | Very good | 300-credit hard cap | Small React/Vite apps, functions, previews |
| Google Cloud Run | **KEEP — situational** | Excellent backend allowance | Billing account/payment method; more infra complexity | Conventional backend/container |
| Vercel Hobby | **KEEP — personal only** | Very good | Personal/non-commercial restriction | Personal web apps/prototypes |
| Oracle Cloud Always Free | **KEEP — niche** | Excellent VM-style resources | Card verification; idle-resource/account policies | Real $0 VM/infrastructure |
| AWS | **HOLD** | Good ecosystem access | Bigger operational/billing surface | AWS-specific learning/services |
| Azure | **HOLD** | Many always-free services | Billing/pay-as-you-go complexity | Azure-specific services |
| IBM Cloud | **HOLD** | 40+ Lite/free products | Card verification; inactivity cleanup | IBM-specific services/POCs |
| Fly.io | **DROP** | Trial only | 2 VM hours or 7 days | No longer an always-free host |
| Heroku | **DROP** | No free dynos | Cheapest Eco runtime is paid | No longer an always-free host |

---

## 1. Cloudflare Workers — STRONG KEEP

This is the strongest general-purpose free-first option left in the original repo.

### Current Free value

- 100,000 Worker requests/day.
- 10 ms CPU/request and 128 MB memory on Workers Free.
- Static asset requests are free and unlimited.
- 3,000 build minutes/month.
- Hyperdrive: 100,000 database queries/day on Free.
- Workers AI: 10,000 Neurons/day free allocation.

### Caveats

- 10 ms of CPU/request makes it a poor fit for CPU-heavy server workloads.
- Some resource-intensive Workers AI models require Workers Paid even though many models remain on Free.
- Edge/serverless constraints are different from a normal long-lived server/container.

### Verdict

**Investigate first for new free-first apps.** It is especially strong for static/full-stack web apps, APIs, auth/proxy layers, lightweight server logic and globally distributed workloads.

Official sources:
- https://developers.cloudflare.com/workers/platform/limits/
- https://developers.cloudflare.com/workers/static-assets/billing-and-limitations/
- https://developers.cloudflare.com/workers/ci-cd/builds/limits-and-pricing/
- https://developers.cloudflare.com/hyperdrive/platform/pricing/
- https://developers.cloudflare.com/workers-ai/platform/pricing/

---

## 2. Netlify — KEEP

Netlify remains a very practical $0 platform for small web projects.

### Current Free value

- $0/month forever.
- 300 usage credits/month with a hard limit.
- Git/API deploys and deploy previews.
- Functions and AI models.
- Netlify Database and Blob storage.
- Custom domains/SSL and global CDN.

### Caveat

When the 300-credit limit is exhausted, Free projects pause until the next billing cycle. There is no Free-plan auto-recharge.

### Verdict

**Keep.** Particularly sensible for React/Vite apps and projects already deployed there. A migration away from Netlify only makes sense if there is a concrete limitation or cost problem.

Official sources:
- https://www.netlify.com/pricing/
- https://docs.netlify.com/manage/accounts-and-billing/billing/billing-for-credit-based-plans/credit-based-pricing-plans/

---

## 3. Google Cloud Run — KEEP, SITUATIONAL

Cloud Run is the best candidate in this list when a lightweight edge/serverless host is no longer enough.

### Current Free value

- 2 million requests/month are included in the current free allowance.
- Scales to zero.
- Supports ordinary languages/frameworks and containers.
- Source-based deployment can build the container for supported languages.

### Caveats

- Google Cloud Free Tier requires an active Cloud Billing account.
- Self-serve billing accounts need a valid payment method even if monthly usage stays at $0.
- More infrastructure and billing complexity than Cloudflare/Netlify/Vercel.

### Verdict

**Strong escalation path, not default first choice.** Use it when a project needs a conventional backend, container, broader runtime compatibility or heavier compute.

Official sources:
- https://cloud.google.com/run
- https://cloud.google.com/run/pricing
- https://docs.cloud.google.com/free/docs/free-cloud-features
- https://docs.cloud.google.com/billing/docs/how-to/payment-methods

---

## 4. Vercel Hobby — KEEP FOR PERSONAL PROJECTS

Vercel remains technically strong, but the usage restriction matters.

### Current value

- Hobby is $0/month.
- Git-based deployment, CI/CD, CDN, WAF and managed web deployment are included.

### Major caveat

Vercel states that Hobby is only for **personal or non-commercial use**.

### Verdict

**Excellent personal-project tier.** Do not treat it as the long-term infrastructure assumption for a project that may become commercial.

Official sources:
- https://vercel.com/pricing
- https://vercel.com/legal/terms

---

## 5. Oracle Cloud Always Free — KEEP AS A NICHE OPTION

Oracle is still one of the rare ways to get meaningful VM-style resources at $0 indefinitely.

### Current Always Free value

- Up to two AMD micro VMs.
- Ampere A1 allowance: 1,500 OCPU-hours and 9,000 GB-hours/month, equivalent to 2 OCPUs + 12 GB RAM for an Always Free tenancy.
- 200 GB total boot/block volume storage.
- Additional Always Free database/networking resources.

### Caveats

- Most users need phone and credit/debit-card verification.
- Oracle can reclaim inactive Always Free compute. Its documentation currently defines inactivity over a seven-day period using low CPU/network usage, plus low memory usage for A1 instances.
- Accounts idle for 30+ days may be treated as abandoned and become eligible for suspension/termination.
- Capacity for specific Always Free shapes can be constrained by region.

### Verdict

**Keep specifically for $0 VM needs.** Not the default platform for a small web app because you take on more operations work.

Official sources:
- https://docs.oracle.com/en-us/iaas/Content/FreeTier/freetier.htm
- https://docs.oracle.com/en-us/iaas/Content/FreeTier/freetier_topic-Always_Free_Resources.htm
- https://www.oracle.com/cloud/free/faq/

---

# Situational / HOLD

## AWS

AWS now gives new users $100 in credits after account creation, with up to another $100 available through activities. Its Free account plan can last up to six months, and AWS documents 30+ services with always-free monthly allowances.

**Why HOLD:** very useful for AWS-specific learning/services, but not the cleanest default free host for a small project. The service and billing surface is much larger than Cloudflare or Netlify.

Official source:
- https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/free-tier.html

## Azure

Azure currently advertises 65+ always-free services, plus new-customer free allowances and $200 credit. Continuing after the initial free-account stage requires moving to pay-as-you-go, and signup may place a temporary card authorization.

**Why HOLD:** real free value exists, but the platform is only worth the extra complexity when an Azure-specific service is useful.

Official source:
- https://azure.microsoft.com/en-us/pricing/purchase-options/azure-account

## IBM Cloud

IBM still advertises 40+ Lite/always-free products. New accounts are Pay-As-You-Go accounts and require card information for verification. IBM also states that Lite service instances can be deleted after 30 days without development activity.

**Why HOLD:** useful for IBM/Watson-specific POCs, but not compelling enough to beat the top shortlist for ordinary app hosting.

Official sources:
- https://www.ibm.com/products/cloud/free
- https://cloud.ibm.com/docs/account?topic=account-accounts

---

# DROP

## Fly.io

The old README's **3 free VMs** claim is obsolete.

Current trial:
- 2 total VM hours **or** 7 days, whichever comes first.
- Apps stop when the trial is exhausted until a payment method is added.

**Decision: DROP from any always-free shortlist.**

Official source:
- https://fly.io/docs/about/free-trial/

## Heroku

Heroku ended free dynos on 2022-11-28. The current Eco dyno plan costs $5/month for 1,000 shared dyno hours.

**Decision: DROP from any always-free shortlist.**

Official sources:
- https://devcenter.heroku.com/changelog-items/2502
- https://www.heroku.com/pricing/

---

# Practical ranking

1. **Cloudflare Workers** — strongest new free-first platform in this repo.
2. **Netlify** — excellent simple web + functions platform; keep using when it already fits.
3. **Google Cloud Run** — best next step for a conventional backend/container.
4. **Vercel Hobby** — excellent personal-project hosting, but non-commercial only.
5. **Oracle Always Free** — strongest niche option when a real VM is required for $0.
6. **AWS / Azure / IBM** — use for ecosystem-specific reasons, not by default.

## Bottom line

The original repo is useful as historical discovery material, not as a current recommendation list. The genuinely useful 2026 shortlist is **Cloudflare Workers, Netlify, Google Cloud Run, Vercel Hobby and Oracle Cloud Always Free**. **AWS, Azure and IBM** are situational. **Fly.io and Heroku** no longer qualify as always-free hosting recommendations.
