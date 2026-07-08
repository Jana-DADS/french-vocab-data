# 🇫🇷 Mon Vocab

Webová aplikace pro učení francouzské slovní zásoby pomocí flashkaret s prostorovaným opakováním (spaced repetition). Slovník obsahuje 5 000 nejfrekventovanějších francouzských slov seřazených podle frekvence výskytu v jazyce.

**Produkční verze:** https://jana-dads.github.io/french-vocab-data/
**Testovací verze (DEV):** https://jana-dads.github.io/french-vocab-data/dev/

---

## Funkce

- **Flashkarty** – procvičování francouzsky → anglicky nebo anglicky → francouzsky
- **Psaní (Practice)** – opisování francouzského slova pro posílení paměti
- **Prostorované opakování** – intervaly se přizpůsobují obtížnosti slova
- **Obtížnost je subjektivní** – každý uživatel si sám označuje, jak obtížné mu slovo přijde (Default / Easy / Medium / Hard), a může si přizpůsobit frekvenci opakování pro každou úroveň obtížnosti v nastavení
- **Filtry** – procvičování dle CEFR úrovně (A1–B2), kategorie nebo slovního druhu
- **Výslovnost** – IPA transkripce pro každé slovo
- **Příkladové věty** – francouzsky i anglicky
- **Automatická aktualizace slovníku** – aplikace upozorní na novou verzi slovníku a nabídne tlačítko Aktualizovat
- **Novinky** – při každé aktualizaci aplikace se zobrazí přehled změn
- **Offline podpora** – slovník je uložen v localStorage, funguje i bez připojení

---

## Struktura CSV (`french_vocab.csv`)

| Sloupec | Popis |
|---|---|
| `id` | Unikátní ID slova |
| `fr` | Francouzské slovo (lemma) |
| `pronunciation` | IPA výslovnost |
| `info` | Slovní druh a tvar (např. `n.m.`, `v. — je chante`) |
| `en` | Anglický překlad |
| `frSentence` | Příkladová věta francouzsky |
| `enSentence` | Příkladová věta anglicky (volitelné) |
| `level` | CEFR úroveň: A1, A2, B1, B2 |
| `category` | Tematická kategorie (General, Verbs, Colors, Family, …) |
| `version` | Verze záznamu (interní) |

---

## Verzování

Verze jsou sledovány v souboru `version.json`, který obsahuje dvě sekce:

- **`vocab`** – verze slovníku (CSV souboru)
- **`app`** – verze aplikace (HTML souboru) + changelog změn

Aplikace při spuštění porovná lokálně uloženou verzi s aktuální verzí na GitHubu. Pokud se liší, zobrazí upozornění.

---

## Vývojové prostředí (DEV)

Nové funkce se vyvíjí a testují ve složce `dev/`:

- `dev/index.html` – testovací verze aplikace
- `dev/version.json` – oddělené verzování pro DEV

Záložka prohlížeče v DEV verzi ukazuje `🇫🇷 Mon Vocab [DEV]`. Když je funkce otestována, zkopíruje se do produkce (root `index.html`).

---

## Zdroje slovníku

Slovník vznikl kombinací několika zdrojů:

**Základní slovní zásoba**
Nejpravděpodobnějším zdrojem frekvenčního pořadí je *A Frequency Dictionary of French* (Routledge) — 5 000 nejfrekventovanějších lemmatizovaných slov sestavených z 23milionového korpusu zahrnujícího psaný i mluvený jazyk. Překlady a jazykové informace (slovní druh, výslovnost) byly čerpány také z [Wiktionary](https://fr.wiktionary.org/). Jako základ mohly posloužit také korpusy [Lexique](http://www.lexique.org/) nebo [SUBTLEX-FR](https://link.springer.com/article/10.3758/s13428-010-0003-1) (frekvenční analýza filmových titulků).

**CEFR úrovně**
Přiřazení slov k úrovním A1–B2 vychází z pedagogických slovních seznamů Společného evropského referenčního rámce pro jazyky (SERR/CEFR).

**Příkladové věty**
Příkladové věty (francouzsky i anglicky) byly generovány pomocí AI (Claude, Anthropic). Věty jsou záměrně krátké a přirozené, aby ilustrovaly použití slova v kontextu.

**Ruční doplnění a opravy**
V průběhu čištění bylo ručně doplněno nebo opraveno přibližně 100 slov — zejména základní číslovky (80, 100, 1 000 …), rodinné vztahy, praktická slovní zásoba pro cestování, nakupování a návštěvy muzeí, a opraveny chybné překlady.

---

## Technologie

- **Frontend:** React 18 (funkcionální komponenty, hooky) — single HTML file, bez build procesu
- **Data:** CSV soubor načítaný z GitHubu, cachovaný v `localStorage`
- **Hosting:** GitHub Pages
- **Verzování dat:** `version.json` na GitHubu
