---
name: gap-analysis
description: >
  Usa questa skill ogni volta che l'utente vuole fare una gap analysis SEO di un articolo rispetto
  ai competitor presenti in SERP. Triggera quando l'utente menziona: "gap analysis", "analisi gap",
  "analisi competitor", "ottimizzare articolo", "cosa manca al mio articolo", "confronto SERP",
  "analisi SERP", "keyword da integrare", "keyword mancanti", "migliorare posizionamento",
  "contenuto da aggiungere", "aggiornare articolo SEO". La skill accetta in input una keyword
  target e l'URL dell'articolo originale pubblicato, esegue lo scraping completo della SERP,
  analizza i contenuti dei top competitor, e produce un report dettagliato con: gap di contenuto,
  keyword semantiche mancanti, sezioni da aggiungere, entità da integrare, ottimizzazioni
  strutturali. Al termine offre di riscrivere l'articolo originale integrando tutte le
  raccomandazioni. USARE SEMPRE questa skill per qualsiasi richiesta di analisi competitiva SEO
  su contenuti o ottimizzazione di un articolo rispetto ai risultati della SERP.
---

# Gap Analysis SEO — Istruzioni Operative

Questa skill esegue un'analisi del divario (gap analysis) tra un articolo originale e i suoi
competitor in SERP, identificando tutto ciò che manca per competere al meglio sul keyword target.

---

## FASE 1 — Raccolta Input

Se la keyword target e/o l'URL dell'articolo originale non sono già stati forniti, chiedi:

1. **Keyword target**: la parola chiave per cui vuoi posizionarti (es. "come fare il pane in casa")
2. **URL articolo originale**: l'URL completo dell'articolo pubblicato da analizzare

Se l'utente ha già fornito entrambi nel messaggio, procedi direttamente alla Fase 2 senza fare
domande.

---

## FASE 2 — Scraping della SERP

Esegui una ricerca WebSearch con la keyword target per ottenere i risultati organici.

**Obiettivo**: raccogliere i top 8-10 URL organici. Escludi: YouTube, Wikipedia, Reddit,
Amazon, e-commerce puri, siti istituzionali (.gov/.edu) a meno che siano rilevanti per il topic.

Costruisci una lista ordinata per posizione in SERP con URL e titolo di ogni risultato.

---

## FASE 3 — Estrazione Contenuto Competitor

Per ogni URL competitor (processa i top 5-7), usa `mcp__workspace__web_fetch` per scaricare
il contenuto della pagina.

Per ogni pagina, estrai e annota:

- **Title tag** e **meta description**
- **H1** principale
- **Struttura heading** completa (H2 → H3 → H4)
- **Word count stimato**
- **Macro-argomenti trattati** (dalle sezioni e heading)
- **Domande a cui risponde** (FAQ, sezioni "come", "perché", "cosa è", ecc.)
- **Entità nominate**: persone, brand, tool, luoghi, concetti chiave, prodotti
- **Keyword semantiche ricorrenti** nel testo

Se una pagina non è accessibile via web_fetch (JavaScript rendering), annota l'URL come
"non accessibile" e prosegui con il prossimo. Focus su heading, prime frasi di ogni sezione,
FAQ e conclusioni — non serve leggere ogni parola.

---

## FASE 4 — Estrazione Articolo Originale

Usa `mcp__workspace__web_fetch` per scaricare l'articolo originale dell'utente.

Estrai le stesse informazioni della Fase 3:
- Title tag, meta description, H1
- Struttura heading completa
- Word count stimato
- Argomenti trattati
- Domande a cui risponde
- Entità menzionate
- Keyword semantiche presenti

---

## FASE 5 — Analisi dei Gap

Confronta l'articolo originale con il set di competitor. L'obiettivo è trovare tutto ciò che
i competitor fanno e l'articolo originale non fa (o fa in modo insufficiente).

### 5a — Gap di Argomenti e Sezioni
Macro-argomenti coperti da ≥2 competitor ma assenti/superficiali nell'articolo originale.
Per ognuno: argomento mancante, quanti competitor lo trattano, proposta di titolo H2/H3.

### 5b — Gap di Keyword Semantiche
Keyword correlate alla principale che appaiono frequentemente nei competitor ma sono poco/nulla
presenti nell'articolo originale. Per ognuna: keyword, frequenza media, dove integrarla.

### 5c — Gap di Entità
Entità importanti (brand, tool, metodologie, nomi propri, termini tecnici) che i competitor
citano ma l'articolo ignora, con indicazione del perché sono rilevanti.

### 5d — Gap Strutturali
- Word count: l'articolo è significativamente più corto dei top competitor?
- Heading depth: i competitor approfondiscono di più con H3/H4?
- Sezioni tipiche assenti: FAQ, Pro/Contro, Tabella comparativa, Guida passo-passo,
  Esempi pratici, Errori comuni, Glossario

