# Podobné projekty: agent a rešerše

Agent pro Claude Code, který k tématu najde projekty, sítě a akce, které už na něm pracují (STARFOS, CEP, CORDIS, COST, OpenAIRE). Doloží poptávku a napíše anglický odstavec State-of-the-art.

## Obsah
- [`.claude/skills/podobne-projekty/SKILL.md`](.claude/skills/podobne-projekty/SKILL.md): definice agenta
- [`CLAUDE.md`](CLAUDE.md): pravidla složky
- [`tema.md`](tema.md): karta tématu (teď vyplněná pro první běh)
- [`JAK-SPUSTIT.md`](JAK-SPUSTIT.md): jak agenta spustit
- [`POSTUP.md`](POSTUP.md): jak agent vznikl a jak proběhl první běh
- [`vystupy/`](vystupy/): výsledky. První běh je [2026-11-26 v PDF](vystupy/2026-11-26-podobne-projekty.pdf) a [v Markdownu](vystupy/2026-11-26-podobne-projekty.md).

Text návrhu (`podklady/navrh/`) v repozitáři záměrně není.

## Spuštění
Naklonuj repozitář, vyplň `tema.md`, vlož návrh do `podklady/navrh/` a v Claude Code v této složce napiš:

```
/podobne-projekty
```

Údaje ve výstupech platí ke dni běhu. Než je použiješ, projdi oddíl „Co ověřit ručně“.
