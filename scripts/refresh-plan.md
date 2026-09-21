# Daily refresh plan

## ABC clubs

- 8080 Best Fitness Danvers
- 8096 Best Fitness Fuller Road
- 8086 Best Fitness of Nashua
- 8098 Best Fitness Springfield
- 8090 Best Fitness of Drum Hill
- 8087 Best Fitness of Schenectady
- 9897 Best Fitness Corp Sales
- 8085 Best Fitness of Albany
- 8092 Best Fitness Lowell
- 48081 Best Fitness Woburn
- 8088 Best Fitness Chelmsford

## Source operation

`abc-ignite:clubs:getpostransactions`

Required runtime args discovered by test invoke:

- `clubNumber`
- `transactionTimestampRange` in `YYYY-MM-DD,YYYY-MM-DD` format
- `page`
- `size` up to 1000

## Transform rules

- Keep item lines where `profitCenter` is exactly `Juice Bar` or `Smoothie Bar`.
- Exclude returns from sales totals or store returns separately.
- Use `subtotal` as net sales, `tax` as tax, and `subtotal + tax` as gross sales.
- Publish only aggregated/item-level sales fields needed for the dashboard. Do not publish member IDs, employee IDs, card suffixes, or raw payment details.

## Publishing rules

- Write the stable dashboard files to GitHub repo `codylrobson/juice-bar-sales`.
- Cloudflare Pages should deploy from GitHub automatically.
- Keep `public/index.html` stable; update `public/data/juice-bar-sales.json` daily.
- If the ABC pull fails validation, do not overwrite the prior published JSON.
