# Editing your content

All of your Past Work items, reviews, and songs now live in **`data.json`** instead of being hardcoded in `index.html`. `index.html` fetches this file at load time, so you never need to touch HTML/JS to update content.

## Easiest way to edit: `admin.html`

1. Open `admin.html` in your browser (double-click it, or visit `yoursite.com/admin.html` once deployed).
2. It auto-loads `data.json` if it's sitting next to it; otherwise use "Choose file" to load it manually.
3. Add, edit, or delete work items, reviews, and songs with the forms — you'll see live previews of images/covers.
4. Click **Download data.json**.
5. Replace the old `data.json` in your project with the downloaded one.
6. Commit and push to GitHub — Vercel (or GitHub Pages) will auto-redeploy.

Nothing in `admin.html` touches a server or database — it just edits the JSON in your browser and hands you a file to commit. It's not password-protected, so don't publish a live link to it if you don't want visitors poking at it (or just keep it local and never deploy it — deleting it from the repo doesn't affect the live site since `index.html` only depends on `data.json`).

## Even simpler way (no tool): edit directly on GitHub

1. Go to `data.json` in your GitHub repo.
2. Click the pencil (edit) icon.
3. Add/edit/remove an entry — it's plain JSON, e.g. for a new banner:
   ```json
   { "id": "b6", "category": "banners", "name": "Banner 6", "src": "https://files.catbox.moe/yourimage.png" }
   ```
4. Commit directly to `main`. Vercel redeploys automatically in ~30 seconds.

## Image/audio hosting

`data.json` just stores URLs — it doesn't host files. Keep using catbox.moe (or swap to something like GitHub itself: drop files in an `/assets` folder in your repo and reference them as a relative path, e.g. `"src": "assets/banner6.png"`).

## Data shape reference

```json
{
  "workItems": [
    { "id": "b1", "category": "banners", "name": "Banner 1", "src": "https://..." }
  ],
  "reviews": [
    { "id": 1, "name": "username", "service": "Logo Design", "stars": 5, "text": "..." }
  ],
  "playlist": [
    { "id": 1, "title": "Song title", "src": "https://....mp3", "cover": "https://....jpg" }
  ]
}
```

`category` must be one of: `banners`, `server-banners`, `footer-banners`, `logos`.
