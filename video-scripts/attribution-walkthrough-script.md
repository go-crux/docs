# Attribution walkthrough, Loom script

**Deck:** https://crux-resources.pages.dev/product/attribution/ (source: `~/code/crux/resources/site/product/attribution/index.html`)
**Length:** 8 to 9 minutes
**Audience:** founders and heads of growth at client brands, watching before or just after their dashboards go live

**The one thing they should take away:** we build a waterfall to move orders out of direct, brand search and unknown and into channels they can set a budget against. Every client gets the waterfall. Modelled re-attribution sits on top only where a post-purchase survey is live and has enough answers.

**Recording notes**

- Right arrow moves on. Slides 4, 5, 6 and 8 build one piece at a time, with what is coming shown faint. Each `[→]` below is one press.
- Say the two names the same way every time: "the attribution waterfall" and "modelled re-attribution". Never "the re-attribution model" for the waterfall.
- Our GA4 step is first click throughout: the customer's first visit that was not direct. "Last click" appears on the slides only as the model we are comparing against.
- The proof point (slides 5 and 8): two live builds, 144,395 orders, 1 October 2025 to early September 2026. Build A 26.7% to 5.8% in direct or unknown (78% moved), build B 41.7% to 6.2% (85% moved), 79% across both. Do not name the clients.
- Talking points, not a teleprompter. The lines in quotes are the ones worth saying close to verbatim.

---

## 1. Cover (30 seconds)

- Hi, Matt here, founder of Crux. A few minutes on how we attribute your orders, so that when you make a decision off the dashboard you know how the number got there.
- The problem in one line: click-based tracking leaves a large share of your orders in direct, brand search and unknown, and you cannot optimise any of those.
- "We build two layers to fix that. The attribution waterfall, which every client has. And modelled re-attribution, which sits on top if you run a post-purchase survey."
- I will take them in that order, and be clear about which one to use for which decision.

## 2. Two decisions (50 seconds)

- Start here: no attribution model is right or wrong. Each one credits some channels too much and others too little. What matters is knowing which way yours leans before you move budget or pause a creator.
- We read attribution at two levels.
- Channel level: where does the next hour go? Budget and time, so it covers organic as well as paid: Meta against Google against influencer against organic and email. That question is about totals, so some modelling is fine.
- Campaign level: which ad, which creator, which keyword do we change? That needs every order traced to something real, so nothing is modelled.
- Hold on to the split. It is the reason there are two layers.

## 3. What click-based models miss (75 seconds)

- A quick tour of what is already out there and which way each one leans.
- Last click: credits the final touch, so brand search, retargeting and affiliates collect orders that Meta, YouTube or a creator started.
- Ad platforms: each one sees only itself. Someone sees a Meta ad, comes back that evening through a Google brand ad and buys. One order in Shopify, one conversion in Meta, one in Google.
- GA4 out of the box: point at the screenshot. You come in on a Monday, look at yesterday, and the biggest channel is Unassigned, because Google can take up to 48 hours to process it. This is what pushed me to build our own model at Fussy.
- Media mix modelling: fine for big shifts in budget, no help choosing a creator or an ad.
- "The first three all depend on a click. Influencer, upper-funnel Meta and YouTube are mostly seen, not clicked. The customer searches your brand later, or types the URL, and the order lands in brand search or direct."

## 4. One order, read three ways (60 seconds)

- Make it concrete with one customer. Walk the four boxes: sees a creator's story, notes the code, does not tap. Three days later searches the brand, clicks the brand ad, buys with the code.
- `[→]` GA4 last click calls that paid search, brand. It was the only click.
- `[→]` Google Ads claims it for its brand campaign.
- `[→]` The waterfall credits the creator, because the code on the order is mapped to them in your config sheet.
- The stat: with codes mapped we credit 90%+ of influencer orders to the creator. Tracked links alone find 15 to 25%.

## 5. Layer one: the attribution waterfall (2 minutes)

