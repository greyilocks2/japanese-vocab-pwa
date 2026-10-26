# German Trainer — fully offline PWA

This version is **static HTML/CSS/JavaScript**, with **no Go server, no SQLite server, and no HTMX dependency**. The 810 Goethe A1 entries from the earlier trainer are bundled. Learning history is stored in **IndexedDB**, separately on each browser/device.

## Start locally on your Mac

A PWA needs a secure origin (HTTPS or localhost), so **don't open `index.html` directly as a file**.

From this folder run one of:

```sh
python3 -m http.server 8080
# or if you prefer Go, with any installed static-file server
```

Then visit http://localhost:8080. After first load, the service worker caches the app for offline use. In Chrome/Edge, use the browser's Install option. The server can be stopped after the app is installed and cached, but initial installation requires localhost or HTTPS.

## Publish on GitHub Pages

Create a repository and upload the **contents of this folder** to its root. Under **Settings → Pages**, choose **Deploy from a branch**, branch **main**, folder **/(root)**. Open the resulting HTTPS URL and install it using your browser's menu. It works offline after the first successful load.

## Features

- English ↔ German vocabulary and sentence quiz modes.
- Reveal answer, rate H/J/K/L; Enter to reveal, H/J/K/L to rate.
- 10, 20, 50, 100 or 200 question sessions; due/unseen items prioritized.
- Separate review history for each quiz direction.
- Vocabulary search, sortable columns including date added / last review / next due.
- 100 displayed rows, paging in 50-row steps.
- Browser speech: question, question + answer, repeat, speed and voice selection.
- Import eight-column TSV, export full JSON backup, restore JSON backup.

## Important differences from the Go/SQLite version

- **Existing `vocabulary.db` progress is NOT automatically migrated.** The original TSV words are bundled, but past review dates/ratings remain in your old SQLite database. Keep that file safe.
- Data is **per browser/device** and can be lost if browser site storage is cleared. Export backups regularly.
- To move data to another device, use **Export progress & vocabulary**, transfer the JSON, then **Restore backup**.
- Browser speech voices vary by platform and may require system-installed voices; some devices need an initial tap before speech plays.
- The spaced-repetition algorithm here is intentionally simple: H extends intervals, J grows them moderately, K repeats tomorrow, L is due today.
- Static hosting cannot write to a shared database; there is **no automatic cross-device sync**.
