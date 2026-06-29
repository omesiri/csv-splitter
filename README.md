# CSVsplit

Split and merge CSV files instantly — entirely in your browser. No uploads, no servers, no data ever leaves your device.

**Live site:** https://omesiri-csv-spliter.netlify.app/

---

## Features

### Split
Upload a CSV file, set a row limit, and download each chunk as a separate file. Every part includes the original header row.

### Merge
Upload two or more CSV files and combine them into one. Columns are matched by header name — files with different columns are aligned automatically, with empty values where a column is absent.

---

## How it works

- Built as a single `index.html` file — no framework, no build step, no dependencies to install
- Uses [PapaParse](https://www.papaparse.com/) (loaded from CDN) for CSV parsing and serialisation
- All processing happens client-side via the File API and Blob downloads

---

## Running locally

Open `index.html` directly in any modern browser, or serve it with:

```sh
python3 -m http.server 8080
```

Then visit `http://localhost:8080`.

---

## Deployment

Hosted on Netlify as a static site. To deploy updates, push to this repo — Netlify will auto-build and publish.
