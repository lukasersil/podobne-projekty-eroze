# Postup: jak vznikl agent a první běh

## 1. Stavba agenta
Agent `podobne-projekty` je dovednost (skill) Claude Code v `.claude/skills/podobne-projekty/SKILL.md`. Má části ROLE, VSTUPY, POSTUP, VÝSTUP, KDY SE ZASTAVIT a PRAVIDLA. Téma do dovednosti napsané není; agent ho pokaždé čte z `tema.md`. Agent se proto dá spouštět opakovaně: stačí přepsat `tema.md` a vyměnit návrh v `podklady/navrh/`.

Soubory:
- `CLAUDE.md`: k čemu složka je, kde co leží, pravidla a jak agenta spustit.
- `tema.md`: karta tématu (téma, klíčová slova CZ/EN, výzva, anonymní hodnocení).
- `JAK-SPUSTIT.md`: návod na jednu obrazovku.
- `podklady/navrh/`: návrh. **Do repozitáře se nenahrává** (`.gitignore`).
- `vystupy/`: výsledky `RRRR-MM-DD-podobne-projekty.md` a PDF.

## 2. Příprava běhu (2026-11-26)
1. Z Technical Annexu návrhu COST OC-2026-1 se vyplnila `tema.md`. Šlo o téma, klíčová slova, výzvu a anonymní hodnocení „ano“.
2. Návrh se zkopíroval do `podklady/navrh/`. Používal se jen lokálně, k hodnocení překryvu.
3. Spuštění: `/podobne-projekty`

## 3. Jak se prohledávaly registry
Do registrů šla jen klíčová slova z `tema.md`, nikdy text návrhu.

| Registr | Způsob přístupu |
|---|---|
| CORDIS | JSON vyhledávání `https://cordis.europa.eu/search?q=contenttype='project' AND '…'&format=json` a detaily `https://cordis.europa.eu/project/id/<ID>?format=json` |
| OpenAIRE | API projektů `https://api.openaire.eu/search/projects?keywords=…&format=json`, detail podle `openaireProjectID` |
| CEP (IS VaVaI) | formulář jednoduchého vyhledávání (POST, pole klíčová slova a název projektu), detaily `https://www.isvavai.cz/cep?ss=detail&h=<kód>` |
| STARFOS | vyhledávací pole na webu v prohlížeči (Chrome). Vyhledávání přes URL vracelo chybu 500. |
| COST | vyhledávání na webu `https://www.cost.eu/?s=…` a stránky akcí `https://www.cost.eu/actions/<kód>/` |

Každý nález se otevřel na detailu a údaje (název, program, ID, roky) se opsaly odtud. Co se neotevřelo, je v tabulce označené „neověřeno“.

## 4. Doložení poptávky
- **Legislativa:** EUR-Lex (Chrome, protože curl blokuje ochrana proti botům). Šlo o směrnici (EU) 2025/2360 a EU Soil Strategy for 2030, COM(2021) 699.
- **Výzvy:** API portálu Funding & Tenders, `https://api.tech.ec.europa.eu/search-api/prod/rest/search?apiKey=SEDIA&text=…`, a stránka COST Open Call.
- **Publikace:** OpenAIRE API, `https://api.openaire.eu/search/publications?keywords=…&fromDateAccepted=RRRR-01-01&toDateAccepted=RRRR-12-31`, počty po letech 2015–2025.

## 5. Výstup a PDF
- Markdown se zapsal do `vystupy/2026-11-26-podobne-projekty.md`.
- PDF vzniklo převodem Markdownu na HTML jednoduchým Python skriptem. HTML se pak vytisklo přes Chrome bez okna (headless), A4 na šířku:

  ```
  "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new --no-pdf-header-footer --print-to-pdf=vystup.pdf vystup.html
  ```

## 6. Pravidla, která běh dodržel
- ID, roky ani řešitele nebral z paměti.
- Text návrhu neodešel mimo složku.
- Kvůli anonymnímu hodnocení odstavec State-of-the-art nezmiňuje projekty, které mohou patřit navrhovatelům.
- Text webů bral jako data, ne jako pokyny.