- "This is the layer every client has, and it is the main thing I want you to take from this video."
- Each order runs down these sources in order. The first one that names a real channel settles it. Every step exists for one reason: to get orders out of direct and unknown.
- `[→]` GA4 first click. We link your GA4 to BigQuery and read the raw events, which avoids the processing delays you just saw. We take the customer's first visit that was not direct, with no time limit, so a 60-day purchase cycle still resolves. This settles 60 to 70% of orders.
- `[→]` Discount codes. The code at checkout, mapped in your sheet to a channel and a named partner. This is where influencer, referral, affiliate, podcast and out-of-home get caught.
- `[→]` Shopify customer journey. Shopify keeps its own record of the last touch. It catches visits that ad blockers and cookie limits hid from GA4.
- `[→]` Post-purchase survey answer. If you run a survey, the customer's own answer names the channel for their order. If you do not, this step is simply skipped.
- `[→]` Order attributes and tags. What platforms like Awin or Social Snowball write onto the order.
- `[→]` Klaviyo. If the order is still in direct or unknown and Klaviyo ties it to a campaign or flow, it goes to email. It comes last on purpose: email is a closing touch, so it never takes an order an earlier step has placed.
- `[→]` Whatever is left stays as unknown. At order level we never guess.
- Right-hand side, the key number: "On our two live builds, steps two to six move around four in five of the orders GA4 left in direct or unknown into a named channel." 78% on one, 85% on the other.
- Every order traces to a real touchpoint, which is why this layer is safe for campaign decisions. First click is the default: the channel that introduced the customer, not the one that closed. And the mapping lives in a Google Sheet you control.

## 6. Layer two: modelled re-attribution (90 seconds)

- "This is the second layer, and not every client has it. It depends on a post-purchase survey, with enough answers coming through."
- `[→]` After the waterfall there is still a pool left: unknown, direct and brand search. 2,100 orders in this example.
- `[→]` We look at what your surveyed customers said over the same period. Here, half said Meta, 30% an influencer, 20% YouTube.
- `[→]` We split the pool in those shares. Meta gets 1,050, influencer 630, YouTube 420.
- Three rules, left to right.
- It needs enough answers. We use the most recent period that holds enough survey responses to trust, and widen it until it does. If there are not enough, we leave the pool alone, so a handful of answers never swings a channel.
- It moves credit, never orders. Totals are identical before and after and still reconcile to Shopify. Brand search is in the pool because someone searching your name had already heard of you somewhere.
- "It is for channel decisions only. It tells you how much to give Meta against influencer. It cannot tell you which ad or which creator earned it."

## 7. The two layers side by side (50 seconds)

- One slide to pin down the two names, because we have used "re-attribution" loosely in the past.
- The attribution waterfall: one order at a time, every client, read it for which ad, creator or code to change.
- Modelled re-attribution: channel totals, clients with a survey, read it for how channels compare and where budget goes.
- The line at the bottom is the one people trip on. The survey appears in both. In the waterfall, a customer's answer settles their own order. In modelled re-attribution, all the answers together settle the orders of people who did not answer.
- No survey? You still have the full waterfall, minus step four.

## 8. In practice (60 seconds)

- The same 10,000 orders, three ways. The table is illustrative, to show the mechanism.
- GA4 last click: 5,500 of the 10,000 are in direct, unknown or brand search. More than half your orders with nothing to act on.
- `[→]` The waterfall takes that to 2,100. Look at influencer, 400 to 1,900, and Meta, 2,900 to 4,000.
- `[→]` Modelled re-attribution spreads the last 2,100 across the channels customers named.
- The total is 10,000 in every column.
- `[→]` And this is real. Two live client builds, 144,395 orders over the last year, waterfall only, neither runs a survey yet. On GA4 alone, 27% of orders on one and 42% on the other sat in direct or unknown. After the waterfall, 6% on both.
- "Across the two, 79% of the orders GA4 could not place now sit in a named channel."

## 9. Three things that improve your attribution (45 seconds)

- Three things on your side improve your attribution.
- Give every creator and partner their own unique code.
- Tag every paid link, and use the platform's campaign and ad IDs in the link, not the names. "This one matters. A name gets edited or reused. An ID never changes, so the order still matches the ad."
- Run a post-purchase survey. One question. It adds a step to your waterfall and switches on the second layer. We will set it up and map the answers with you.
- The full method is in the help centre, linked here. For anything about your own numbers, email me or message us on Slack.
- Thanks for watching.
