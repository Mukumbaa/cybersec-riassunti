
# Lezione su Cybersecurity Management

Questa lezione affronta il tema della **gestione della sicurezza informatica (Cybersecurity Management)** dal punto di vista organizzativo e strategico, sottolineando che la sicurezza non è solo un problema tecnico, ma anche, e soprattutto, un **problema gestionale e di governance**.

---

## 1. La Sicurezza come Problema Organizzativo

La premessa fondamentale è che la sicurezza informatica non riguarda solo firewall, antivirus e patch. Per essere efficace, deve essere integrata in una **visione d'insieme dell'organizzazione** che coinvolge:

*   **Identificazione degli Asset**: Cosa dobbiamo proteggere? (Dati, sistemi, reputazione, continuità operativa).
*   **Valutazione delle Minacce e dei Rischi**: Da cosa dobbiamo proteggerci? Con quale probabilità e con quale impatto potenziale?
*   **Strategie di Difesa**: Queste devono essere pianificate in modo **proporzionale** al valore degli asset e al rischio reale. Non ha senso spendere un milione per proteggere un asset che ne vale diecimila.
*   **Piani di Ripresa (Rescue/Recovery)**: Poiché nessuna difesa è perfetta, è essenziale avere piani per **ripristinare le operazioni** dopo un attacco riuscito.

---

## 2. Il Piano di Sicurezza Informatica

Il documento centrale della gestione della sicurezza è il **Piano di Sicurezza Informatica**. Non è un manuale tecnico, ma un **documento strategico** che deve contenere:

1.  **Policy (Politica)**: L'espressione formale della **volontà e degli obiettivi** dell'organizzazione in materia di sicurezza.
2.  **Stato Attuale**: Una fotografia dello stato della sicurezza al momento della stesura del piano.
3.  **Requisiti (Requirements)**: Raccomandazioni concrete su come raggiungere gli obiettivi di sicurezza. Devono essere **corretti, consistenti, completi, realistici, necessari, verificabili e tracciabili**.
4.  **Controlli Raccomandati**: La mappatura dei controlli di sicurezza (tecnici, procedurali, fisici) alle vulnerabilità identificate.
5.  **Accountability (Responsabilità)**: Documentazione chiara su **chi è responsabile** per ogni attività di sicurezza. Assegna ruoli.
6.  **Cronogramma (Timetable)**: Definisce **quando** devono essere svolte le diverse funzioni di sicurezza.
7.  **Manutenzione**: Specifica una struttura per l'**aggiornamento periodico** del piano stesso. La sicurezza non è statica.

---

## 3. La Politica di Sicurezza (Security Policy)

La **Policy** è la dichiarazione di alto livello che dà il via a tutto. Risponde a tre domande fondamentali:
1.  **Chi** dovrebbe avere accesso?
2.  **A quali risorse** (sistemi e organizzative) dovrebbe essere consentito l'accesso?
3.  **Quali tipi di accesso** dovrebbero essere consentiti a ciascun utente per ciascuna risorsa?

La policy deve specificare chiaramente:
*   Gli **obiettivi di sicurezza** dell'organizzazione.
*   **Dove risiede la responsabilità** per la sicurezza.
*   L'**impegno formale** dell'organizzazione verso la sicurezza.

---

## 4. Responsabilità e Ruoli (Accountability)

La sicurezza è responsabilità di tutti, ma con ruoli distinti. Il piano deve identificare chi fa cosa. Ruoli comuni includono:
*   **Utenti**: Responsabili della sicurezza dei propri dispositivi.
*   **Responsabili di Progetto (Project Leaders)**: Responsabili della sicurezza di dati e calcoli del loro progetto.
*   **Manager**: Responsabili di assicurarsi che il personale che supervisionano implementi le misure di sicurezza.
*   **Amministratori di Database (DBA)**: Responsabili dell'accesso e dell'integrità dei dati.
*   **Responsabili dell'Informazione (Information Officers)**: Sovrintendono alla creazione, uso, conservazione e smaltimento dei dati.
*   **Personale dell'Ufficio Personale (HR)**: Responsabile della sicurezza legata ai dipendenti (es. onboarding/offboarding degli account).

---

## 5. Garantire l'Impegno (Assuring Commitment)

Un piano perfetto fallisce se le persone non lo adottano. Per avere successo, tre gruppi devono essere coinvolti e impegnati:
1.  **Il Team di Pianificazione**: Deve essere sensibile alle esigenze di tutti i reparti coinvolti.
2.  **Gli Utenti e i Reparti Coinvolti**: Devono **comprendere** cosa significa il piano per le loro attività quotidiane e come le loro azioni influenzano la sicurezza altrui.
3.  **Il Management (Direzione)**: Deve dimostrare un **impegno chiaro** nell'usare e far rispettare gli aspetti di sicurezza. Senza il supporto attivo della direzione, qualsiasi iniziativa è destinata a fallire.

---

## 6. Continuità Operativa e Ripresa da Disastro (BCP/DR)

Poiché gli incidenti gravi possono accadere, servono piani specifici per gestire la crisi.

