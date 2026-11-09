# jorigrym.com – personal portfolio site

Jori Grym's personal site: behavioral strategist (Finnish Tax Administration), researcher (Hanken School of Economics), science communicator. Hosted on **GitHub Pages** from `JoriGrym/jorigrym.github.io`, branch `main`, custom domain via `CNAME` (jorigrym.com). Pushing to `main` publishes the site within a minute or two. There is no build step.

The site is **bilingual**: English at jorigrym.com (`index.html`) and Finnish at jorigrym.com/fi/ (`fi/index.html`). Each page links to the other in the top-right corner ("Suomeksi" / "In English").

## Files

- `index.html`: the English site. HTML, CSS and a small vanilla script are inline, with no framework and no build.
- `fi/index.html`: the Finnish site. Same markup and CSS, with Finnish text.
- `398423632_...jpg`: profile photo, referenced by its raw GitHub URL in the hero.
- `CNAME`: custom domain. Do not change it.
- `README.md`: placeholder.
- `.claude/launch.json`: local preview server (`python -m http.server 8765`) for checking pages in a browser. Not part of the site.

**Every content change goes into both files.** The two pages have identical entries. Only the UI text, dates, summaries, "With"/"Host" lines and link labels are translated.

## Page structure (ids are the same in both files)

| id | Section (EN / FI) | Entry markup |
|---|---|---|
| `about` | Hero: name, bio, tags, stats | n/a |
| `latest` | Latest / Uusimmat: 4 hand-picked cards | `a.card` (update by hand, see below) |
| `publications` | Research / Tutkimus | `li > a.row` |
| `articles` | Writing / Kirjoitukset: opinion, Hanken blog and LinkedIn in one list (`#writing-list`) | `li[data-kind] > a.row` |
| `media` | TV, radio & podcasts: three tab panels `radio`, `tv`, `podcasts` | `li.ep` |
| `contact` | Get in touch / Ota yhteyttä | n/a |

Old anchors still work: `#tv`, `#radio` and `#podcasts` open that tab, and `#blog` filters Writing to blog posts.

All lists are flat and sorted **newest first**. There are no year groups. The script works out the stats, the tab counts, the Writing filter counts and the year filter buttons from the entries, so adding an entry needs no other edits. The exception is the **Latest** cards: when a newer radio episode, opinion piece, paper or TV episode is added, update the matching card in both files.

## Entry templates

Copy an existing entry of the same type, including its arrow `<svg class="ico" …>`, and change the text. `target="_blank" rel="noopener"` is on every external link.

### Episode (in `#radio`, `#tv` or `#podcasts` `ol.eps`)
```html
<li class="ep" data-year="2026" data-search="lowercased title, summary, people and date">
  <div class="ep-date">Nov 6, 2026</div>                      <!-- FI: 6.11.2026 -->
  <div class="ep-body">
    <h4 class="ep-title"><a href="URL" target="_blank" rel="noopener">Original episode title</a></h4>
    <p class="ep-topics">One-to-three-sentence summary.</p>     <!-- EN summary / FI summary -->
    <p class="ep-people">With Name &amp; Name</p>                <!-- FI: Mukana Name &amp; Name; podcasts: Host: / Juontaja: -->
  </div>
  <a class="ep-go radio" href="URL" target="_blank" rel="noopener" aria-label="Listen on Areena: Title">Listen on Areena <svg…></svg></a>
</li>
```
- `ep-go` class is `radio`, `tv` or `podcasts`.
- Link labels: EN "Listen on Areena" / "Watch on Areena" / "Listen"; FI "Kuuntele Areenassa" / "Katso Areenassa" / "Kuuntele".
- `data-year` drives the year filter. `data-search` is optional (search falls back to the visible text).

### Writing item (in `#writing-list`)
```html
<li data-kind="opinion"><a class="row" href="URL" target="_blank" rel="noopener">
  <span class="row-date">Apr 11, 2026</span>                    <!-- FI: 11.4.2026 -->
  <span class="row-main"><span class="row-outlet">Turun Sanomat</span><span class="row-title">Original headline</span></span>
  <span class="row-go">Read Article <svg…></svg></span>       <!-- FI: Lue artikkeli -->
</a></li>
```
`data-kind` is `opinion`, `blog` (Hanken CERS Blog, FI label "Lue kirjoitus") or `linkedin`.

