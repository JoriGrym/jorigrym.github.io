# jorigrym.com – personal portfolio site

Jori Grym's personal site: behavioral strategist (Finnish Tax Administration), researcher (Hanken School of Economics), science communicator. Hosted on **GitHub Pages** from `JoriGrym/jorigrym.github.io`, branch `main`, custom domain via `CNAME` (jorigrym.com). Pushing to `main` publishes the site within a minute or two. There is no build step.

## Files

- `index.html`: the whole site. HTML and CSS are inline, there is no JS framework and no build.
- `398423632_...jpg`: profile photo, referenced by its raw GitHub URL in the header.
- `CNAME`: custom domain. Do not change it.
- `README.md`: placeholder.

## Page structure (section ids in `index.html`)

| id | Section | Entry markup |
|---|---|---|
| `about` | Header: name, title, bio, tags | n/a |
| `publications` | Scientific Publications | `publication-item` |
| `articles` | Articles & Commentary: "Opinion Articles" subsection, plus others | `publication-item` |
| `tv` | Jälkikaronkka – Yle Aamu | `episode-card` with `watch-link tv`, "Watch on Areena" |
| `radio` | Kulttuuriykkönen Perjantaistudio – Yle Radio 1 | `episode-card` with `watch-link radio`, "Listen on Areena" |
| `podcasts` | Podcast Appearances | `episode-card` with `watch-link podcast`, "Listen" |
| `blog` | Blog & LinkedIn | see existing entries |
| `contact` | Get in Touch | n/a |

Entries are grouped by year (`<!-- 2026 -->` + `year-group` / `year-label` divs, with `tv-label` / `radio-label` variants) and sorted **newest first** within each year. When adding the first entry of a new year, create a new year group above the previous year's.

### Article template
```html
<div class="publication-item">
    <div class="publication-journal">Outlet name</div>
    <div class="publication-title">Original (usually Finnish) headline</div>
    <div class="publication-year">Month D, YYYY</div>
    <a href="URL" class="publication-link article-link" target="_blank">Read Article</a>
</div>
```

### Episode template (TV / radio / podcast)
```html
<div class="episode-card">
    <div class="episode-date">Month D, YYYY</div>
    <h3 class="episode-title">Original episode title</h3>
    <div class="episode-topics">One-to-three-sentence English summary of topics discussed.</div>
    <div class="episode-panelists">With Name & Name</div>  <!-- podcasts: "Host: Name" -->
    <a href="URL" class="watch-link tv|radio|podcast" target="_blank">Watch on Areena | Listen on Areena | Listen</a>
</div>
```

## Conventions

- Keep titles in their original language (mostly Finnish). Summaries (`episode-topics`) are in English.
- Dates are in English, like "February 27, 2026".
- Get titles, dates and co-panelists from the linked page. Don't guess. If a detail can't be confirmed, leave it out and tell Jori.
- Update the footer copyright year when the year changes.
- Don't redesign or restyle unless asked. Match the existing markup exactly.
- Twitter/X handle is @GrymJori.

## Workflow

0. **First-time setup on a new computer:** if this folder has no `.git`, connect it to GitHub without overwriting local files: `git init -b main`, `git remote add origin https://github.com/JoriGrym/jorigrym.github.io.git`, `git fetch origin`, `git reset origin/main`. CLAUDE.md will then show as a new untracked file. Pushing needs Jori signed in to GitHub, through Git Credential Manager or `gh auth login`.
1. `git pull` before editing.
2. Edit `index.html`, then open it in a browser to check that the layout isn't broken.
3. Commit with a descriptive message (e.g. "Add 3 Perjantaistudio episodes (Mar–Apr 2026)") and push to `main` only after Jori approves.

## History

- 2025-05/06: many small manual edits through the GitHub web editor.
- 2026-04-14: major update with Claude: redesign, new sections, Perjantaistudio, Asiastudio and Hilden & Kaira episodes; Innohub renamed to Futucast; Blog & LinkedIn moved after Podcasts; X link fixed.
- 2026-10-23: added J. Marketing Analytics paper (2026), TS article Apr 11, final Jälkikaronkka May 27 (the show has ended), and 6 Perjantaistudio episodes May 29–Oct 16. Git installed on this computer (`C:\Program Files\Git\cmd\git.exe`), GitHub sign-in stored.
- 2026-11-09: added Perjantaistudio episodes Apr 17 and Nov 6, 2026 (checked the full series listing; 8 episodes with Jori in Apr–Nov 2026, all now on the site).
- Newest content as of Nov 9, 2026: paper 2026; article Apr 11, 2026; Jälkikaronkka May 27, 2026; Perjantaistudio Nov 6, 2026; podcast Jan 14, 2026. Perjantaistudio series page: https://areena.yle.fi/1-77188392

## Known loose ends

- The Futucast entry still links to an `innohub.fi` URL.
- Asiastudio cards show recording dates ("Recorded June 10, 2025"), since asiastudio.fi gives no release date. The YouTube video zySKwU3NKSw is the same AI episode, so don't add it separately.
- One Perjantaistudio link uses `arenan.yle.fi` (the Swedish-language Areena) instead of `areena.yle.fi`.
