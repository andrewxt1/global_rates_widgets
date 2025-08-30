
# Global Key Interest Rates — Notion Widgets

Two drop-in HTML widgets you can host (Vercel/Netlify/GitHub Pages) and embed in Notion.

## Files
- `global-rates-newtab.html` — clicking a row opens the official chart in a **new tab**.
- `global-rates-inline.html` — clicking a row **loads the chart inside** the embed.

## Features
- Auto-updates daily (client-side fetch).
- Color-coded trend arrows: red ↑ (hike), green ↓ (cut), gray → (unchanged).
- Hover any row to see the **last 3–4 distinct moves** with dates (tooltip).
- Compact, clean design for Notion headers.

## Data Source
- **API Ninjas — Interest Rate API** (current + historical): https://api-ninjas.com/api/interestrate
  - You need a free API key. Add it to the URL: `?api_key=YOUR_KEY`.

## Usage
1. Host the HTML files (Vercel, Netlify, GitHub Pages, S3, etc.).
2. In Notion: `/embed` → paste the hosted URL.
3. Append your API key as a query parameter:
   - New tab: `https://yourdomain/global-rates-newtab.html?api_key=YOUR_KEY`
   - Inline:  `https://yourdomain/global-rates-inline.html?api_key=YOUR_KEY`

## Optional Settings
- You can also add `&mode=newtab` or `&mode=inline` in the URL — but each file already forces the intended mode.
- To customize labels or countries, edit the `ENTRIES` array near the top of the `<script>` in each file.

## Click-Through Charts (per row)
- U.S. (Fed) → FRED Fed Funds chart
- Eurozone (ECB) → ECB key rates page
- U.K. (BoE) → Bank Rate history
- Japan (BoJ) → Policy rate chart
- China (PBoC) → LPR page
- Switzerland (SNB) → Current interest rates

These links open **in a new tab** (newtab version) or **inline** (inline version).

## Notes
- Some corporate networks may block API calls. Ensure `api.api-ninjas.com` is accessible.
- If you want to switch to your own data sources (FRED/ECB/BoE/etc.), swap out the fetcher in `fetchCountry()`.
- Timezone: Date stamps use the browser timezone.
