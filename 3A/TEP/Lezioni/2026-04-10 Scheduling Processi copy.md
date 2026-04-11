
# 2026-04-10 — Scheduling Processi

tags: [lezione]
classe: 3A
materia: TEP

## Argomento

Scheduling Processi

## Obiettivi

- Algoritmi di scheduling: FCFS, SJF, Priority, Round Robin, MQLF
- Caratteristiche e parametri degli algoritmi di scheduling
- Overhead dello scheduler e impatto sulle prestazioni del sistema

## Spiegazione

#### Algoritmi di scheduling

- **First-Come, First-Served (FCFS)**: i processi vengono eseguiti nell'ordine di arrivo.
- **Shortest Job First (SJF)**: il processo con il tempo di esecuzione più breve viene eseguito per primo.
- **Shortest Remaining Time First (SRFT)** è una variante *preemptive* di SJF, in cui un processo può essere interrotto se arriva un processo con un tempo di esecuzione più breve.
- **Priority Scheduling**: i processi vengono eseguiti in base alla loro priorità, con priorità più alta eseguita prima. Può essere *preemptive* o *non-preemptive*. La versione *preemptive* può causare starvation se processi con priorità più alta continuano ad arrivare.
- **Round Robin (RR)**: i processi vengono eseguiti in modo ciclico, con un quanto di tempo (time slice) assegnato a ciascun processo.
- **Multilevel Feedback Queue Scheduling (MLFQ)**: simile a MQLF, ma i processi possono essere spostati tra le code in base al loro comportamento e al tempo di esecuzione.

#### Criticità degli algoritmi di scheduling

- **Starvation**: alcuni processi potrebbero non ricevere mai la CPU se altri processi con priorità più alta continuano ad arrivare (tipico di Priority Scheduling o SRTF).
- **Convoy Effect**: in FCFS, un processo lungo può bloccare l'esecuzione di processi più brevi, causando un aumento del tempo di attesa (tipico di FCFS).
- **Overhead dello scheduler**: il tempo speso dallo scheduler per gestire i processi (context switch) può ridurre l'efficienza del sistema, soprattutto in algoritmi come Round Robin con un quanto di tempo troppo breve.
- **Deadlock**: in sistemi con risorse condivise, i processi potrebbero bloccarsi reciprocamente, impedendo l'esecuzione di entrambi (può verificarsi in qualsiasi algoritmo se non gestito correttamente).

#### Concetti chiave

- **Context Switch**: il processo di salvare lo stato di un processo (**PCB**) e caricare lo stato di un altro processo, che comporta un overhead.
- **Time Slice (Q)**: la quantità di tempo assegnata a ciascun processo in Round Robin, che influisce sulla reattività e sull'overhead del sistema.
- **Preemption**: la capacità dello scheduler di interrompere un processo in esecuzione per assegnare la CPU a un altro processo, tipica di algoritmi come Round Robin e Priority Scheduling.
- **Non-preemptive scheduling**: una volta che un processo inizia a essere eseguito, continua fino al completamento, tipico di FCFS e SJF.
- **RTC**: Real-Time Clock, utilizzato per gestire i timer e le interruzioni (Interrupt), fondamentale per il funzionamento dello scheduler.

#### Obiettivi degli algoritmi di scheduling

- **Equità**: garantire che tutti i processi abbiano accesso alla CPU in modo equo.
- **Efficienza**: massimizzare l'utilizzo della CPU e minimizzare il tempo di attesa dei processi.
- **Reattività**: garantire che i processi interattivi ricevano risposte rapide.
- **Minimizzazione dell'overhead**: ridurre al minimo il tempo speso dallo scheduler per gestire i processi.

#### Parametri degli algoritmi di scheduling

- **T0**
  Tempo di arrivo del processo (stato NEW)

- **CPU Utilization**
  `CPU Utilization = Tbusy / (Tbusy + Tidle)`

- **Throughput**
  `Throughput = Nprocessi completati / unità di tempo`

- **Waiting Time (Tw)**
  Tempo trascorso nella ready queue, in attesa di essere eseguito

- **Turnaround Time (Ta)**
  Tempo totale trascorso dal momento dell'arrivo del processo al completamento:
  `Ta = Tproc_completed - T0`

- **Response Time (Tr)**
  Tempo trascorso dal momento dell'arrivo del processo al primo avvio sulla CPU:
  `Tr = Tfirst_run - T0`

- **Dispatch latency / Context switch (Tcsw)**
  Tempo necessario allo scheduler per fermare un processo e avviarne un altro

- **Overhead (%)**
  `Overhead = Tcsw / (Q + Tcsw) · 100`

## Attività

- Esercizi di calcolo e confronto degli algoritmi di scheduling, FCFS, SJF, SRFT e RR.

## Materiali

- Da pag. 272 a pag. 283 del libro di testo

## Compiti

-

## Note

-

## Immagini

![schema](img/schema.png)
