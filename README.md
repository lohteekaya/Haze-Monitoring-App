# Haze Monitor: Singapore and ASEAN

A single-page static site (no build step).

- **Haze data** (PSI, PM2.5 24 h, PM10 24 h): National Environment Agency via data.gov.sg, Singapore only.
  Endpoint: `https://api-open.data.gov.sg/v2/real-time/api/psi`
- **Weather** for every city: Open-Meteo, `https://api.open-meteo.com/v1/forecast`

Both APIs are called straight from the browser and need no key. If the NEA feed can't be reached, the page falls back to a clearly labelled reference reading.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole app (HTML, CSS and JS) |
| `vercel.json` | Clean URLs and basic security headers |
| `.gitignore` | Keeps local junk out of the repo |

## Deploy to Vercel

1. Create a GitHub repository and upload these files to the repository root.
2. In Vercel, choose **Add New, Project** and import the repository.
3. Set **Framework Preset** to **Other**. Leave Build Command and Output Directory empty (or set Output Directory to `.`).
4. Click **Deploy**.

Or from a terminal: `npx vercel --prod`.

## Notes

- data.gov.sg limits requests without an API key. If many people use the site at once you may see HTTP 429. The fix is a small serverless proxy that adds an `x-api-key` header, so the key stays off the browser.
- Haze data is used under the Singapore Open Data Licence v1.0. Weather data is from Open-Meteo.com (CC BY 4.0).
