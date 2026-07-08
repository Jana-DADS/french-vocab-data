# 🇫🇷 Mon Vocab

A web app for learning French vocabulary using flashcards with spaced repetition. The dictionary contains 5,000 of the most frequently used French words, ordered by frequency of occurrence in the language.

**Production:** https://jana-dads.github.io/french-vocab-data/
**Testing (DEV):** https://jana-dads.github.io/french-vocab-data/dev/

---

## Features

- **Flashcards** — practice French → English or English → French
- **Practice mode** — type the French word to reinforce memory
- **Spaced repetition** — review intervals adapt based on word difficulty
- **Subjective difficulty** — each user marks words as Default / Easy / Medium / Hard and can customize the review frequency for each difficulty level in settings
- **Filters** — practice by CEFR level (A1–B2), category, or word class
- **Pronunciation** — IPA transcription for every word
- **Example sentences** — in both French and English
- **Automatic vocabulary updates** — the app detects a new vocabulary version and offers an Update button
- **What's New** — a changelog is shown whenever the app is updated
- **Offline support** — vocabulary is cached in localStorage and works without an internet connection

---

## CSV Structure (`french_vocab.csv`)

| Column | Description |
|---|---|
| `id` | Unique word ID |
| `fr` | French word (lemma) |
| `pronunciation` | IPA transcription |
| `info` | Word class and form (e.g. `n.m.`, `v. — je chante`) |
| `en` | English translation |
| `frSentence` | Example sentence in French |
| `enSentence` | Example sentence in English (optional) |
| `level` | CEFR level: A1, A2, B1, B2 |
| `category` | Thematic category (General, Verbs, Colors, Family, …) |
| `version` | Record version (internal) |

---

## Versioning

Versions are tracked in `version.json`, which contains two sections:

- **`vocab`** — vocabulary version (CSV file)
- **`app`** — application version (HTML file) + changelog

On startup, the app compares the locally stored version with the current version on GitHub and notifies the user if an update is available.

---

## Development Environment (DEV)

New features are developed and tested in the `dev/` folder:

- `dev/index.html` — test version of the app
- `dev/version.json` — separate versioning for DEV

The browser tab in the DEV version shows `🇫🇷 Mon Vocab [DEV]`. Once a feature is tested, it is copied to the production root `index.html`.

---

## Sources

**Base vocabulary**
Word frequency order is based on *A Frequency Dictionary of French* (Routledge). Translations and linguistic information (word class, pronunciation) were sourced from [Wiktionary](https://fr.wiktionary.org/).

**CEFR levels**
Word assignments to levels A1–B2 follow the pedagogical word lists of the Common European Framework of Reference for Languages (CEFR).

**Claude (Anthropic)**
Example sentences, vocabulary cleanup and additions, translation fixes, and the development of the entire application were carried out by [Claude](https://claude.ai) (Anthropic) in collaboration with the project author.

---

## Tech Stack

- **Frontend:** React 18 (functional components, hooks) — single HTML file, no build process
- **Data:** CSV file fetched from GitHub, cached in `localStorage`
- **Hosting:** GitHub Pages
- **Version tracking:** `version.json` on GitHub
