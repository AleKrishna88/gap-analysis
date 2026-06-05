# Gap Analysis SEO — Skill per Claude (Cowork)

**Gap Analysis SEO** è una skill per Claude Cowork che analizza automaticamente il tuo articolo rispetto ai competitor presenti in SERP, identifica tutto ciò che manca per competere sulla keyword target e — se vuoi — riscrive l'articolo ottimizzato mantenendo il tuo stile.

Basta fornire una keyword e l'URL del tuo articolo: la skill scrapa i top risultati organici, confronta struttura, argomenti, keyword semantiche ed entità, e produce un report d'azione con gap critici, quick win e struttura heading consigliata. Alla fine puoi scegliere se ricevere solo il report o avere l'articolo riscritto e pronto da pubblicare.

---

## Cosa fa

1. **Analizza la SERP** per la keyword target (top 8-10 risultati organici)
2. **Scrapa i top 5-7 competitor** estraendo struttura, heading, keyword semantiche ed entità
3. **Confronta il tuo articolo** con i competitor su argomenti, keyword, entità, struttura e intento
4. **Produce un report** con gap critici, gap secondari, quick win, keyword da integrare e struttura consigliata
5. **Riscrive l'articolo** ottimizzato (opzionale), mantenendo tono e stile originali

---

## Come installare

### Opzione A — Installazione manuale

1. Copia la cartella `gap-analysis/` in:
   - **macOS/Linux**: `~/.claude/skills/`
   - **Windows**: `%APPDATA%\Claude\skills\`
2. Riavvia Claude Cowork

### Opzione B — Tramite file `.skill`

Se hai il file `.skill` (zip rinominato), trascinalo direttamente nell'interfaccia di Claude Cowork oppure installalo via Settings → Skills → Install from file.

---

## Come usare

Nella chat di Claude Cowork, scrivi uno di questi trigger:

```
/gap-analysis
gap analysis di questo articolo: [URL]
analizza i gap SEO per la keyword: [keyword]
cosa manca al mio articolo su [topic]?
confronto SERP per [keyword]
```

Claude chiederà (se non forniti):
- **Keyword target** — es. `miglior crm per piccole imprese`
- **URL articolo originale** — es. `https://tuosito.it/articolo`

---

## Output del report

Il report include:

| Sezione | Contenuto |
|---|---|
| 🔴 Gap Critici | Argomenti/sezioni mancanti, priorità alta |
| 🟡 Gap Secondari | Keyword semantiche, entità, profondità |
| 🟢 Quick Win | Ottimizzazioni rapide (<30 min) |
| 📝 Keyword da Integrare | Tabella con frequenza e posizione consigliata |
| 🏗️ Struttura Consigliata | Heading H1→H2→H3 post-ottimizzazione |
| 📌 Action List | Azioni concrete prioritizzate |

---

## Requisiti

- Claude Cowork (desktop app) con accesso a WebSearch e web_fetch
- Nessuna dipendenza esterna o API aggiuntiva

---

## Struttura del repository

```
gap-analysis/
├── SKILL.md      # Istruzioni operative della skill (lette da Claude)
└── README.md     # Questo file
```

---

## Licenza

MIT — libero uso, modifica e distribuzione.
