
# Lezione su Threat Modeling (Modellazione delle Minacce)

Questa lezione fornisce una panoramica completa e strutturata del **Threat Modeling**, una metodologia proattiva e strategica per identificare, valutare e mitigare i rischi di sicurezza in un sistema software o in un'applicazione **prima che venga sviluppato o durante il suo ciclo di vita**.

---

## 1. Cos'è il Threat Modeling?

Il Threat Modeling è definito come:

> **"Un processo strategico volto a considerare possibili scenari di attacco e vulnerabilità all'interno di un ambiente applicativo proposto o esistente, allo scopo di identificare chiaramente i livelli di rischio e impatto."** (UcedaVelez & Morana, 2015)

In termini semplici, è il processo di **pensare come un attaccante** per capire dove un sistema potrebbe essere vulnerabile, prima che qualcuno lo sfrutti realmente. È fondamentale perché un'applicazione diventa un bersaglio quando un attacco fornisce un **ritorno sull'investimento (ROI)** per l'aggressore.

**Obiettivi principali:**
1.  Comprendere il **contesto di business** dell'applicazione e identificare i suoi **asset** (ciò che è prezioso).
2.  Identificare i possibili **agenti di minaccia** (chi potrebbe attaccare) e i loro obiettivi.
3.  **Generalizzare** le minacce per applicazioni con funzionalità simili.
4.  **Prioritizzare** le misure di sicurezza per mitigare i rischi in modo efficace ed efficiente.

---

## 2. Perché fare Threat Modeling? (Reasons to Threat Model)

I motivi sono molteplici e strategici:
*   **Trovare bug di sicurezza in anticipo**: È molto più economico e semplice risolvere problemi di sicurezza nella fase di progettazione che dopo lo sviluppo o la distribuzione.
*   **Comprendere i requisiti di sicurezza**: Aiuta a definire chiaramente cosa deve essere protetto e come.
*   **Ingegnerizzare e consegnare prodotti migliori**: Integra la sicurezza nel DNA del prodotto, non come un ripensamento.
*   **Affrontare problemi che altre tecniche non individuano**: Tecniche come test di penetrazione o scansioni automatizzate trovano problemi in ciò che *è stato costruito*. Il Threat Modeling aiuta a identificare problemi nel *disegno* stesso del sistema (vulnerabilità architetturali).

---

## 3. Concetti Fondamentali e Modello STRIDE

Il cuore del Threat Modeling si basa su alcune domande chiave:
1.  **Cosa stai costruendo?** (Definire il sistema)
2.  **Cosa può andare storto una volta costruito?** (Identificare le minacce)
3.  **Cosa dovresti fare riguardo a quelle cose che possono andare storte?** (Definire le mitigazioni)
4.  **Hai fatto un'analisi decente?** (Validare il modello)

Per identificare sistematicamente "cosa può andare storto", si utilizza spesso il modello **STRIDE**, sviluppato da Microsoft. STRIDE è un acronimo che categorizza i tipi di minacce in base alla proprietà di sicurezza che violano:

| Minaccia (Threat) | Proprietà Violata | Vittime Tipiche |
| :--- | :--- | :--- |
| **S**poofing (Spoofing) | Autenticazione | Processi, Entità Esterne, Persone |
| **T**ampering (Manomissione) | Integrità | Processi, Archivi Dati, Flussi Dati |
| **R**epudiation (Ripudio) | Non-Ripudio | Processi |
| **I**nformation Disclosure (Divulgazione) | Riservatezza | Processi, Archivi Dati, Flussi Dati |
| **D**enial of Service (Diniego) | Disponibilità | Processi, Archivi Dati, Flussi Dati |
| **E**levation of Privilege (Escalation) | Autorizzazione | Processi |

Ogni categoria di STRIDE viene poi analizzata in profondità con esempi concreti (es: come avviene lo spoofing di un file? Come si può manomettere un pacchetto di rete?) e vengono proposte strategie e tecniche di mitigazione specifiche.

---

## 4. Il Processo di Threat Modeling

