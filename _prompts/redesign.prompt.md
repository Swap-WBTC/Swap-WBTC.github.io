# Codex task: premium 2026 redesign of the Swap WBTC landing page (LIGHT) + a clean TradingView chart section + WBTC authorities

Rebuild this static one-page site IN PLACE (your -C workdir): overwrite `index.html` + `style.css`, keep
every other file. No frameworks, no build, no external JS libraries (EXCEPTION: the official TradingView
embed widget script, see CHART). Premium, modern, 2026 -- NOT dry, NOT chunky.

IMAGES ARE FROZEN (local): never create, overwrite, download, replace, rename, or delete any LOCAL image
(`favicon.png`, `btc.png`, `eth.png`, `simpleswap.png`, `og-cover.png`, any local `*.png`/`*.svg`/`*.ico`).
Use ONLY the local images already in the folder, byte-unchanged. Keep `<link rel="icon">` and the topbar
brand `<img>` on the existing `favicon.png` (no inline `<svg>`, no data-URI).
EXTERNAL images allowed ONLY for the authority-source logos (favicon service, see AUTHORITIES). No new LOCAL files.

PRESERVE from the current `index.html` (read it first): the exact keyword `Swap WBTC` (as `<h1>` and in
`<title>`), the existing value sentence (deck `<p>` = `<meta description>`, word-for-word, light polish
only), the `<link rel=canonical>`, the money CTA target href.

## IMPORTANT -- THIS PAGE SCROLLS (not a one-screen lock)
The HERO is a strong premium FIRST screen (fills ~one viewport). The page then SCROLLS DOWN to: (1) a clean
TradingView WBTC chart section, (2) the 5 WBTC authority links BELOW the chart, (3) the footer. Use normal
document flow -- do NOT set `overflow:hidden` / `height:100vh` lock on the body. `overflow-x:hidden` only,
to prevent horizontal scroll. No horizontal overflow anywhere, desktop or mobile.

## THEME: LIGHT premium 2026 (WBTC = Bitcoin)
- Clean LIGHT base; ONE confident accent = Bitcoin orange (around `#F7931A`; derive/confirm from
  `favicon.png` / `btc.png`). Soft white cards, GENEROUS rounded corners (~16-22px), gentle soft shadows,
  hairline neutral borders, airy whitespace. ONE accent, no rainbow. `<meta theme-color>` = the light base.
- Quiet premium motion only; respect `prefers-reduced-motion`.

## SEO spine (LOCKED -- exactly as standard)
- `<title>` = `Swap WBTC &mdash; <short hook>` (em-dash, keyword first, <=60 chars, no weak suffix).
- Exactly one `<h1>` = `Swap WBTC`. NO `<h2>` anywhere. Deck `<p>` wraps `<strong>Swap WBTC</strong>` and
  equals `<meta description>` word-for-word. Schema `@graph` = WebSite + WebApplication + Organization,
  truthful, no FAQ/HowTo. SEO text in source HTML.

## BUTTON STYLE (2026-modern, refined)
Both CTAs: hero ~50px / card ~48px, radius ~12-13px, font-weight ~600-650, slight negative letter-spacing.
Clean accent fill + subtle top inner highlight + faint 1px ring + a TIGHT low accent-tinted shadow (NOT a big
glow). A small arrow (`&rsaquo;`) that nudges ~3px right on hover with a gentle 1px lift.

## Section 1 -- HERO (first screen, split)
- **Topbar:** brand mark (`favicon.png`) + `Swap WBTC` wordmark LEFT; flexible spacer; THREE WBTC
  super-authority links on the RIGHT (replace the old generic ones), plain text,
  `target="_blank" rel="nofollow noopener noreferrer"`:
  - WBTC -> https://www.wbtc.network/
  - BitGo -> https://www.bitgo.com/
  - Etherscan -> https://etherscan.io/token/0x2260fac5e5542a773aa44fbcfedf7c193bc2c599
  No topbar button.
- **Left:** `<h1>Swap WBTC</h1>` (RENDER ~80px on desktop, e.g. `clamp(2.9rem,5.6vw,5.1rem)`, never under 64px)
  -> deck `<p>` (keyword in `<strong>`) -> THREE qualitative chips (e.g. `1:1 Bitcoin-backed`, `Non-custodial`,
  `DeFi-ready`) -> ONE primary CTA `Enter App`. NO `<h2>`.
- **Right (the star):** a RICH light swap-preview card: chrome + selector pill + pulsing `Preview` pill; a
  From (WBTC, use `btc.png`) -> To (ETH, `eth.png`) route in two rounded panels with a SMALL GAP + a circular
  switch in a clean notch; an abstract `Best route` micro-row (faint hop dots, NO fabricated numbers); a faint
  number-free hint; the `Start Swap` CTA. Non-interactive preview (only switch toggles icons). No fake amounts.