### 5e — Gap di Intento di Ricerca
Sfaccettature dell'intento coperte dai competitor ma non dall'articolo originale
(informazionale vs. commerciale, principiante vs. esperto, ecc.).

---

## FASE 6 — Report di Output

Presenta il report in questo formato esatto:

---

# 📊 Gap Analysis SEO — [Keyword Target]

## Overview
- **Keyword analizzata**: [keyword]
- **Articolo originale**: [URL]
- **Competitor analizzati**: [N] su [M] in SERP
- **Word count originale**: ~[N] parole
- **Word count medio competitor**: ~[N] parole
- **Gap score complessivo**: [Basso / Medio / Alto / Critico]

---

## 🔴 Gap Critici (priorità alta)

Per ogni gap critico usa questo schema:

**Gap**: [nome sintetico]
**Dettaglio**: [cosa manca e perché è importante per l'utente e per Google]
**Soluzione**: [cosa aggiungere, titolo H2/H3 suggerito, contenuto da includere]
**Competitor che lo trattano**: [N/M]

---

## 🟡 Gap Secondari (priorità media)

[Gap di keyword semantiche, entità, profondità — meno urgenti ma consigliati]
Stesso schema dei gap critici.

---

## 🟢 Quick Win (basso sforzo, alto impatto)

[Ottimizzazioni rapide: aggiungere keyword nel title, integrare sinonimi in un paragrafo
esistente, aggiungere una FAQ, inserire una tabella — cose che richiedono <30 minuti]

---

## 📝 Keyword da Integrare

| Keyword | Frequenza nei competitor | Dove integrarla |
|---------|--------------------------|-----------------|
| [kw1] | Alta | Introduzione + H2 principale |
| [kw2] | Media | Sezione [X] |

---

## 🏗️ Struttura Consigliata Post-Ottimizzazione

Proposta di struttura heading completa per l'articolo ottimizzato:

```
H1: [titolo ottimizzato]
  H2: [sezione 1]
    H3: [sottosezione]
  H2: [sezione 2]
  ...
  H2: FAQ
    H3: [domanda 1]
    H3: [domanda 2]
```

---

## 📌 Action List Prioritizzata

1. [Azione concreta #1 — la più impattante]
2. [Azione concreta #2]
3. [Azione concreta #3]
...

---

Dopo aver presentato il report completo, chiedi:

> **Vuoi che ottimizzi l'articolo originale sulla base di questa analisi?**
> Posso riscrivere e arricchire l'articolo integrando tutti i gap individuati,
> mantenendo il tono e lo stile originali.
> Rispondi **Sì** per procedere oppure **No** se preferisci solo il report.

---

## FASE 7 — Ottimizzazione Articolo (opzionale)

**Se l'utente risponde sì**, riscrivi l'articolo originale con queste priorità:

1. **Mantieni tono, stile e punto di vista** originale — amplia la voce dell'autore, non
   sostituirla.
2. **Integra tutte le sezioni mancanti** dai gap critici, aggiungendo i nuovi H2/H3 suggeriti.
3. **Inserisci le keyword semantiche** nei punti suggeriti, con naturalezza — no keyword stuffing.
4. **Cita le entità rilevanti** dove pertinente.
5. **Approfondisci le sezioni superficiali** con esempi pratici, dati, step-by-step.
6. **Allinea la struttura heading** a quella consigliata nella Fase 6.
7. **Aggiungi FAQ** se i competitor le usano e l'originale no.

All'inizio dell'articolo ottimizzato, inserisci un riepilogo delle modifiche apportate:

```
> ✏️ **Modifiche apportate**: [lista sintetica dei cambiamenti principali]
```

Se l'articolo ottimizzato supera le ~800 parole, salvalo come file `.md` nella cartella
di lavoro dell'utente e presentalo tramite il tool `present_files`.

---

## Note Operative

- Se un URL non è accessibile, segnalalo nel report e prosegui con i dati disponibili.
- Per keyword italiane, considera varianti con/senza accenti e forme flesse comuni.
- Il word count si stima sul contenuto visibile, non sull'HTML.
- Se la SERP mostra risultati in lingue miste, concentrati sugli URL nella stessa lingua
  dell'articolo originale.
- **Il report deve essere specifico e azionabile.** Evita consigli generici ("scrivi contenuti
  di qualità", "migliora la UX"). Ogni raccomandazione deve indicare *cosa* aggiungere e *dove*.
- Usa dati concreti: "5 su 7 competitor trattano questo argomento", "la keyword X appare in
  media 8 volte nei top 5 risultati", ecc.
