
Questa lezione è un viaggio approfondito nel mondo delle vulnerabilità del software, dei metodi per classificarle, misurarne la pericolosità e, infine, dei principi per sviluppare software sicuro (Secure Software Development). È un tema centrale, dato che la maggior parte degli attacchi informatici sfrutta proprio errori nel software.

### **Parte 1: Classificazione delle Debolezze del Software (CWE) e Vulnerabilità (CVE)**

La lezione inizia presentando i framework standard del settore per parlare in modo strutturato dei problemi del software.

*   **CWE (Common Weakness Enumeration)**: Non è un elenco di vulnerabilità specifiche, ma una **tassonomia delle debolezze** intrinseche che possono esistere nel software (e anche nell'hardware). Una debolezza è una condizione che, in certe circostanze, può contribuire a una vulnerabilità. Il CWE è organizzato gerarchicamente (come un albero) e categorizza problemi in aree come: errori di validazione dell'input, problemi di buffer, errori di crittografia, problemi di controllo degli accessi, errori di concorrenza, e così via. La versione corrente elenca **944 debolezze**.
    *   **CWE Top 25**: Una classifica delle 25 debolezze più pericolose e diffuse. In cima troviamo le grandi classiche degli attacchi web: **Cross-site Scripting (XSS - CWE-79)**, **SQL Injection (CWE-89)**, **Cross-Site Request Forgery (CSRF - CWE-352)**. Ma compaiono anche problemi di basso livello come **Buffer Overflow (CWE-787, CWE-120)** e **Use-After-Free (CWE-416)**.

*   **CVE (Common Vulnerabilities and Exposures)**: Questo è il sistema pratico per identificare **vulnerabilità specifiche** in prodotti software reali. Un **CVE ID** (es. CVE-2021-1675) identifica univocamente una vulnerabilità pubblicamente nota in una specifica versione di un prodotto. Il programma CVE ha lo scopo di catalogare queste vulnerabilità. Una vulnerabilità è definita come un'istanza di una o più debolezze (CWE) che può essere sfruttata, causando un impatto negativo sulla riservatezza, integrità o disponibilità.

*   **NVD (National Vulnerability Database)**: Gestito dal NIST, è il database americano che arricchisce i record CVE con informazioni aggiuntive come score di severità, riferimenti a patch e impatto.

*   **Root Cause Mapping**: È il processo cruciale di collegare una **CVE** (la vulnerabilità specifica) alla **CWE** sottostante (la debolezza di progettazione/codice che l'ha causata). Questo permette di capire non solo "che cosa è rotto", ma "perché si è rotto", guidando investimenti per correggere le pratiche di sviluppo alla radice (es. formare gli sviluppatori a evitare quella specifica CWE).

### **Parte 2: Valutazione della Gravità e della Probabilità di Sfruttamento**

Avere migliaia di CVE rende necessario stabilire priorità. La lezione presenta strumenti per farlo:

*   **CVSS (Common Vulnerability Scoring System)**: È uno standard per assegnare un **punteggio numerico (da 0 a 10)** a una vulnerabilità, basato su caratteristiche come la facilità di sfruttamento, l'impatto e se richiede privilegi pregressi. Il punteggio viene poi tradotto in un livello qualitativo (Basso, Medio, Alto, Critico). Il **vettore CVSS** (es. CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H) è una stringa compatta che riassume queste metriche.

*   **KEV (Known Exploited Vulnerabilities) Catalog**: Mantenuto dalla CISA americana, è un catalogo **autoritativo** delle vulnerabilità per le quali esiste una prova certa di sfruttamento attivo "in the wild". Patchare queste vulnerabilità è la massima priorità assoluta. La lezione mostra la **Top 10 delle CWE più sfruttate nel 2024**, dove dominano problemi come **Out-of-bounds Write (CWE-787)**, **OS Command Injection (CWE-78)** e **Use After Free (CWE-416)**.

*   **EPSS (Exploit Prediction Scoring System)**: Questo è un modello **predittivo** e probabilistico. Mentre il CVSS valuta la gravità "potenziale" e il KEV conferma lo sfruttamento "attuale", l'EPSS stima **la probabilità (da 0% a 100%) che una data vulnerabilità venga sfruttata nei prossimi 30 giorni**. Aiuta a prendere decisioni basate sul rischio reale quando le risorse per patchare sono limitate.

### **Parte 3: La Ricerca delle Vulnerabilità e l'Obfuscazione**

Trovare vulnerabilità è difficile perché:
1.  **Qualsiasi programma può contenere debolezze**, derivanti dal linguaggio, da input inaspettati o da errori logici.
2.  **La malizia dipende dal contesto**: Un input non è di per sé malizioso; lo diventa in base a come viene interpretato e processato dal programma.
3.  **Ambiguità fra dati e istruzioni**: Nei flussi di byte (come input di rete o file), non è sempre chiaro dove finiscono i "dati" e dove iniziano le "istruzioni" eseguibili. Questa confusione è alla base di molti attacchi di injection.

Un esempio pratico di questa difficoltà è l'**Obfuscazione del codice**. Gli attaccanti (o il malware) nascondono il loro intento modificando il codice (sorgente o binario) senza cambiarne la semantica, rendendolo illeggibile per analisti umani o tool automatici. La lezione mostra tecniche come:
*   **Concatenazione e Riorganizzazione** di stringhe.
*   **Uso di variabili intermedie** e di **caratteri maiuscoli/minuscoli** insoliti.
*   **Codifica (es. Base64)** e **Compressione** di parti del codice.
*   **Uso di funzioni di valutazione dinamica** (come `eval`) che costruiscono ed eseguono codice al volo.

L'obiettivo è creare "un programma che costruisce un programma che costruisce un programma...", mascherando l'attività malevola finale (es. scaricare ed eseguire malware).

### **Parte 4: Vulnerabilità di Gestione della Memoria (Buffer Overflow e Derivati)**

Questo è il cuore storico della sicurezza del software. I linguaggi come **C e C++** danno al programmatore un controllo potente ma pericoloso sulla memoria, senza protezioni automatiche.

*   **Vulnerabilità Spaziali**: Si accede a memoria al di fuori dei limiti di un buffer allocato. L'esempio archetipico è il **Buffer Overflow**.
*   **Vulnerabilità Temporali**: Si accede a memoria che è stata già liberata (deallocata). L'esempio tipico è il **Use-After-Free** (dereferenziare un puntatore "dangling").

Un **Buffer Overflow** si verifica quando un programma tenta di memorizzare più dati in un buffer (es. un array) di quanto sia stato allocato, sovrascrivendo le locazioni di memoria adiacenti. Queste locazioni possono contenere:
*   **Altre variabili del programma** (attacco "data-only").
*   **Dati di controllo del flusso**, come l'**indirizzo di ritorno** di una funzione sullo stack (attacco "control-flow hijack"). Sovrascrivendo questo indirizzo, si può dirottare l'esecuzione verso codice scelto dall'attaccante (**shellcode**).
*   **Puntatori a funzione** (attacco "code pointer corruption").

La lezione ripercorre la **storia** di questi attacchi, dal worm Morris (1988) fino a worm famosi come Code Red (2001) e Sasser (2004).

### **Parte 5: Altre Categorie Critiche di Attacchi**

*   **Attacchi di Injection**: Sono la classe più diffusa (vedi CWE Top 25). Si verificano quando **input non validati o non sanificati vengono interpretati come parte di un comando o di una query**. I tipi principali sono:
    *   **SQL Injection**: L'input utente modifica la query SQL al database.
    *   **OS Command Injection**: L'input utente viene eseguito come comando di sistema operativo.
    *   **Cross-Site Scripting (XSS)**: L'input utente (JavaScript) viene inserito in una pagina web e eseguito nel browser di altre vittime.
*   **Race Conditions**: Si verificano in codice concorrente (multi-thread) quando l'esito corretto dipende dalla sequenza temporale di accessi a risorse condivise. Una sincronizzazione errata può portare a corruzione di dati o a **deadlock**.
*   **Vulnerabilità di Canali Laterali (Side Channel)**: Non attaccano la logica del programma, ma sfruttano **informazioni fisiche** indirette rilasciate durante l'esecuzione (es. tempo di esecuzione, consumo di energia, emissioni elettromagnetiche, uso della cache) per dedurre informazioni segrete (es. chiavi crittografiche).

### **Parte 6: Principi di Programmazione Difensiva e Sviluppo Sicuro**

La seconda metà della lezione si sposta sulla **prevenzione**: come scrivere codice più sicuro.

*   **Programmazione Difensiva (Defensive Programming)**: Filosofia per cui il software deve essere progettato per **continuare a funzionare correttamente anche in presenza di input inattesi o di attacchi**. La regola d'oro è **non assumere mai nulla**. Bisogna validare tutti gli input, gestire tutti gli stati d'errore possibili e non fidarsi dell'ambiente.
*   **Scrittura di Codice Sicuro**:
    1.  **Implementazione Corretta dell'Algoritmo**: L'algoritmo deve gestire tutti i casi. Attenzione al **codice di debug** lasciato per sbaglio in produzione, che può diventare una backdoor.
    2.  **Corrispondenza fra Codice Sorgente e Linguaggio Macchina**: In ambienti ad altissima sicurezza, si verifica che il compilatore abbia generato le istruzioni corrette. È un processo complesso.
    3.  **Interpretazione Corretta dei Dati**: I linguaggi **fortemente tipati** (es. Java, Rust) sono più sicuri perché impediscono interpretazioni ambigue dei bit in memoria. Linguaggi più liberi (es. C) richiedono più attenzione.
    4.  **Uso Corretto della Memoria**: Preferire linguaggi con **gestione automatica della memoria (Garbage Collection)** o, meglio ancora, con **ownership model** (come **Rust**) che elimina a compile-time i problemi di use-after-free e buffer overflow senza penalizzare le prestazioni.
    5.  **Interazione con il Sistema Operativo**: Applicare il **principio del minimo privilegio**. Un programma dovrebbe essere eseguito solo con i privilegi strettamente necessari alla sua funzione, per limitare i danni in caso di compromissione (**Privilege Escalation**).

### **Parte 7: Contromisure e Strategie di Difesa**

La lezione conclude con una tabella riassuntiva delle strategie per affrontare le varie categorie di vulnerabilità:

*   **Prevenzione (Prevention)**:
    *   Usare **linguaggi memory-safe** (Rust, Go, Java, Python).
    *   Usare **API sicure** e **prepared statements** per le query SQL.
    *   Adottare **linee guida di coding** e **code review**.
*   **Rilevamento (Detection)**:
    *   **Analisi Statica (SAST)**: Analizza il codice sorgente senza eseguirlo.
    *   **Analisi Dinamica (DAST)**: Testa il programma in esecuzione.
    *   **Fuzzing**: Tecnica di testing automatizzato che invia input casuali o semi-casuali al programma per trovare crash o comportamenti anomali (nato nel 1989).
*   **Mitigazione (Mitigation)** (quando la vulnerabilità esiste nel codice in esecuzione):
    *   **Canary (Stack Protector)**: Valori casuali sullo stack per rilevare overflow.
    *   **ASLR (Address Space Layout Randomization)**: Randomizza gli indirizzi di memoria, rendendo difficile per un attaccante sapere dove dirottare l'esecuzione.
    *   **DEP/NX (Data Execution Prevention)**: Impedisce l'esecuzione di codice in aree di memoria dedicate ai dati (es. stack).
    *   **Sandboxing/Isolamento**: Eseguire il programma in un ambiente confinato con accessi limitati.
    *   **Compartmentalizzazione**: Suddividere il programma in parti con privilegi differenziati.

---

### **Domande da Esame Possibili:**

1.  **Tassonomia e Classificazione:** Spiega la differenza fondamentale tra **CWE** e **CVE**. Perché è importante effettuare il **Root Cause Mapping** tra i due? Cita tre esempi di CWE dalla Top 25 e descrivi brevemente il tipo di attacco che abilitano.
2.  **Prioritizzazione del Rischio:** Descrivi lo scopo e la differenza tra **CVSS**, **KEV Catalog**, e **EPSS**. Se dovessi gestire la patch di 100 vulnerabilità in un sistema critico, in che ordine di priorità assoluta metteresti: a) Una vulnerabilità con CVSS 9.8 ma EPSS 2%, b) Una vulnerabilità con CVSS 7.5 ma presente nel KEV Catalog, c) Una vulnerabilità con CVSS 8.5 e EPSS 85%?
3.  **Vulnerabilità di Memoria:** Cosa sono le vulnerabilità **spaziali** e **temporali** nella gestione della memoria? Fai un esempio concreto per ciascuna categoria (es. Buffer Overflow, Use-After-Free). Perché linguaggi come C e C++ sono particolarmente soggetti a questi problemi?
4.  **Attacchi di Injection e Validazione Input:** Descrivi in cosa consistono gli attacchi di **SQL Injection** e **OS Command Injection**. Qual è il principio fondamentale della **programmazione difensiva** per prevenirli? Cita una tecnica di testing automatizzato (menzionata nella lezione) utile per trovare vulnerabilità legate a input non gestiti.
5.  **Sviluppo Sicuro e Contromisure:** Elenca almeno tre **principi di sviluppo software sicuro** discussi nella lezione (es. Principio del Minimo Privilegio). Perché l'uso di un linguaggio **memory-safe** come Rust è considerato una contromisure così efficace? Cosa si intende per **ASLR** e come aiuta a mitigare gli attacchi di buffer overflow?
6.  **Analisi e Offuscamento:** Perché è difficile rilevare le vulnerabilità? Spiega il concetto di **obfuscazione del codice** e a quale scopo viene utilizzata (dai due punti di vista: attaccante e difensore).