## Section 2 -- TradingView CHART (scroll down to it)
A clean section with a small quiet heading (e.g. `WBTC price`) and an embedded TradingView chart -- CLEAN, NO
extra buttons/toolbars. Use the official TradingView Advanced Real-Time Chart widget for symbol
`BINANCE:WBTCUSDT`, configured minimal:
```
<script type="text/javascript" src="https://s3.tradingview.com/external-embedding/embed-widget-advanced-chart.js" async>
{ "symbol": "BINANCE:WBTCUSDT", "theme": "light", "style": "3", "autosize": true,
  "hide_top_toolbar": true, "hide_side_toolbar": true, "hide_legend": false,
  "allow_symbol_change": false, "save_image": false, "details": false, "hotlist": false,
  "calendar": false, "withdateranges": false }
</script>
```
Put it in a rounded white card with a fixed height (~360-440px desktop, ~300px mobile, set the container
height so there is no layout shift). `style:"3"` = a clean area chart. No symbol search, no toolbar buttons --
just the clean live WBTC chart.

## Section 3 -- WBTC AUTHORITIES (directly BELOW the chart -- cleaner here)
A small quiet label (e.g. `Verified across WBTC authorities` / `Sources`) then a tidy row of these FIVE
WBTC super-authorities, each = its REAL LOGO + name, linked. Use EXACTLY (name | favicon domain | link),
do NOT alter the URLs:
- CoinGecko | coingecko.com | https://www.coingecko.com/en/coins/wrapped-bitcoin
- CoinMarketCap | coinmarketcap.com | https://coinmarketcap.com/currencies/wrapped-bitcoin/
- Gemini (What is WBTC) | gemini.com | https://www.gemini.com/cryptopedia/wbtc-what-is-wrapped-bitcoin
- Proof of Reserve (Chainlink) | bitgo.com | https://blog.bitgo.com/chainlink-brings-onchain-proof-of-reserve-to-wbtc-fcda00f2815c
- Bitstamp (WBTC guide) | bitstamp.net | https://www.bitstamp.net/learn/cryptocurrency-guide/what-is-wrapped-bitcoin-wbtc/
LOGOS via the Google favicon service ONLY: `https://www.google.com/s2/favicons?sz=64&domain=<DOMAIN>` (the
only external image source besides TradingView; create NO local files). Each logo `<img>`: width+height
(e.g. 22x22), `loading="lazy"`, `alt=""`, `onerror="this.remove()"`. Style: uniform rounded chips, muted by
default, gently colorize + lift on hover; tidy single row (wraps on mobile). Each link
`target="_blank" rel="nofollow noopener noreferrer"`. No horizontal overflow.

## Footer
A `Swap WBTC &mdash; 2026` brand line + ONE educational line:
`Information on this page is for educational purposes only and is not financial advice.`

## CTAs + Claims
- Exactly TWO CTAs, distinct, both -> the preserved target href, `rel="noopener noreferrer"`: hero `Enter App`
  + card `Start Swap`. No third CTA, no topbar button.
- Confident premium copy; two floors: (1) NO invented numbers (the TradingView widget shows the only price --
  do not type any price/stat yourself); (2) no "guaranteed / risk-free / 100%", no fake wallet-connect.

## Technical / mobile
- SEO content in SOURCE HTML; tiny INLINE `<script>` only for the switch (the TradingView embed script is the
  one allowed external script). Every LOCAL `<img>` has width+height.
- Page scrolls; `overflow-x:hidden` on html/body; reserve the chart container height (no CLS). Respect
  `prefers-reduced-motion`.
- MOBILE CLEAN: single column; cards full-width; swap route stacks (switch rotates vertical); chart ~300px
  tall; authorities wrap to a tidy block; comfortable spacing + tap targets; NO horizontal overflow.
- Keep `lang="en"`; keep favicon/og/manifest/robots/sitemap referenced. HTML entities (`&mdash;`,`&rsaquo;`,`&darr;`), no literal non-ASCII.

## Self-QC
- [ ] LIGHT premium 2026, Bitcoin-orange accent; modern refined buttons (arrow nudge); NOT dry.
- [ ] Topbar = THREE WBTC authorities (WBTC / BitGo / Etherscan), in source HTML.
- [ ] One `<h1>` = `Swap WBTC`; NO `<h2>`; deck `<p>` == meta description; H1 ~80px.
- [ ] Hero first screen; PAGE SCROLLS to chart + authorities (no one-screen lock); no horizontal overflow desktop/mobile.
- [ ] Clean TradingView `BINANCE:WBTCUSDT` chart: no toolbars/buttons, reserved height, light theme.
- [ ] FIVE WBTC authorities BELOW the chart with the EXACT URLs, real logos via Google favicon, nofollow, tidy.
- [ ] Rich number-free WBTC->ETH swap preview (btc.png/eth.png); switch in a clean notch.
- [ ] Exactly TWO CTAs (`Enter App` + `Start Swap`) -> target; no topbar button.
- [ ] LOCAL images byte-untouched; favicon still the icon + brand mark; footer brand line + one educational line.

Make it genuinely premium, 2026-modern, with a clean WBTC chart and tasteful authorities. Then stop.
