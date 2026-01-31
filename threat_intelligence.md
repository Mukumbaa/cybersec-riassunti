
# Lezione su Cyber Threat Intelligence (CTI)

Questa lezione fornisce una panoramica completa della **Cyber Threat Intelligence (CTI)**, l'intelligence informatica, che è il processo di raccolta, analisi e interpretazione di informazioni sulle minacce informatiche per supportare la prevenzione, il rilevamento e la risposta agli attacchi.

---

## 1. Cos'è la Cyber Threat Intelligence?

La CTI si basa **sull'analisi e correlazione di dati provenienti da molteplici fonti** per ricostruire le fasi di un attacco, elencando tecniche, vulnerabilità sfruttate, malware utilizzati, ecc. Non è semplicemente una raccolta di dati (come liste di IP malevoli), ma è **l'informazione contestualizzata e analizzata** che fornisce **intelligence** operativa.

**L'obiettivo finale** della CTI è duplice:
1.  **Prevenire** un attaccante dall'avere successo, anticipando le sue mosse.
2.  **Riconoscere e rispondere efficacemente** a un attacco già in corso o concluso.

Il fine ultimo è **comprendere le motivazioni, i bersagli e i comportamenti degli aggressori**, per aiutare la comunità a migliorare protezione, rilevamento e risposta.

---

## 2. Modelli di Riferimento: Cyber Kill Chain e MITRE ATT&CK

Per analizzare e descrivere gli attacchi in modo strutturato, si utilizzano due modelli fondamentali.

### A. Cyber Kill Chain
Sviluppato da Lockheed Martin, è un modello lineare in **sette fasi** che descrive la progressione di un attacco informatico:
1.  **Ricognizione (Reconnaissance)**: L'attaccante raccoglie informazioni sul bersaglio (email, conferenze, dati pubblici).
2.  **Preparazione dell'arma (Weaponization)**: Si accoppia un exploit (per sfruttare una vulnerabilità) con un backdoor (per mantenere accesso) in un "pacchetto" consegnabile (es. un PDF maligno).
3.  **Consegna (Delivery)**: Il pacchetto viene inviato alla vittima via email, web, chiavetta USB, ecc.
4.  **Sfruttamento (Exploitation)**: Il codice maligno viene eseguito sul sistema della vittima, sfruttando una vulnerabilità.
5.  **Installazione (Installation)**: Il malware si installa sul sistema, assicurandosi la persistenza.
6.  **Comando e Controllo (Command and Control - C2)**: Viene stabilito un canale di comunicazione remoto con l'attaccante.
7.  **Azioni sugli obiettivi (Actions on Objectives)**: Con l'accesso "hands on keyboard" (manuali sulla tastiera), l'intruso raggiunge i suoi obiettivi finali: rubare dati, cifrare file, ecc.

### B. MITRE ATT&CK
È un modello più sofisticato e granulare sviluppato da MITRE. Mentre la Cyber Kill Chain è lineare, ATT&CK è una **matrice tassonomica** che cataloga centinaia di **tecniche** e **sotto-tecniche** raggruppate in **tattiche**. Fornisce una visione più realistica e non lineare del comportamento degli avversari.

**Struttura di ATT&CK:**
*   **Tattiche (Tactics)**: Rappresentano il "perché" di una tecnica, lo scopo tattico dell'avversario (es. "Accesso Iniziale", "Movimento Laterale", "Esfiltrazione").
*   **Tecniche (Techniques)**: Il "come", le azioni specifiche per raggiungere una tattica (es. "Phishing", "Sfruttamento di Vulnerabilità Remota", "Utilizzo di PowerShell").
*   **Sotto-Tecniche (Sub-Techniques)**: Descrizioni ancora più dettagliate (es. "Phishing via Email").

ATT&CK è utile per **documentare il comportamento dei gruppi avversari** indipendentemente dagli strumenti usati, permettendo una migliore caccia alle minacce (threat hunting) e analisi post-incidente.

---

## 3. I Tre Livelli di Threat Intelligence

