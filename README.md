# LC / SN QC rating app (static, for GitHub Pages)

A version of the QC rating app that runs entirely in the browser, with no Python or server. It's a single file, `index.html`, so it can be hosted on GitHub Pages or opened straight from disk.

- **Images** are read from the rater's own computer when they choose their `MT_QC_scans` folder. They are never uploaded anywhere, so the hosted page contains no data.
- **Ratings** are saved in the browser as the rater works, under their name, so refreshing or closing the tab loses nothing. They come out as one CSV, `qc_notes_<name>.csv`, with one row per subject and LC and SN columns side by side (`LC_looks_good`, `LC_check_registration`, `LC_comment`, then the same for SN). It's the same file the standalone Flask app writes.

## For raters

1. Open the page. Enter your name and choose your `MT_QC_scans` folder, which must contain `MT_direct_transform_QC_images_LC` and `MT_direct_transform_QC_images_SN`. Your browser may ask whether to "upload" the files. Nothing is actually sent anywhere.
2. Rate each subject as **Good**, **Maybe**, or **Poor**. Click a selected rating again to unrate it. Tick **Check registration** if the alignment needs a second look. Use the left and right arrow keys to move between subjects, and the **Show** menus to list only good, maybe, poor, or unrated subjects.
3. Save your ratings with **Download CSV**. The bar at the top shows how many changes you haven't downloaded yet. Download again whenever you like; each download contains all your ratings so far.
4. To continue on another computer or browser, choose your downloaded CSV under **Previous ratings** on the start page.

Your ratings stay in this browser until you clear its site data. **Clearing site data before you download deletes them.**

## Trying it locally

Opening `index.html` directly (double-click) should work in most browsers, but the tested way is to serve it the way GitHub Pages will:

```bash
python3 -m http.server 8123 --directory qc_static_webapp
```

Then open <http://localhost:8123>.

## Troubleshooting

- **Download CSV does nothing:** the browser has probably blocked downloads from this page. In Chrome, click the icon at the right end of the address bar (or go to the site's settings via the icon left of the address), set **Automatic downloads** to **Allow**, then reload the page. Your ratings are kept.
