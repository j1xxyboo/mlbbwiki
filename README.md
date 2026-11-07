
<h1 align="center">mlbb.wiki</h1>

<p align="center">
  Every hero. Every build. Every counter.<br />
  A community wiki, tier list and toolbox for <strong>Mobile Legends: Bang Bang</strong>, built from the game's own numbers.
</p>

<p align="center">
  <a href="https://mlbbwiki.vercel.app">Live site</a> ·
  <a href="#features">Features</a> ·
  <a href="#where-the-data-comes-from">Data</a> ·
  <a href="#run-it-locally">Run it locally</a> ·
  <a href="#contributing">Contributing</a>
</p>

<p align="center">
  <img alt="React 18" src="https://img.shields.io/badge/React-18-20232a?logo=react&logoColor=61dafb" />
  <img alt="TypeScript" src="https://img.shields.io/badge/TypeScript-5-3178c6?logo=typescript&logoColor=white" />
  <img alt="Vite" src="https://img.shields.io/badge/Vite-5-646cff?logo=vite&logoColor=white" />
  <img alt="Tailwind CSS" src="https://img.shields.io/badge/Tailwind_CSS-3-06b6d4?logo=tailwindcss&logoColor=white" />
  <img alt="Deployed on Vercel" src="https://img.shields.io/badge/Vercel-deployed-000000?logo=vercel&logoColor=white" />
</p>

![mlbb.wiki home page: the hero showcase with the featured hero's splash art, skill icons and the five featured heroes](docs/readme/home.jpg)

## What it is

mlbb.wiki is a fan-made site for Mobile Legends players who want answers between two matches: which heroes win right now, what to build on them, who counters whom, what the last patch changed, and when the next pro match starts.

Everything on the site is measured or sourced, never guessed. Win, pick and ban rates come from ranked play and are broken down by rank. Patch changes are the official notes, restructured per hero and per item. Pro drafts come from the leagues. Hand-written analysis sits on top of that data, clearly separated from it.

The site has no signup and no database. The optional sign-in uses your Player ID and the game's own verification code, and the session lives in your browser.

## Features

### Hero pages

Every one of the game's 130+ heroes has a page with its skills, lore, skins, measured counters and best teammates, the builds actually played at each rank, pro-play presence, and the hero's full patch history.

![Kagura's hero page: identity, ratings, lane and region facts, win and ban rates, rank selector, pro-play presence](docs/readme/hero.jpg)

**Guide tab.** One recommended build for the rank you select (the most played core items plus a top-rated player's full six-item equipment), the skill level-up order, and three "how to play" tips built from the hero's lane, matchups and build.

![Kagura's guide tab: recommended build with items, emblem, talents and spell, skill order, and three how-to-play tips](docs/readme/hero-guide.jpg)

**Patch awareness.** A badge says when the hero was last buffed, nerfed or adjusted. The Patches tab lists every synced patch that touched the hero with the numbers before and after, so you never have to dig through a whole patch note.

![Kagura's patch history: each patch with its buff or nerf label, intro, and before-to-after values](docs/readme/hero-patches.jpg)

### Tier list and statistics

Heroes ranked from the game's measured win, ban and pick rates, filterable by rank, lane and role, with a short note on each hero and a meta report. The statistics page has every figure behind it.

![Tier list page: filters by rank, lane and role, and the S+ tier with win, ban and pick rates per hero](docs/readme/tier-list.jpg)

### Draft simulator and team tools

Play a full ranked or tournament (MPL) draft for both sides. At every step the assistant suggests the best ban or pick from measured counters, synergies and win rates. Compare two heroes side by side, or check a five-hero lineup in the team builder.

![Draft pick and ban simulator: blue side banning, the hero grid with tiers, and the red side slots](docs/readme/draft.jpg)

### Esports

Next matches updated every minute, live and upcoming tournaments, standings, results, and the heroes pros pick and ban compared with ranked play. Pro teams and players have their own pages.

![Esports page: the next five matches with teams and times, then the tournaments section](docs/readme/esports.jpg)

### Heroes, items and game knowledge

![Heroes list: 134 heroes with role counters, search, role and lane filters, and tier tags on every portrait](docs/readme/heroes.jpg)

![Items page: every item with its category and price, opening into a sheet with stats, passives, recipe and the patches that changed it](docs/readme/items.jpg)

The items page shows each item's stats, passives and recipe, plus the patches that changed it. Emblems, battle spells, skins with a release calendar, lore by region, game modes, patch notes and news (including the Advance Server) complete the picture.

### Tools

- **Win rate calculator**: how many wins you need to reach a target rate.
- **Server time**: the current time on every server, with the next resets.
- **Objective timer**: Turtle, Lord and buff respawns during a match.
- **Draw calculator**: odds, expected cost and milestones of a draw event.
- **Retribution test** and **collection value calculator**.
- **Tier list maker**: your own ranking, shared by link or exported as an image.
- **MLBBdle**: guess the hero of the day from colour clues or a single skill icon.

![MLBBdle: the daily hero guessing game](docs/readme/mlbbdle.jpg)

### Your account

Sign in with your Player ID and Server ID. The game mails a 4-digit code to your in-game inbox; no password, no signup. You then get your profile (name, avatar, level, current and highest rank, region), your friend list, a shareable lobby card, and scrims: lobbies where creators invite players and record results.

## Where the data comes from

| Data | Source | How it is refreshed |
| --- | --- | --- |
| Heroes, skills, skins, items, patch notes | Mobile Legends wiki (Fandom) | `npm run sync` (full or daily), stored in `src/data/game/` |
| Win, pick and ban rates, counters, builds, player guides | In-game ranked statistics | same sync, broken down by rank |
| Esports tournaments, matches, pro drafts | Liquipedia (CC BY-SA 3.0) | `npm run sync:esports` |
| Pro teams, players and live matches | PandaScore API | serverless routes under `/api` |
| Events and skin calendar | Game events feed | `npm run sync:events` |
| Advance Server notes, news | Official channels | `npm run sync:advance-server`, `npm run watch:news` |
| Player account | The game's account API, proxied by `/api/mlbb-*` | live, on sign-in |

Hand-written hero analyses (summary, strengths, weaknesses, annotated builds, skill order, tips) live in `src/data/wiki/heroes/` and are layered on top of the synced data by hero slug.


## Credits and legal

Mobile Legends: Bang Bang is a trademark of Moonton. This is a community project, not affiliated with or endorsed by Moonton.

Game data and art come from public community sources, esports data from Liquipedia under CC BY-SA 3.0, pro data from PandaScore. The counters and builds-by-rank views were ported from achedon12/mlbb.