La CTI opera a tre diversi livelli, ognuno con uno scopo e un pubblico specifici:

*   **Intelligence Tattica (Tactical CTI)**:
    *   **Focus**: Sul "cosa" tecnico immediato.
    *   **Esempi**: **Indicatori di Compromissione (IOCs)** come indirizzi IP, domini, hash di file malevoli, analisi del reverse engineering del malware, dettagli del traffico di rete e comportamento degli host.
    *   **Pubblico**: Analisti SOC (Security Operations Center), team di risposta agli incidenti. Viene utilizzata per configurare firewall, IDS/IPS e strumenti di rilevamento.

*   **Intelligence Operativa (Operational CTI)**:
    *   **Focus**: Sul "come" e "chi". Comportamento, motivazioni, intenti e capacità (TTPs - Tactics, Techniques and Procedures) degli avversari.
    *   **Esempi**: Cronologia delle campagne, descrizioni comportamentali, operazioni end-to-end di un gruppo specifico (es. "APT28").
    *   **Pubblico**: Team di Threat Hunting, analisti di intelligence. Aiuta a informare decisioni di acquisto e raccolta dati per migliorare la difesa.

*   **Intelligence Strategica (Strategic CTI)**:
    *   **Focus**: Sul "perché" più ampio e sull'impatto sul business.
    *   **Esempi**: Background degli avversari, intenti e motivazioni valutate, impatto aziendale, previsioni sull'evoluzione degli avversari.
    *   **Pubblico**: Direttori della Sicurezza (CISO), dirigenti, consiglio di amministrazione. Viene utilizzata per informare decisioni aziendali, gestione del rischio e allocazione degli investimenti in sicurezza.

---

## 4. Fonti, Raccolta e Analisi dei Dati

La CTI si nutre di dati provenienti da molteplici fonti:
*   **Fonti interne**: Log di sistema, di rete, di applicazioni, di firewall, IDS, EDR.
*   **Fonti esterne pubbliche**: **Shodan** (per scoprire dispositivi esposti su Internet), **Google Dorks** (per trovare informazioni sensibili indicizzate), database di vulnerabilità (CVE), rapporti di sicurezza pubblici.
*   **Fonti esterne private/comunitarie**: Piattaforme di condivisione come **MISP**, feed di intelligence a pagamento.
*   **Fonti umane (HUMINT)**: Riferita alla raccolta di informazioni da persone, anche online (es. monitoraggio di forum chiusi tramite "personaggi" o "puppet").

Tutte queste informazioni vengono **correlate e fuse** utilizzando strumenti di data science, machine learning e intelligenza artificiale per estrarre conoscenza significativa.

---

## 5. Gestione dei Log e SIEM

I **log** sono la fonte primaria di dati per la CTI interna. Sono registrazioni di eventi generati da sistemi operativi, applicazioni e dispositivi di rete. Contengono timestamp, descrizioni degli eventi e sono essenziali per valutare la salute, le prestazioni e la sicurezza del sistema.

La gestione dei log è critica (rotazione, archiviazione) per evitare di riempire lo storage e per rispettare i vincoli normativi.

**SIEM (Security Information and Event Management)** è la tecnologia centrale che abilita la CTI operativa. Un sistema SIEM:
*   **Raccoglie** log e dati di sicurezza da fonti eterogenee (firewall, server, endpoint, applicazioni).
*   **Correla** gli eventi nel tempo (es. un login fallito da un IP, seguito da una connessione sospetta dallo stesso IP a un server database).
*   **Analizza** i dati per individuare anomalie e pattern di attacco.
*   **Si integra** con tassonomie esterne come ATT&CK per classificare le minacce.
*   **Fornisce** dashboard di visualizzazione e allerta.

Esempi di strumenti SIEM: Splunk, IBM QRadar, Elastic SIEM (ELK), Microsoft Sentinel, Exabeam.

---

## 6. Indicatori di Compromissione (IOC) e Analisi del Malware

