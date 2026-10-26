# Japanese Trainer PWA — corrected version 2

Standalone static PWA, with 1,000 entries imported from `top_1000_kanji.htm`.

## Corrections

- All German UI wording replaced with Japanese.
- Quiz modes and word-type checkboxes shown.
- Vocabulary table columns now match the data; last reviewed and next due show recorded dates.
- Corrected selected clear kana/romaji mistakes. See `corrections.txt`.
- Existing IndexedDB quiz progress is preserved during upgrades on the same site/origin.
- Source comment numbers 1–1000 used as source ranks, **not independently verified corpus frequencies**.
- Example sentences are only populated where manually supplied; other fields are blank.

## Run

Upload all files to GitHub Pages, or serve locally via `python3 -m http.server 8080` and open `http://localhost:8080`. Do not open as `file://`. After first load, install from browser menu. Clear/reload once if your browser has cached an older service worker.

## Data

Progress is stored per browser in IndexedDB. Export JSON backups regularly. On a different site origin, old progress is not automatically transferred; restore a backup.

## Version 3
- All/Clear word-type selection; End quiz early (completed ratings are saved).
- Android Japanese speech test and available voice selection.
- If speech is silent, check Android **Settings → Text-to-speech output**; select an engine with Japanese language/voice data installed, and test with the in-app button. Browser speech depends on the phone's installed TTS voices; this offline PWA does not bundle audio files.
- Keep the same GitHub Pages URL to retain existing IndexedDB review history.
