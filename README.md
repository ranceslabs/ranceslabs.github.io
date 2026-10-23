# Shared website for Jesse Rances's mobile games

Plain static HTML/CSS for GitHub Pages. No build step, no JavaScript, no cookies, trackers or analytics.
Games are published by **Jesse Rances as an individual developer**. Support and privacy contact for every game:
**ranceslabs.support@gmail.com**.

## Layout

```
index.html              Studio page: lists every game and links to its pages
app-ads.txt             AdMob authorized sellers file (must stay at the domain ROOT)
.nojekyll               Tells GitHub Pages to serve files as-is (no Jekyll)
assets/style.css        Shared dark/brass styles
last-bastion/
  privacy.html          Privacy policy (from last-bastion-legal/privacy-policy.html)
  delete-data.html      Data-deletion request page
ashdrift/
  privacy.html          Privacy policy (from airship-colony-legal/privacy-policy-draft.md v4)
  delete-data.html      Data-deletion request page
```

Public URLs once published (replace `<user>` with the GitHub username):
`https://<user>.github.io/last-bastion/privacy.html`, `.../last-bastion/delete-data.html`, and so on.

## Publishing notes

- **app-ads.txt only works at the domain root.** Publish this repo as a GitHub Pages *user site*
  (repo named `<user>.github.io`) or behind a custom domain. A project site (`<user>.github.io/<repo>/`)
  will NOT work for app-ads.txt.
- Put the same website URL in each app's Play Console store settings (Developer website).
- Before launch, replace `pub-XXXXXXXXXXXXXXXX` in `app-ads.txt` with the real AdMob publisher ID.
- Privacy pages must stay public, non-PDF and not geofenced.

## Adding another game

1. Make a folder named after the game, lowercase with hyphens, e.g. `bunker-nights/`.
   The folder name becomes part of the URL, so don't rename it after the store listing links to it.
2. Add `bunker-nights/privacy.html`. Start from the game's finished policy text in its `*-legal` folder.
   Only fill placeholders (effective date, support email, URLs); don't change legal wording without the
   legal docs being updated first. Link the stylesheet with `<link rel="stylesheet" href="../assets/style.css">`
   and add the back link `<a href="../">&larr; All games</a>` at the top.
3. Add `bunker-nights/delete-data.html`. Copy an existing `delete-data.html` and rewrite it to match what
   that game really stores (local saves, cloud saves, accounts, analytics IDs, etc.) and how each is deleted.
   If the game has accounts or sign-in, Play requires this page to let users request deletion without
   reinstalling the app, so explain the email request path clearly.
4. In `index.html`, add (or update) the game's `<li class="game">` card with links to both pages:
   ```html
   <li class="game">
     <h2>Bunker Nights</h2>
     <p>One-line description.</p>
     <div class="links">
       <a href="bunker-nights/privacy.html">Privacy policy</a>
       <a href="bunker-nights/delete-data.html">Delete your data</a>
     </div>
   </li>
   ```
   Games without finished pages get `<span class="soon">Coming soon</span>` instead of links.
5. `app-ads.txt` needs no change if the game uses the same AdMob account.
6. Open the pages locally (`python3 -m http.server` in this folder) and check them on a narrow window.