Gli **IOC** sono "fatti" o "artefatti" forensi che indicano una potenziale intrusione (es. hash di file malevolo, indirizzo IP C2, nome di dominio sospetto). Sono il cuore dell'intelligence tattica e possono essere condivisi nella comunità per migliorare le difese collettive.

L'analisi del malware avviene spesso in **sandbox**, ambienti virtuali isolati e controllati dove il codice sospetto può essere eseguito in sicurezza mentre si registrano tutte le sue attività (creazione di processi, chiamate di sistema, traffico di rete). Servizi online come Any.Run, Hybrid-Analysis e VirusTotal offrono queste capacità. Strumenti on-premise come **Cuckoo Sandbox** sono ampiamente utilizzati.

---

## 7. Condivisione e Standardizzazione

Per rendere efficace la condivisione della CTI, sono stati sviluppati **standard e formati**:
*   **STIX (Structured Threat Information eXpression)**: Linguaggio per descrivere informazioni sulle minacce.
*   **TAXII (Trusted Automated eXchange of Indicator Information)**: Protocollo per lo scambio sicuro di informazioni STIX.
*   **MAEC (Malware Attribute Enumeration and Characterization)**: Linguaggio per caratterizzare il malware.
*   **MISP (Malware Information Sharing Platform & Threat Sharing)**: Piattaforma open-source per la condivisione collaborativa di IOCs e informazioni sulle minacce.

---

## 8. Esempi Pratici e Applicazioni

La lezione conclude con numerosi esempi pratici di come la CTI viene applicata:
*   **Analisi di malware specifici**: Come **Emotet**, **Shamoon** o **Black Basta**, utilizzando ATT&CK per mapparne le TTPs.
*   **Utilizzo di cataloghi**: Come il **KEV (Known Exploited Vulnerabilities)** del CISA, per prioritizzare la patch di vulnerabilità attivamente sfruttate.
*   **Mappe delle minacce in tempo reale**: Fornite da vendor come Kaspersky o Fortinet per una visualizzazione immediata dell'attività malevola globale.
*   **Tool di ricerca**: Come **Maltego** per la link analysis e la visualizzazione delle relazioni tra entità (domini, IP, persone).

---

## Domande da Esame

1.  **Definisci la Cyber Threat Intelligence (CTI) e spiega la differenza tra "dati" e "intelligence" in questo contesto. Quali sono i due obiettivi principali della CTI?**
2.  **Descrivi le sette fasi della Cyber Kill Chain di Lockheed Martin. Perché è considerato un modello utile per la difesa?**
3.  **Spiega la struttura del framework MITRE ATT&CK. Cosa sono le "Tattiche" e le "Tecniche"? Perché ATT&CK è considerato più sofisticato della Cyber Kill Chain?**
4.  **Distingui tra i tre livelli di Threat Intelligence (Tattico, Operativo, Strategico). Per ognuno, indica il focus, un esempio concreto e il pubblico di riferimento principale.**
5.  **Cosa sono gli Indicatori di Compromissione (IOC)? Fai tre esempi diversi di IOC e spiega come possono essere utilizzati da un team di sicurezza.**
6.  **Qual è il ruolo di un sistema SIEM (Security Information and Event Management) nell'ambito della Cyber Threat Intelligence? Elenca almeno tre funzionalità chiave di un SIEM.**
7.  **Spiega cos'è un "sandbox" nel contesto dell'analisi del malware. Perché è uno strumento fondamentale per la CTI tattica?**
8.  **Perché la standardizzazione è importante nella condivisione della CTI? Cita due standard o formati (es. STIX, TAXII) e spiega brevemente a cosa servono.**
9.  **Descrivi come strumenti come Shodan o Google Dorks possano essere utilizzati come fonti di intelligence nella fase di Ricognizione (Reconnaissance).**
10. **Prendi come esempio un attacco ransomware. Utilizzando il modello ATT&CK, elenca almeno tre tattiche che il gruppo ransomware potrebbe perseguire e, per ognuna, una possibile tecnica associata.**