Il processo viene descritto in diversi modi, ma segue un flusso logico comune:

### A. Modellare il Sistema
Si inizia creando una **rappresentazione grafica** del sistema. Gli strumenti preferiti sono:
*   **Diagrammi di Flusso Dati (DFD)**: Mostrano come i dati si muovono tra processi, archivi di dati ed entità esterne. Sono molto efficaci per il threat modeling.
*   **Diagrammi UML**.
*   **Diagrammi a Corsie (Swin Lane)**.
*   **Diagrammi di Stato**.

### B. Identificare i Confini di Fiducia (Trust Boundaries)
I **Trust Boundaries** sono linee immaginarie che separano aree del sistema con **diversi livelli di privilegio o fiducia**. Sono punti critici dove è più probabile che si verifichino attacchi (es: il confine tra l'utente su Internet e il server web; tra un'applicazione utente e il kernel del sistema operativo). Per identificarli, ci si chiede: "Tutto nel sistema ha lo stesso livello di accesso? Tutto ciò con cui il software comunica è dentro lo stesso confine?" Se la risposta è "no", c'è un confine di fiducia.

### C. Identificare le Minacce
Utilizzando il modello STRIDE, si analizza ogni elemento del diagramma (processi, flussi dati, archivi) chiedendosi: "Come potrebbe essere attaccato per Spoofing, Tampering, ecc.?".

### D. Classificare e Prioritizzare le Minacce
Non tutte le minacce hanno la stessa probabilità o impatto. Vengono utilizzati modelli per **quantificare il rischio**.
*   **Modello DREAD**: Assegna un punteggio (Alto=3, Medio=2, Basso=1) a cinque fattori:
    *   **D**amage Potential (Danno Potenziale)
    *   **R**eproducibility (Riproducibilità)
    *   **E**xploitability (Sfruttabilità)
    *   **A**ffected Users (Utenti Coinvolti)
    *   **D**iscoverability (Scopribilità)
    La somma dei punteggi dà una priorità di rischio.

### E. Definire le Mitigazioni
Per ogni minaccia identificata e prioritaria, si definiscono contromisure. Le opzioni sono:
*   **Eliminare la minaccia**: Ridesignando la funzionalità.
*   **Mitigare la minaccia**: Implementando controlli di sicurezza (es: crittografia, autenticazione, logging).
*   **Trasferire il rischio**: Ad esempio, tramite assicurazioni.
*   **Accettare il rischio**: Se il costo della mitigazione supera il potenziale danno.

---

## 5. Approcci e Metodologie

La lezione descrive due approcci principali:

*   **Approccio Centrato sulla Sicurezza (Security-Centric)**: Si concentra sull'analisi tecnica delle proprietà del software (usando STRIDE e DFD). Evita di elencare profili di attaccanti specifici per non cadere nel bias "nessuno lo farebbe mai".
*   **Approccio Basato sul Rischio (Risk-Based)**: Si concentra sugli **asset** da proteggere (dati, reputazione) e sugli **attaccanti** per meglio prioritizzare gli sforzi. Una metodologia strutturata in questo ambito è **PASTA** (Process for Attack Simulation and Threat Analysis), un framework in sette fasi che va dalla definizione degli obiettivi di business all'analisi di rischio e impatto, passando per la scomposizione tecnica, l'analisi delle minacce e la modellazione degli attacchi.

---

## 6. Asset e Agenti di Minaccia

*   **Cosa Proteggere (Assets)**:
    *   **Cose che gli attaccanti vogliono**: Password, numeri di carte di credito, dati aziendali riservati.
    *   **Asset intangibili**: Reputazione, buona volontà del marchio.
    *   **Pietre di Inciampo (Stepping Stones)**: Qualsiasi cosa (come un server compromesso) che possa essere usata per attaccare altri asset più preziosi.

*   **Agenti di Minaccia (Threat Agents)**: Chi o cosa potrebbe causare un danno. Possono essere:
    *   **Umani**: Hacktivisti, cybercriminali, spie.
    *   **Strumenti**: Malware, keylogger.
    *   **Non-umani**: Disastri naturali (tempeste, terremoti).

