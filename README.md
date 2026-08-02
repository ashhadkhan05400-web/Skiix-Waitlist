# Skiix Waitlist

Landing page for the Skiix waitlist — collects name and email, deployed as a static site, and writes submissions straight into a Google Sheet.

**Live:** https://skiix-waitlist.vercel.app/

## Structure

```
Skiix-Waitlist/
├── Waitlist/        → site files (HTML/CSS/JS)
└── README.md
```

## What's on the page

- **What is Skiix** — short intro to the product
- **Waitlist form** — name + email capture
- **Meet the team** — team grid

## Stack

- Plain HTML/CSS/JS — no framework, no build step
- Fonts: Space Grotesk, Inter, IBM Plex Mono (Google Fonts)
- Form submissions handled by a Google Apps Script Web App, writing directly to a Google Sheet

## Design

Flat black background, no gradients, blue accent (`#5B8FFF`), no filler copy.

## Setup — connecting the form to Google Sheets

1. Open the target Google Sheet → **Extensions → Apps Script**
2. Paste in the Apps Script code (see `apps-script.gs`)
3. **Deploy → New deployment → Web app**
   - Execute as: **Me**
   - Who has access: **Anyone**
4. Authorize the script when prompted (click through the "unverified app" warning — it's your own script)
5. Copy the deployment URL (ends in `/exec`)
6. In the HTML file, find:
   ```js
   const SHEETS_ENDPOINT = "PASTE_YOUR_APPS_SCRIPT_WEB_APP_URL_HERE";
   ```
   and replace the placeholder with your deployment URL

Submissions land in the sheet as: **Name | Email | Timestamp**

## Deploying on Vercel

Vercel serves whatever's at the repo root — since the site currently lives inside `Waitlist/`, do one of the following:

- **Option A:** Move the HTML file (renamed to `index.html`) to the repo root
- **Option B:** In Vercel → Project Settings → General → set **Root Directory** to `Waitlist`, and make sure the file inside is named `index.html`

Either fixes the `404: NOT_FOUND` error on the deployed URL.

## Team

Built by the Skiix team — Ashhad Khan (Founder & CEO), Omer & Zufar (Design), Abdullah (Social), Furqan, Luthfi, Micheal, Juan, Huzaifa.
