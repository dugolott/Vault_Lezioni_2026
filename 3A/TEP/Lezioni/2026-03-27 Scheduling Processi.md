
# 2026-04-10 — Scheduling Processi

tags: [lezione]
classe: 3A
materia: TEP

## Argomento

Scheduling Processi  - Ripasso

## Obiettivi

- Consolidamento concetti chiave

## Spiegazione

 Confronto fra FCFS e FIFO:

- FIFO logica di gestione che può riferirsi a vari ambiti: in informatica ne parliamo come modalità di funzionamento di memorie dette code (queue); tipico il buffer della tastiera o la coda di prefetch della CPU.
- FCFS è anch'essa una logica di tipo FIFO ma è specifica del contesto scheduling; si riferisce ad un ALGORITMO che ha il compito di gestire l'ordine con cui processare dei comandi.

- MQLF algoritmo di scheduling che combina tutte le altre tecniche, in modi diversi per ottimizzare i parametri dello scheduler in funzione del tipo di:
  - processo (CPU bound o I/O bound)
  - carico di lavoro (numero di processi in esecuzione)
  - tempo di esecuzione (processi brevi o lunghi)
  - priorità (processi più o meno importanti)
  - tipologia di sistema (sistemi interattivi, batch o real-time)
- Confronto fra i diversi "setup" di MQLF nei SO più diffusi (windows, linux, macOS).

- Overhead: tempo necessario per eseguire le operazioni di scheduling (cambio di contesto, gestione code, ecc.) che può influire sulle prestazioni del sistema.
	Confronto di alcuni casi di esempio (vedi esercizio)

## Attività

-

## Materiali

-

## Compiti

-

## Note

-

## Immagini

![schema](img/schema.png)