*   **Business Continuity Plan (BCP - Piano di Continuità Operativa)**: Documenta come l'azienda **continuerà a funzionare** durante o dopo un grave incidente di sicurezza. Si occupa di situazioni **catastrofiche** (es. perdita totale di un data center) e di **lunga durata**. Le attività includono:
    *   Valutare l'**impatto** di una crisi sul business.
    *   Sviluppare una **strategia** per controllare l'impatto e proteggere gli asset chiave.
    *   Implementare un **piano** con ruoli chiari (chi comanda, cosa fare).
    *   Spesso segue standard come la **ISO 22301**, che applica il ciclo **Plan-Do-Check-Act (PDCA)**.

*   **Disaster Recovery Plan (DRP - Piano di Ripristino)**: Parte del BCP, si concentra più tecnicamente sul **ripristino di sistemi IT, dati e infrastrutture** dopo un disastro.

---

## 7. Risposta agli Incidenti (Incident Response)

Mentre il BCP guarda al "dopo", il piano di risposta agli incidenti gestisce il "durante".

*   **Security Incident Response Plan**: Dice al personale **come affrontare un incidente di sicurezza** in corso. L'obiettivo immediato è **contenere, eradicare e recuperare**, non la continuità aziendale a lungo termine.
*   **Computer Security Incident Response Team (CSIRT)**: Il team dedicato alla risposta. I suoi ruoli chiave sono:
    *   **Reporting**: Ricevere e inoltrare segnalazioni.
    *   **Rilevamento (Detection)**: Investigare per confermare l'incidente.
    *   **Triaging**: Agire immediatamente sui bisogni urgenti.
    *   **Risposta (Response)**: Coordinare gli sforzi di contenimento ed eradicazione.
    *   **Post-Mortem**: Analizzare l'incidente concluso per imparare e migliorare.
    *   **Educazione**: Diffondere lezioni apprese e consigliare sulle buone pratiche.
*   **CSIRT Nazionale**: Viene citato l'**Italian CSIRT**, operante all'interno dell'Agenzia per la Cybersicurezza Nazionale (ACN), nato dall'esperienza del CERT nazionale e del CERT-PA, con il compito di coordinare la risposta agli incidenti di livello nazionale.

---

## 8. Trasferimento del Rischio: la Cyber Assicurazione

Poiché i costi di un grave attacco informatico (danni a terzi, interruzione operativa, costi di recupero, multe normative, cause legali) possono essere proibitivi, le organizzazioni possono **trasferire parte del rischio finanziario** attraverso la **Cyber Insurance**.

*   **Cosa copre**: Può coprire una vasta gamma di costi conseguenti a un attacco (es. risarcimenti a clienti, spese di notifica per data breach, sanzioni regolatorie, costi legali).
*   **Mercato in crescita**: I dati mostrano un **mercato globale ed europeo in forte crescita** (in termini di premi assicurativi).
*   **Sottoscrizione (Underwriting)**: Le compagnie valutano il rischio prima di assicurare, considerando:
    *   Il **tipo di industria** (un ospedale è più a rischio di un negozio di candele).
    *   Il **profilo di sicurezza** dell'organizzazione, valutato tramite questionari sulla preparedness.
    *   È un business emergente, quindi **modelli statistici e dati storici sono ancora limitati**, rendendo la valutazione del rischio complessa.

---

## Domande da Esame

1.  **Perché la lezione sostiene che la sicurezza informatica è "non solo un problema tecnico, ma anche organizzativo"? Fai due esempi di aspetti organizzativi critici.**
2.  **Elenca e descrivi brevemente i sette contenuti fondamentali di un Piano di Sicurezza Informatica (Cybersecurity Plan).**
3.  **Cosa si intende per "Security Policy" (Politica di Sicurezza)? Quali sono le tre domande fondamentali a cui deve rispondere?**
4.  **Definisci il concetto di "Accountability" nel contesto della gestione della sicurezza. Fai tre esempi di ruoli specifici all'interno di un'organizzazione e delle loro responsabilità di sicurezza.**
5.  **Quali sono i tre gruppi di persone il cui impegno è essenziale per il successo di un piano di sicurezza? Per ciascuno, spiega quale deve essere il loro contributo.**
6.  **Spiega la differenza principale tra un *Business Continuity Plan (BCP)* e un *Security Incident Response Plan*. A quali scenari rispondono rispettivamente?**
7.  **Descrivi le principali responsabilità di un Computer Security Incident Response Team (CSIRT). Quali sono le fasi del suo intervento, dalla segnalazione alla chiusura dell'incidente?**
8.  **Cosa si intende per "Cyber Insurance" (Assicurazione Informatica)? Perché le organizzazioni la considerano uno strumento di gestione del rischio? Elenca due tipologie di costi che una polizza potrebbe coprire.**
9.  **In base a quali fattori una compagnia assicurativa valuta il rischio di un'organizzazione prima di sottoscrivere una polizza di cyber insurance? Perché questo mercato è considerato "emergente"?**
10. **Cita l'esempio del CSIRT italiano. All'interno di quale struttura nazionale opera e da quali precedenti esperienze è nato?**
