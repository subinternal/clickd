# Changelog

Versions follow semantic versioning: a major version changes what the skill asks of the person or the agent, a minor one adds or tightens steps, a patch corrects wording. The version is in `SKILL.md` under `metadata`, as the Agent Skills format keeps anything it does not define.

## 2.0.0 (2026-10-31)

- The skill is renamed clickd, from mttr. Install it with `npx skills add subinternal/clickd`, or in Claude Code with `/plugin install clickd --marketplace subinternal/clickd`. The MCP server's key in a client's config is `clickd`, and the key is read from `CLICKD_KEY`.
- Shop Ready is built in. The former `mttr-shop-ready` skill is now `references/shop-ready.md`, with its own references under `references/shop-ready/`, and step 4 sends shop and product page work there. Its history is below under its old name.
- clickd's server still runs at mttr.si: its addresses, the MCP tool names (`mttr_brief` and the rest), the API and the crawler's name `mttr` are unchanged.

Versions 1.0.0 to 1.2.1 were released as the `mttr` skill.

## 1.2.1 (2026-10-23)

- The open path names each free check at its own address, such as `/h1-checker`, where the free tools moved.
- Reading a brief says what its fifth line now names: `mttr_rescan` and `mttr_changes`, or a fresh read with no key.
- The example of a page whose kind is misread uses a sample town.

## 1.2.0 (2026-10-19)

- Step 4 checks the facts an answer quotes about a business (name, address, phone, hours, services, booking) agree everywhere they appear. We added it after reading how real answers are put together: they lean on exactly those.

## 1.1.0 (2026-10-18)

- Reading a brief and a plan: what each part of the brief means, when to depart from its order, the same read as data, and the mistakes that cost time.
- Confirming a finding: fetching what the server sends, pass and fail for the common rules, finding the one template behind many pages, worked before and after examples, and where a rule misreads a page.
- Shipping safely: a worked proposal with its limits, what each answer means, what a pull request carries, and caches after a deploy.
- Troubleshooting: checking the MCP connection by hand, and each refusal mttr gives with its cause and fix.
- After a rescan: every field of `mttr_changes`, the order to read them in, why a rule breaks, and what to do when a fix does not show.
- Steps 2, 3, 5 and 6 say what to check at that point and link the reference that goes deeper.
- Three more worked loops: a site closed to crawlers, a site whose text is written by script, and several claimed sites.
- Sources added for the MCP transport and authorization specs, Google's robots.txt, noindex, canonical, JavaScript and URL Inspection pages, and MDN's 429 and Cache-Control pages.

## 1.0.1 (2026-10-16)

- Each source is listed by its page's own title, with what the skill takes from it.

## 1.0.0 (2026-10-16)

- First release: six steps from reading the site to reading it again, over MCP at `https://mttr.si/mcp`, with approval through `mttr_propose` and a report template.
- An open path for an agent with no key: the public report, a fresh read, the rulebook and the free checks.
- A reference of every MCP tool, written from mttr's own tool list, and worked loops for a new site, one page, a pull request and a weekly check.

Versions below were released as the separate `mttr-shop-ready` skill, before it was built into this one.

## mttr-shop-ready 1.2.0 (2026-10-18)

- A new reference, `references/markup.md`: before and after JSON-LD for a plain product, a product with variants, a sale price with a strikethrough price, and the shop's shipping and returns on its `Organization`, with the rules for availability, condition, GTIN, MPN, SKU, brand, ratings and escaping, and which source wins when a policy is stated twice.
- A new reference, `references/merchant-center.md`: the feed's attributes beside the page's fields, why they must agree (automatic item updates, disapproval on a mismatch), prices and tax by country, and the feed apps on Shopify and WooCommerce.
- A new reference, `references/verify.md`: a command that prints each JSON-LD block the server sends, what each part of the check's answer means and what a pass is, Google's own tools, and a troubleshooting table of symptom, cause and fix.
- The platform notes add BigCommerce's Cornerstone theme, Magento's core microdata and a way to add a JSON-LD block, headless storefronts, a whole replacement block in Liquid, a before and after for Next.js Commerce, and a WooCommerce filter that writes a `ProductGroup`.
- Step 1 recognizes BigCommerce and headless storefronts; step 2 searches the live HTML for blocks an app or tag manager writes; step 4 adds sale prices, default-variant products and a GTIN only when it is one; step 5 checks the page against the Merchant Center feed; step 7 turns to the troubleshooting table before changing more.
- The React escape now reads `\u003c`, as it should; it had lost its backslash sequence.
- mttr's check counts a shop-wide shipping or return policy only when the `Organization` block is in the product page's own HTML, and the skill says so.

## mttr-shop-ready 1.1.1 (2026-10-16)

- Sources lists end `SKILL.md` and the platform notes, each by its page's own title, with what the skill takes from it.

## mttr-shop-ready 1.1.0 (2026-10-16)

- The description names its triggers plainly, the platforms it works on, and what it is not for.
- How the change ships is decided before any file changes, from a table of four cases, and never revisited.
- Each step opens with the one thing it does, and no file changes before step 4.
- The baseline check asks for a product with variants, one on sale and one out of stock where the shop has them.
- Step 5 reads the data from the HTML the server sends, and checks a sold-out variant and the variant the address selects.
- A refused rescan, or a site mttr has not read before, is said and reported from the product checks alone.
- A report template ends the skill, with the line that Merchant Center and Google decide.
- The platform notes were checked against current sources: Shopify's filter gives a `ProductGroup` for products with variants; Hydrogen 2026.10 no longer supports `getSeoMeta`; Next.js Commerce does not escape its JSON; WooCommerce already writes the GTIN and a `priceValidUntil`.

## mttr-shop-ready 1.0.0 (2026-10-16)

- First release: seven steps from finding the platform to checking again, with `mttr_product_check` before and after, approval through `mttr_propose`, and notes for Shopify, Hydrogen, Next.js commerce, WooCommerce and Magento.
