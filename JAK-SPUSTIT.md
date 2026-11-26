# Jak spustit agenta podobne-projekty

**1. Vyplň `tema.md`**
Téma jednou větou, klíčová slova česky i anglicky, výzvu (nebo „žádná“)
a anonymní hodnocení (ano/ne). Nenech v souboru žádné `[DOPLNIT]`.

**2. Vlož návrh do `podklady/navrh/`** (nepovinné)
Slouží jen k hodnocení překryvu a ke kontrole projektů navrhovatelů.
Ze složky nikam neodchází.

**3. Spusť v Claude Code v této složce:**
```
/podobne-projekty
```

**4. Výsledek:** `vystupy/RRRR-MM-DD-podobne-projekty.md`
- tabulka projektů (ověřeno / neověřeno),
- poptávka: legislativa EU, projekty a výzvy, vývoj publikací,
- odstavec State-of-the-art anglicky (≤ 150 slov),
- **Co ověřit ručně** – projdi vždy, než cokoli převezmeš do návrhu.

**Nové téma = nový běh:** přepiš `tema.md`, vyměň návrh v `podklady/navrh/`
a spusť znovu. Starší výstupy zůstávají.

**Agent nedělá:** nehledá odborné články, nehodnotí návrh, nic neodesílá,
nepublikuje ani nemaže.
