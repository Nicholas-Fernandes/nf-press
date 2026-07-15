# How to Add New Press Coverage
**Nicholas Fernandes — nf-press archive**

---

## Overview

The site reads from one file: `manifest.json`. Adding new press = adding one entry to that file. No code changes, no rebuilding, no re-exporting.

---

## Step-by-step for each type

### PDF or document (via Google Drive — recommended)

1. Upload the PDF to your Google Drive "Featured news" folder
2. Right-click the file → **Share** → change to **"Anyone with the link"** → copy the link
3. Open `manifest.json` on GitHub, click the pencil ✏️ to edit
4. Add this entry inside the `articles` array (before the last `]`):

```json
{
  "id": "unique-id-here",
  "sectionId": "businesses",
  "business": "Memmzy Health",
  "title": "Article Headline Here",
  "publication": "Publication Name",
  "date": "2026-07-15",
  "type": "pdf",
  "driveUrl": "https://drive.google.com/file/d/PASTE_FILE_ID_HERE/view",
  "link": "https://original-article-url.com (if still live, else leave blank)",
  "acquired": false
}
```

5. Make sure you add a **comma after the previous entry** before pasting yours
6. Click **Commit changes**

---

### Image / Screenshot (via Google Drive)

Same as PDF above, but set `"type": "image"` instead of `"pdf"`.

If the image is in Google Drive, use `driveUrl`. If it's uploaded to GitHub, use `"file": "articles/folder/filename.jpg"` instead.

---

### YouTube / Podcast video

No file upload needed — just the URL.

```json
{
  "id": "unique-id-here",
  "sectionId": "personal",
  "business": "Nicholas Fernandes",
  "title": "Video or Episode Title",
  "publication": "Channel or Show Name",
  "date": "2026-07-15",
  "type": "video",
  "mediaType": "YouTube",
  "url": "https://www.youtube.com/watch?v=VIDEOID",
  "link": "https://www.youtube.com/watch?v=VIDEOID",
  "views": "1.2K views",
  "acquired": false
}
```

For podcasts, change `"mediaType": "YouTube"` to `"mediaType": "Podcast"`.

---

## Section IDs

| Section | sectionId |
|---|---|
| Businesses (Memmzy, CreditSage, future) | `businesses` |
| Real Estate (Bright Bloom) | `realestate` |
| Personal (awards, podcasts, recognition) | `personal` |

---

## Business values

Use exactly one of these in the `business` field:
- `Memmzy Health`
- `CreditSage`
- `Bright Bloom`
- `Nicholas Fernandes` (for personal)
- Or any new business name — just be consistent

---

## Rules

- **`acquired: true`** → use for CreditSage (sold). Greyed out card with Acquired badge.
- **`acquired: false`** → everything else
- **`id`** → must be unique. Use format like `mh-12`, `cs-12`, `p-5`, `bb-3`
- **`date`** → format `YYYY-MM-DD`. Use `2021-01-01` if exact date unknown
- **`driveUrl`** → Google Drive share link. File must be set to "Anyone with the link"
- **`link`** → original article URL if still live. Leave `""` if the page is gone
- Always put a **comma** after the previous `}` before adding your new entry

---

## Adding a new section (e.g. a new business)

Add it to the `sections` array in `manifest.json`:

```json
{ "id": "newbusiness", "name": "New Business Name", "color": "#60a5fa", "note": "" }
```

Color options: `#c084fc` violet · `#34d399` green · `#fb923c` amber · `#60a5fa` blue · `#f472b6` pink · `#f87171` red

Then use `"sectionId": "newbusiness"` on your articles.

---

## Your live site

**https://nicholas-fernandes.github.io/nf-press**

Changes go live ~60 seconds after you commit on GitHub.