### Research item (in `#publications ul.rows`)
Same `a.row` markup without `data-kind`. `row-date` is the year. FI link labels: "Lue artikkeli", "Lue väitöskirja", "Lue luku", "Lue tiivistelmä".

## Conventions

- Keep titles in their original language (mostly Finnish) in both versions. Summaries are in English on `index.html` and in Finnish on `fi/index.html`.
- Dates in lists: EN short month ("Nov 6, 2026"), FI "6.11.2026". Latest cards: EN full month ("November 6, 2026"), FI "6.11.2026". Asiastudio: "Recorded Jun 23, 2025" / "Nauhoitettu 23.6.2025".
- Get titles, dates and co-panelists from the linked page. Don't guess. If a detail can't be confirmed, leave it out and tell Jori.
- Jori's title is "Behavioral Science Researcher" (FI "käyttäytymistieteen tutkija"), not Behavioral Economics.
- Contact email is info@jorigrym.com. Twitter/X handle is @GrymJori.
- Update the footer copyright year in both files when the year changes.
- Don't redesign or restyle unless asked. Match the existing markup exactly. Colours are CSS variables on `:root` (light) and under `prefers-color-scheme: dark`. Headings use Manrope and body text uses Inter (Google Fonts).

## Workflow

0. **First-time setup on a new computer:** if this folder has no `.git`, connect it to GitHub without overwriting local files: `git init -b main`, `git remote add origin https://github.com/JoriGrym/jorigrym.github.io.git`, `git fetch origin`, `git reset origin/main`. Pushing needs Jori signed in to GitHub, through Git Credential Manager or `gh auth login`.
1. `git pull` before editing.
2. Edit `index.html` **and** `fi/index.html`. Check both in a browser (the `site` preview server in `.claude/launch.json`, then http://localhost:8765/ and /fi/), at desktop and phone widths.
3. Commit with a descriptive message (e.g. "Add 3 Perjantaistudio episodes (Mar–Apr 2026)") and push to `main` only after Jori approves.

## History

- 2025-05/06: many small manual edits through the GitHub web editor.
- 2026-04-14: major update with Claude: redesign, new sections, Perjantaistudio, Asiastudio and Hilden & Kaira episodes; Innohub renamed to Futucast; Blog & LinkedIn moved after Podcasts; X link fixed.
- 2026-10-23: added J. Marketing Analytics paper (2026), TS article Apr 11, final Jälkikaronkka May 27 (the show has ended), and 6 Perjantaistudio episodes May 29–Oct 16. Git installed on this computer (`C:\Program Files\Git\cmd\git.exe`), GitHub sign-in stored.
- 2026-11-09: added Perjantaistudio episodes Apr 17 and Nov 6, 2026 (checked the full series listing; 8 episodes with Jori in Apr–Nov 2026, all now on the site).
- 2026-11-09: second redesign: new navigation (Latest, Research, Writing, Media with tabs, search and year filters), cool navy/petrol palette, Finnish version at /fi/. Bio title changed to Behavioral Science Researcher; contact email set to info@jorigrym.com (was a placeholder).
- Newest content as of Nov 9, 2026: paper 2026; article Apr 11, 2026; Jälkikaronkka May 27, 2026; Perjantaistudio Nov 6, 2026; podcast Jan 14, 2026. Perjantaistudio series page: https://areena.yle.fi/1-77188392

## Known loose ends

- The Futucast entry still links to an `innohub.fi` URL.
- Asiastudio entries show recording dates, since asiastudio.fi gives no release date. The YouTube video zySKwU3NKSw is the same AI episode, so don't add it separately.
- One Perjantaistudio link (Feb 27, 2026) uses `arenan.yle.fi` (the Swedish-language Areena) instead of `areena.yle.fi`.
- The Finnish summaries and bio were translated by Claude; Jori has reviewed only the bio's research sentence.
