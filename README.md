# Best Fitness Juice Bar Live Feed

Static Cloudflare Pages dashboard for daily ABC Ignite POS juice bar / smoothie bar sales.

## Intended hosting

- Repository: `codylrobson/juice-bar-sales`
- Branch: `main`
- Cloudflare Pages build: no build command; output directory `/public` or repo root depending project setup.
- WordPress embed: iframe pointing to the Cloudflare Pages URL.

## Data model

The dashboard reads `public/data/juice-bar-sales.json`, generated from ABC Ignite club POS transactions and filtered to item `profitCenter` values:

- `Juice Bar`
- `Smoothie Bar`

## Refresh cadence

Daily at 5:00am America/New_York.

The refresh should pull POS transactions for each authorized ABC club and write the newest aggregate JSON. The previous published JSON should remain in place if the ABC pull fails validation.
