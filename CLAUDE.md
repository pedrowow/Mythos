# Mythos — Project Brief

## What this is

A personal Greek mythology learning site for Pedro, hosted on GitHub Pages at pedrowow.github.io/Mythos. Pedro is the sole user. He is a leadership coach with a strong interest in Jungian psychology and a practising witchcraft student (Unnamed Path tradition, currently moving from spellwork into divination). The site exists so he can rabbit-hole through myths, deities, and their interconnections, and understand each deity as an archetype: psychologically and magically, not just narratively.

Written in British English throughout. No em-dashes; use commas, colons, or parentheses instead.

## Current state and the problem

The site was built in May 2026 and stalled at the Creation Cycle: three stories (Chaos, Age of the Titans, Titanomachy), eight thin character pages, a timeline, and a characters index. Problems identified:

1. Wrong spine. Stories are the destination and characters are footnotes. Pedro's goals need the inverse: deity pages as rich dossiers, stories as supporting material.
2. Content is uneven: summarised in places, detailed in others, walls of text, no rabbit-hole density.
3. Most images are broken (hotlinked Wikimedia URLs).
4. Dark green background fights long-form reading.

## Architecture decision: character-first

Each major deity gets a **dossier page** with these sections, in this order:

1. **Essence** — one-paragraph distillation of who this deity is and what force they embody.
2. **The myths** — the deity's essential stories, each as a short titled summary (150–300 words) with a link to the full story page where one exists. Dense inline links to other deities.
3. **Epithets and domains** — the major cult titles (e.g. Athena Parthenos, Athena Promachos) with what each aspect governs. These matter for both psychology and practice.
4. **The archetype** — Jungian reading. What pattern this deity personifies, its light expression and its shadow expression, drawing on the archetypal psychology tradition (Jung, Hillman, Jean Shinoda Bolen's *Gods in Everyman* / *Goddesses in Everywoman*). Be substantive, not a paragraph of hand-waving.
5. **In modern life** — how this archetype shows up today: in personalities, workplaces, relationships, culture. Pedro is a leadership coach, so concrete behavioural patterns are more useful than abstractions.
6. **Correspondences** — a structured panel for magical practice: planet, day of the week, colours, symbols and sacred objects, animals, plants and herbs, offerings, and any historically attested festivals or cult sites. Ground these in Hellenic sources and established Hellenic polytheist practice where possible; flag clearly anything that is modern convention rather than ancient attestation. Do not invent correspondences.
7. **Relations** — parents, consorts, children, rivals, allies. Every name is a link.

Story pages remain, but serve the dossiers. Every myth mentions several deities; every deity links to several myths. That cross-linking density is the core feature.

## Content roster and phasing

Work in phases. Complete and commit each phase before starting the next. Ask Pedro to review the first dossier (Hermes) before producing the rest, so the template is validated once rather than corrected twelve times.

**Phase 1 — Foundations (do first, quick wins):**
- Fix all images site-wide by self-hosting (see Images below).
- Add a reading theme: default to a warm parchment/sepia light theme, keep the existing dark theme as a toggle (persist choice in localStorage). Keep the gold accent palette.
- Break existing story pages into shorter sections with subheadings roughly every 3–4 paragraphs. Add collapsible "side myth" asides (details/summary elements) for digressions.

**Phase 2 — The Twelve Olympians (the heart of the project):**
Zeus, Hera, Poseidon, Demeter, Athena, Apollo, Artemis, Ares, Aphrodite, Hephaestus, Hermes, Dionysus. Full dossiers per the template. **Start with Hermes** (Pedro's personal infrastructure is named after him; divination and liminality are directly relevant to his practice), then Hecate from Phase 3 may be pulled forward if he asks.

**Phase 3 — The essential non-Olympians:**
Hades, Persephone, Hecate, Prometheus, Pan, Eros, Gaia (upgrade existing page), Cronus (upgrade), Nyx (upgrade), the Fates, the Muses (single collective page each for Fates and Muses).

**Phase 4 — Myth cycles beyond Creation:**
Persephone's descent, the birth of Athena, Prometheus and fire, Apollo and Python (Delphi), the contest for Athens, Dionysus' arrival and the resistance to him, Aphrodite's birth, the loves and punishments of Zeus (as a linked set of short pieces rather than one monolith). Same story template as existing pages.

**Phase 5 — Navigation upgrades:**
Extend the timeline to cover new content. Add an "archetype index" page listing deities by psychological pattern. Consider a simple client-side search (vanilla JS over a generated JSON index; no build step).

## Content standards

- Depth target per Olympian dossier: roughly 1,500–2,500 words plus the correspondences panel. Enough to be genuinely educational, short enough to read in one sitting.
- No walls of text. Subheadings, short paragraphs, pull quotes from primary sources (Hesiod, the Homeric Hymns, Ovid) used sparingly and attributed.
- Cite the mythological source when versions conflict (e.g. Hesiod vs. Homeric tradition) rather than silently picking one.
- Inline character links (`.char-link`) on first mention of any deity with a page; related story links (`.story-link`) styled distinctly, as now.
- Tone: intelligent, vivid, a little dry. Not academic prose, not children's retellings.

## Images

Stop hotlinking. For every page:

1. Find public-domain artwork on Wikimedia Commons (classical paintings, red-figure and black-figure vases, sculpture photography; pre-1928 works or explicit PD).
2. Download, resize to max 1600px wide, compress (JPEG quality ~80), and commit to `/images/` with descriptive kebab-case filenames.
3. Reference with relative paths. Every image gets a caption: artist, title, date, collection.
4. Verify each image actually loads before committing. Broken images were the recurring failure of the first build; treat this as a hard acceptance criterion.

Aim for 2–4 images per dossier and per story page.

## Model strategy

Pedro is on a Claude Pro subscription with finite usage. Do not burn top-tier capacity on mechanical work. Match the model to the task; switch with `/model` in Claude Code, and default each session to the cheapest model that the session's planned work allows.

**Fable 5 (top tier) — reserve for judgement-heavy, accuracy-critical writing:**
- The Archetype and In Modern Life sections of each dossier (Jungian nuance, coaching relevance).
- The Correspondences panels (highest confabulation risk; requires source discipline).
- The first Hermes dossier in full, since it sets the template every later page copies.
- Resolving conflicting myth variants where the choice shapes the narrative.

**Sonnet — the workhorse, default for most sessions:**
- Story pages and myth summaries (Phases 1 retelling work and Phase 4).
- Essence, The Myths, Epithets, and Relations sections of dossiers once the Hermes template exists to imitate.
- HTML/CSS work: the theme toggle, template refactors, timeline extensions, the archetype index.
- Upgrading the existing thin character pages.

**Haiku — mechanical and repetitive tasks:**
- Image sourcing workflow: downloading from Wikimedia Commons, resizing, compressing, committing, verifying loads.
- Link checking across the site; fixing broken relative paths.
- Applying an already-designed change across many files (e.g. adding the theme toggle snippet to every page).
- Commit hygiene, index updates, adding new cards to characters.html and index.html.

**Practical pattern per Olympian:** draft the structural sections and page scaffold on Sonnet, switch to Fable 5 only for the archetype and correspondences sections of that page, then drop to Haiku for images and link wiring. If Pro limits are running low mid-session, finish structural work on Sonnet and defer the Fable 5 sections to the next window rather than writing them on a lesser model; a wrong correspondence is worse than a missing one.

## Technical constraints

- Static HTML/CSS/vanilla JS only. No build step, no frameworks, no npm. GitHub Pages serves the repo as-is.
- One shared stylesheet (`css/style.css`). Extend it; do not create per-page styles.
- Keep pages self-contained and the existing folder structure (`stories/`, `characters/`, `css/`, `js/`, plus new `images/`).
- Mobile-readable: Pedro reads on phone as well as laptop.
- Commit granularly: one commit per page or per coherent change, with clear messages. Do not push without being asked; Pedro reviews locally first.

## Working style

- Ask before restructuring navigation or deleting existing pages.
- When content decisions are ambiguous (e.g. which myth variant to feature), pick the best-attested version, note the alternative briefly in the text, and move on. Do not stall waiting for feedback on content; Pedro has said he cannot meaningfully review mythology content, only design and structure.
- Flag at the end of each session what was completed and what the next session should pick up.
