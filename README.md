# Mon Vocab

A web app for learning French vocabulary with flashcards and spaced repetition. The vocabulary has 5,195 French words
with pronunciation, grammar information, an English translation and an example sentence.

**Production:** https://jana-dads.github.io/french-vocab-data/
**Testing (DEV):** https://jana-dads.github.io/french-vocab-data/dev/

## Two dictionaries

The same words can be learned in two orders, chosen on the Update Progress page. Each order keeps its own progress.

- **By frequency** – the most used words first (spoken French, Lexique subtitle frequencies).
- **By level A1 → C2** – beginner words first (FLELex levels), and by frequency inside each level.

Levels: A1 1196, A2 659, B1 1263, B2 1500, C1 427, C2 150.

## Features

- Flashcards and writing practice, French → English and English → French
- Spaced repetition with Easy / Default / Hard and adjustable intervals
- Filters by level and topic, pronunciation (IPA and speech), example sentences
- Typing French: any form of a card is accepted (`le / la / les`: `la`, `les le`…), other spellings too (`diner` for `dîner`)
- Phone layout, can be added to the home screen
- Automatic vocabulary updates and a What's New notice

## CSV structure (`french_vocab.csv`)

| Column | Description |
|---|---|
| `id` | Word id. It is also the key of the learner's progress: never renumber. A removed word leaves a gap. |
| `fr` | French word; several forms are separated by ` / ` (`le / la / les`) |
| `pron` | IPA pronunciation |
| `info` | Word class, gender and forms (`n.f.`, `n.m. (f. actrice)`, `v. — je chante, nous chantons`) |
| `en` | English translation |
| `fr_sentence`, `en_sentence` | Example sentence and its translation |
| `level` | CEFR level A1–C2 |
| `category` | Topic (Grammar, Food & Drink, Verbs, …) |
| `alt` | Other accepted spellings, separated by `|` |
| `order_freq` | Position in the frequency dictionary |
| `order_level` | Position in the level dictionary |
| `added` | Vocabulary version that added the word (empty for the original words) |

## Sources

- Words, frequency order, pronunciation, gender: [Lexique 4](http://www.lexique.org/) (New, Pallier et al.), CC BY-SA 4.0
- Translations and grammar information: [Wiktionary](https://en.wiktionary.org/), CC BY-SA 4.0, reviewed and edited
- Example sentences: [Tatoeba](https://tatoeba.org/), CC BY 2.0 FR; some edited or written for this list
- Levels A1–C2: [FLELex](https://cental.uclouvain.be/cefrlex/flelex/) (FLELex / Beacco, TreeTagger), CC BY-NC-SA 4.0.
  Please cite: François, T., Gala, N., Watrin, P. & Fairon, C. (2014). *FLELex: a graded lexical resource for French
  foreign learners.* LREC 2014, Reykjavik; and Pintard, A. & François, T. (2020). *Combining Expert Knowledge with
  Frequency Information to Infer CEFR Levels for Words.* READI 2020.
- Review, corrections, added words and the app: [Claude](https://claude.ai) (Anthropic) together with the project author

## Licence

Non-commercial use only: see [LICENSE.md](LICENSE.md).

## Versioning

`version.json` holds the vocabulary version (`vocab`) and the app version with its changes (`app`). The app compares them
with the stored ones and offers an update. New features are tested in `dev/` first.
