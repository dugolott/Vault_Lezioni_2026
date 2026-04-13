# 2026-04-10 — WiFi e autenticazione (Enterprise)

tags: [lezione]
classe: quarta
materia: Informatica

## Argomento

Tecniche di autenticazione WiFi: Enterprise, RADIUS, Captive Portal

## Obiettivi

- Comprendere i modelli di sicurezza WiFi
- Distinguere autenticazione base vs enterprise
- Capire il ruolo del server RADIUS
- Comprendere il concetto di NAS

## Spiegazione

### Sicurezza WiFi: contesto

Cosa intendiamo per sicurezza?
In una parola, basta ricordare alla C.I.A.: Confidentiality, Integrity, Availability.
Ovvero:

- Protezione dei dati trasmessi --> *cifratura* (Confidentiality)
- Protezione da alterazioni dei dati trasmessi --> *integrità* (Integrity)
- Protezione da accessi non autorizzati --> *autenticazione* (Availability)

Per quanto riguarda l'*autenticazione*, le reti WiFi possono adottare diversi livelli di sicurezza:

- Open (nessuna autenticazione) --> vulnerabile a chiunque, soluzione non accettabile per reti private, aziendali o pubbliche
- PSK (password condivisa) --> semplice ma poco sicura (password condivisa: un segreto è tale solo se è conosciuto da pochi, ma in questo caso è condiviso da tutti)
- Enterprise (autenticazione centralizzata) --> ogni utente ha credenziali univoche, gestite da un server centrale (RADIUS)

Al di là del modello di autenticazione, quello che veramente garantisce la triade CIA della sicurezza è il protocollo di cifratura. In ordine di sicurezza crescente, abbiamo:

1. WEP --> Deprecato, vulnerabile
2. WPA --> Miglioramento rispetto a WEP, ma oramai vulnerabile
3. WPA2 --> Miglioramento rispetto a WPA, con maggiore sicurezza
4. WPA3 --> Ultimo standard, con la massima sicurezza e integrità

---

### Sicurezza Enterprise (WPA2/WPA3 Enterprise)

Si basa su un'infrastruttura centralizzata che prevede:

- un server RADIUS
- uno o più NAS (Network Access Server) che fungono da client del RADIUS, agendo come intermediari tra i dispositivi degli utenti e il server di autenticazione

#### RADIUS

Remote Authentication Dial-In User Service

È un server AAA:

- **Authentication**: verifica identità
- **Authorization**: determina permessi
- **Accounting**: traccia accessi e attività

#### Credenziali UNIVOCHE

A differenza del PSK:

- ogni utente ha username/password propri
- maggiore sicurezza e tracciabilità

Oltre alle credenziali degli utenti, è fondamentale che anche i NAS (l'Access Point) si autentichino al RADIUS.
Questo processo di autenticazione reciproca garantisce la sicurezza dell'intera infrastruttura WiFi, prevenendo:

- accessi non autorizzati al server RADIUS (ad esempio, da parte di dispositivi non autorizzati che tentano di impersonare un NAS)
- proteggendo le credenziali degli utenti da potenziali attacchi MITM (Man-In-The-Middle) che potrebbero intercettare le comunicazioni tra NAS e RADIUS

---

### NAS (Network Access Server)

⚠️ In questo contesto NON è Network Attached Storage, ovvero un dispositivo di archiviazione collegato alla rete.

È il client del RADIUS, tipicamente:

- Access Point (AP)
- Controller WiFi

#### Ruolo

- riceve richieste di connessione dai client utente
- inoltra le richieste di autenticazione al RADIUS
- in base alla risposta del RADIUS, concede o nega l'accesso alla rete

---

### Flusso semplificato

0. Il NAS (AP) si autentica al RADIUS ed instaura un canale cifrato
1. Client Richiede connessione al NAS
2. AP (NAS) inoltra richiesta al RADIUS
3. RADIUS verifica credenziali del client
4. Se OK → accesso alla rete (può partire DORA del DHCP per fornire IP al client)
5. RADIUS registra attività (Accounting)

---

### Captive Portal

E' il meccanismo di autenticazione utilizzato in molte reti WiFi pubbliche, come quelle di hotel, aeroporti o caffè.

Rete:

- apparentemente aperta (NO lucchetto nelle icone WiFi)
- ma con accesso limitato (finchè non ci si autentica non si ha accesso a internet)

#### Funzionamento

- utente si connette
- viene reindirizzato a pagina web
- inserisce dati (email / telefono)
- dopo autenticazione → accesso internet

#### Collegamento con AAA

- Rappresenta un elementare interfaccia di registrazione e autenticazione,su RADIUS o altri sistemi di backend

---

## Attività

- Analizzare una rete WiFi reale (scuola/casa)
- Identificare tipo di autenticazione
- Sperimentare RADIUS con CPT

## Materiali

- Slide
- Packet Tracer

## Compiti

- Completare gli esercizi su Packet Tracer dell'esercitazione di marzo
- Completare e correggere esercizi su RADIUS secondo le correzioni fornite in classe

## Note

## Immagini