---

## 7. Strumenti e Risorse

*   **Librerie di Attacchi**: Per andare oltre le astrazioni di STRIDE e trovare tecniche d'attacco concrete.
    *   **CAPEC** (MITRE): Cataloga schemi di attacco comuni.
    *   **ATT&CK** (MITRE): Conoscenza basata su tattiche e tecniche di avversari reali.
    *   **OWASP Cheat Sheet Series**: Linee guida concise su specifici temi di sicurezza.

*   **Software per il Threat Modeling**:
    *   **Microsoft SDL Threat Modeling Tool** (gratuito).
    *   **OWASP Threat Dragon** (open-source).
    *   **IriusRisk, ThreatModeler** (commerciali con edizioni community).
    *   **CAIRIS, Threagile** (open-source).

*   **Alberi di Attacco (Attack Trees)**: Strumento grafico per scomporre un obiettivo di attacco (es: "Rubare dati dal database") in sotto-obiettivi sempre più specifici (es: "accedere al server", "bypassare l'autenticazione"), mostrando i percorsi logici che un attaccante potrebbe seguire.

---

## 8. Integrazione nel Ciclo di Vita dello Sviluppo (SDL)

Il Threat Modeling è una pratica cardine del **Security Development Lifecycle (SDL)** di Microsoft, un processo che integra la sicurezza in ogni fase dello sviluppo software, dalla formazione e definizione dei requisiti, attraverso la progettazione, implementazione, verifica (con SAST, DAST, Penetration Test), fino al rilascio e alla risposta agli incidenti.

---

## 9. Validazione e Best Practices

Il modello di minaccia creato deve essere **validato**:
*   **Completezza**: Copre tutto il sistema?
*   **Accuratezza**: Rappresenta correttamente il sistema?
*   **Copertura**: Include tutte le decisioni di sicurezza?
Il diagramma dovrebbe focalizzarsi sui **flussi di dati** (non sul controllo), evitare termini vaghi ("a volte"), non avere "pozzi di dati" (mostrare chi li usa) e mostrare esplicitamente i processi che spostano i dati.

---

## Domande da Esame

1.  **Definisci il Threat Modeling e spiega perché è considerato un processo "strategico" e "proattivo" nella sicurezza del software.**
2.  **Elenca e descrivi brevemente i quattro obiettivi principali del Threat Modeling come presentati nella lezione.**
3.  **Spiega l'acronimo STRIDE. Per ognuna delle sei categorie, indica la proprietà di sicurezza violata e fornisci un esempio concreto di minaccia.**
4.  **Descrivi le quattro domande chiave che guidano il processo di Threat Modeling.**
5.  **Cosa sono i "Trust Boundaries" (Confini di Fiducia)? Perché sono punti critici nell'analisi delle minacce? Fai un esempio in un'architettura web tipica.**
6.  **Spiega il modello DREAD per la classificazione del rischio. Quali sono i suoi cinque fattori e come vengono utilizzati per prioritizzare le minacce?**
7.  **Qual è la differenza principale tra l'approccio "Security-Centric" e l'approccio "Risk-Based" al Threat Modeling?**
8.  **Cosa si intende per "mitigazione" di una minaccia? Elenca le quattro possibili strategie generali per affrontare una minaccia identificata.**
9.  **Qual è il ruolo dei Diagrammi di Flusso Dati (DFD) nel Threat Modeling? Che tipo di elementi contengono tipicamente?**
10. **Fai due esempi di "asset" che un'organizzazione dovrebbe proteggere, distinguendo tra asset tangibili e intangibili. Cosa si intende per "stepping stone" (pietra d'inciampo)?**
11. **Descrivi lo scopo e l'utilità delle librerie di attacchi come CAPEC e ATT&CK nel contesto del Threat Modeling.**
12. **Come si integra il Threat Modeling all'interno di un framework più ampio come il Security Development Lifecycle (SDL)? Menziona almeno due pratiche SDL collegate al Threat Modeling.**
