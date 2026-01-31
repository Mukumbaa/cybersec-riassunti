
Certamente. Questa lezione è un'immersione completa nel mondo dell'**Autenticazione** e del **Controllo degli Accessi**, due pilastri fondamentali della sicurezza informatica. Attraverseremo i principi, i meccanismi, le vulnerabilità e le best practice, seguendo anche le linee guida più aggiornate come quelle del NIST.

### **Parte 1: Concetti Fondamentali e Quadro di Riferimento**

La lezione si apre citando le **Linee Guida per l'Identità Digitale del NIST (SP 800-63-4)**, aggiornate a luglio 2025. Questo documento è la bibbia in materia e stabilisce standard per metodi di autenticazione moderni come portafogli digitali, passkey e documenti di identità fisici.

Vengono definiti due processi chiave:
1.  **Identity Proofing (Verifica dell'Identità)**: Il processo iniziale in cui un'organizzazione verifica che un individuo sia chi dice di essere, tipicamente prima di rilasciargli un account (esempio: registrazione con documento d'identità).
2.  **Enrollment (Registrazione)**: La fase in cui l'identità verificata viene legata a uno o più **autenticatori** (es. password, impronta digitale, token).

L'**Autenticazione** è definita come il processo che permette a una **Relying Party** (la parte che fornisce il servizio) di fidarsi che un **Claimant** (l'utente che afferma un'identità) sia effettivamente il **Subscriber** (l'utente registrato). Un'autenticazione di successo dimostra che il claimant possiede e controlla uno o più autenticatori validi legati alla sua identità. Questo avviene tramite un **protocollo di autenticazione** tra il claimant e il **Verifier** (il sistema che verifica le credenziali).

Vengono presentati due modelli architetturali:
*   **Modello Non Federato**: L'utente ha credenziali separate per ogni servizio (es. password diversa per ogni sito).
*   **Modello Federato**: L'utente si autentica una volta con un **Identity Provider (IdP)** fidato (es. Google, Microsoft, l'Università), che poi fornisce un "assertion" di sicurezza al **Service Provider (SP)**. Questo abilita il **Single Sign-On (SSO)**. Una variante avanzata è il modello con **portafoglio controllato dall'utente**, dove l'utente gestisce direttamente le proprie credenziali e attributi verificati nel suo dispositivo (wallet), rilasciandoli ai service provider quando necessario, aumentando privacy e controllo.

Si distingue chiaramente tra:
*   **Autenticazione**: *"Chi sei?"* (Verifica dell'identità).
*   **Autorizzazione**: *"Cosa puoi fare?"* (Verifica dei privilegi sulle risorse), tipicamente gestita tramite una **matrice di accesso**.

### **Parte 2: Meccanismi di Autenticazione e Fattori**

I meccanismi di autenticazione si basano su tre (o più) **fattori**:
1.  **Qualcosa che SAI (Knowledge)**: Segreti come password, PIN, domande di sicurezza.
2.  **Qualcosa che HAI (Possession)**: Oggetti fisici come carte, chiavi, token hardware o software (app di autenticazione).
3.  **Qualcosa che SEI (Inherence)**: Caratteristiche biometriche (impronte digitali, volto, iride).

La lezione classifica i tipi di segreti in modo dettagliato, dai semplici **Password** e **Look-up Secret** (segreti monouso emessi dal verifier), fino a:
*   **Single/Multi-Factor OTP (One-Time Password)**: Codici monouso generati da un dispositivo/app. Il multi-fattore richiede l'attivazione da parte di un secondo fattore (es. impronta per sbloccare l'app che genera l'OTP).
*   **Autenticazione Crittografica**: Dimostra il possesso di una chiave crittografica. Può essere a singolo fattore (solo chiave) o multi-fattore (chiave attivata da un secondo fattore, come un PIN per accedere al keystore).

L'**Autenticazione Multi-Fattore (MFA)** combina due o più fattori distinti (es. carta + PIN, password + OTP), mitigando drasticamente il rischio che un singolo fattore venga compromesso.

### **Parte 3: Attacchi ai Sistemi di Autenticazione**

La lezione fornisce una tassonomia dettagliata degli attacchi, classificati per tipo di attacco e fattore bersaglio, con esempi e mitigazioni:
*   **Attacchi Lato Client (Client Attack)**: Forza bruta su password, ricerca esaustiva su token, falsi positivi biometrici. *Mitigazione*: Complessità delle credenziali, limitazione tentativi, rilevamento della "vitalità" (liveness) per le biometrie.
*   **Attacchi Lato Host (Host Attack)**: Furto del database delle password o dei template biometrici. *Mitigazione*: Crittografia forte (hashing con sale), protezione fisica dei dispositivi di acquisizione.
*   **Intercettazione, Furto, Copia (Eavesdropping, Theft, Copy)**: Shoulder surfing, keylogger, clonazione di token, falsi tratti biometrici. *Mitigazione*: Formazione utente, token resistenti alla manomissione, MFA.
*   **Replay**: Riuso di una credenziale intercettata. *Mitigazione*: Protocolli challenge-response, OTP.
*   **Cavallo di Troia (Trojan Horse)**: Client o dispositivi di acquisizione malevoli. *Mitigazione*: Trusted Locations/Devices.
*   **Denial of Service (DoS)**: Blocco dell'account per troppi tentativi falliti. *Mitigazione*: MFA con dispositivi fisici (meno soggetti a blocco automatico).

Viene citato il **DBIR 2024 di Verizon**, che evidenzia come gli **account validi** (compromessi tramite phishing, credenziali rubate, ecc.) siano il vettore di attacco più comune per le violazioni dati.

### **Parte 4: Il Problema delle Password e le Best Practice**

Un'ampia sezione è dedicata alla **gestione delle password**, punto debole storico.
*   **Debolezze delle Password**: La maggior parte degli utenti sceglie password deboli e prevedibili (es. "123456", "password"). Gli attacchi comuni sono **Dictionary Attack** e **Brute Force**. Strumenti come **John the Ripper** e **Hashcat** automatizzano questi attacchi. Siti come **Hashes.com** archiviano enormi database di hash rubati con le password in chiaro già crackate.
*   **Memorizzazione Sicura (Secure Password Storage)**: Viene presentato un studio scioccante: molti sviluppatori freelance scelgono metodi insicuri per memorizzare le password (testo in chiaro, Base64 - che non è cifratura!, hash obsoleti come MD5). Le best practice prevedono l'uso di **funzioni di hashing lente e con sale** come **PBKDF2**, **Bcrypt** o **Argon2**.
*   **Linee Guida NIST (Aggiunte 2025)**: Le raccomandazioni moderne sfatano molti miti:
    1.  Lunghezza minima di **8 caratteri**, ma è consigliato **15+**. Massima lunghezza consentita di almeno 64 caratteri.
    2.  Accettare tutti i caratteri stampabili, spazi e Unicode.
    3.  **NON** imporre regole di composizione complesse (es. "deve contenere maiuscole, numeri e simboli"), perché portano a password prevedibili (es. "Password1!").
    4.  **NON** richiedere la **cambio periodico della password**, se non in caso di compromissione accertata. Il cambio forzato frequente induce gli utenti a scegliere password deboli e sequenziali.
    5.  **NON** usare domande di sicurezza (Knowledge-Based Authentication - KBA).
    6.  **Permettere l'uso di Password Manager** e la funzione "incolla", perché incentivano l'uso di password lunghe, complesse e uniche.
*   **Passphrase Multilingue**: Uno studio dimostra che l'uso di passphrase (frasi lunghe) basate su lingue diverse dall'inglese (es. lingue africane) può aumentare la sicurezza, riducendo la prevedibilità.

### **Parte 5: Altri Meccanismi e Vulnerabilità Specifiche**
*   **One-Time Password (OTP)**: Codice valido una volta sola, generato da un server o da un'app (es. Google Authenticator, Symantec VIP). Vulnerabile ad attacchi di **SIM Swapping**, dove un attaccante convince l'operatore telefonico a trasferire il numero della vittima su una scheda SIM sotto il suo controllo, per intercettare gli SMS con gli OTP.
*   **Autenticazione con Sfide Multiple (Multi-Challenge)**: Durante la registrazione, l'utente fornisce più segreti (es. più impronte). All'accesso, il sistema ne richiede a caso un sottoinsieme, aumentando la sicurezza.
*   **PUF (Physical Unclonable Functions)**: Sfruttano le minuscole imperfezioni casuali introdotte nella fabbricazione dell'hardware per creare un'impronta digitale fisica unica e non clonabile del dispositivo, usata per autenticazione e generazione di chiavi.
*   **Biometria**: Più difficile da spoofare, ma richiede sensori costosi e algoritmi avanzati per precisione e rilevamento della vitalità. Problemi di accettazione sociale (intrusività) e di gestione dei template biometrici (se rubati, non si possono "cambiare" come una password).

La **scelta del metodo di autenticazione** deve bilanciare il **valore delle risorse da proteggere**, il **costo della soluzione** (hardware, software, formazione) e le **debolezze intrinseche** della soluzione stessa.

### **Parte 6: Controllo degli Accessi e Identity Management**

Una volta autenticato, bisogna controllare cosa l'utente può fare. Il **Controllo degli Accessi** si implementa attraverso:
*   **Reference Monitor**: Componente software che media tutti gli accessi a oggetti, applicando le policy di sicurezza.
*   **Matrice di Controllo degli Accessi**: Tabella teorica che per ogni soggetto (utente/processo) e oggetto (risorsa) specifica i diritti di accesso (Read, Write, Execute, Own...). Viene implementata praticamente tramite:
    *   **Access Control List (ACL)**: Lista associata a un oggetto, che dice chi può accedervi e come.
    *   **Capability List (C-LIST)**: Lista associata a un soggetto, che dice a quali oggetti può accedere e come.

**Policy di Controllo degli Accessi**:
*   **DAC (Discretionary)**: I proprietari delle risorse decidono chi può accedervi (es. permessi file Unix/Windows).
*   **MAC (Mandatory)**: Gli accessi sono controllati da policy centrali basate su etichette di sicurezza (es. classificazioni militari: Top Secret, Secret).
*   **RBAC (Role-Based)**: Gli accessi sono concessi in base ai ruoli organizzativi degli utenti (es. "Medico", "Contabile"). Efficiente per grandi organizzazioni.
*   **ABAC (Attribute-Based)**: Gli accessi sono concessi in base ad attributi dinamici dell'utente, della risorsa e del contesto (es. "L'utente è un dipendente del reparto X, che accede dal network aziendale, a un documento classificato come Y"). Molto flessibile.

La gestione degli account prevede processi precisi: creazione, abilitazione, monitoraggio, disabilitazione (per inattività, cambio ruolo, etc.) e rimozione.

### **Parte 7: Gestione degli Accessi Privilegiati (PAM)**

Gli account privilegiati (admin, root, service account) sono bersagli primari. La **Privileged Access Management (PAM)** è un ciclo che prevede:
1.  **Inventario** di tutti gli account privilegiati.
2.  **Identificazione** degli utenti (umani e non) e dei proprietari delle risorse.
3.  **Pulizia e Razionalizzazione** degli accessi.
4.  **Gestione dell'Accesso**:
    *   **JIT (Just-In-Time)**: L'accesso privilegiato è concesso solo per un breve periodo specifico.
    *   **PASM (Privileged Account & Session Management)**: Broker che gestiscono l'accesso agli account privilegiati, spesso creando account effimeri.
    *   **PEDM (Privileged Elevation & Delegation Management)**: Permette l'elevazione temporanea dei privilegi di un account normale (es. comando `sudo` su Linux).
5.  **Registrazione e Audit**: Sessioni, comandi, keystrokes vengono registrati. Il monitoraggio dell'integrità dei file e dei database completa il quadro. I log sono analizzati da strumenti **SIEM** e **UEBA**.
6.  **Automazione**: Rimuove l'elemento umano per task ripetitivi, riducendo errori e superficie d'attacco.

### **Parte 8: Protocolli di Autenticazione**

La lezione esamina protocolli per l'autenticazione di dispositivi in rete:
*   **PAP (Password Auth. Protocol)**: Invia password in chiaro. **INSICURO**.
*   **CHAP (Challenge-Handshake)**: Usa una challenge (nonce) e una risposta basata su hash della challenge + password condivisa. Più sicuro.
*   **EAP (Extensible Auth. Protocol)**: Framework flessibile che supporta molti metodi (EAP-TLS, EAP-PEAP, etc.), usato spesso in reti WiFi (WPA2/3 Enterprise).

Viene approfondito il **Protocollo Needham-Schroeder**, un protocollo fondamentale che utilizza un **Trusted Third Party (TTP)** per stabilire una chiave di sessione segreta (**K_AB**) tra due parti (Alice e Bob) che non si conoscono, usando chiavi pre-condivise con il TTP. Il protocollo usa **nonce** (numeri casuali usati una volta) per prevenire replay attack.

### **Parte 9: Autenticazione Federata e Standard Moderni**

*   **Kerberos**: Protocollo complesso ma elegante per l'autenticazione in reti distribuite, basato su ticket cifrati e timestamps per prevenire replay. Usa un **Key Distribution Center (KDC)** composto da Authentication Server (AS) e Ticket Granting Server (TGS).
*   **SAML (Security Assertion Markup Language)**: Standard XML per scambiare dichiarazioni di identità e autorizzazione tra Identity Provider e Service Provider. È alla base di **Shibboleth** (usato in molte università, come UniCa) e della prima versione di **SPID**.
*   **OAuth 2.0**: Standard di **autorizzazione**, non di autenticazione. Permette a un'applicazione di ottenere accesso limitato (delegato) alle risorse di un utente su un altro servizio, **senza condividere la password** (es. "Accedi con Facebook").
*   **FIDO (Fast IDentity Online)**: Iniziativa industriale per ridurre la dipendenza dalle password. Promuove standard per autenticatori basati su crittografia a chiave pubblica:
    *   **FIDO UAF (Universal Authentication Framework)**: Permette l'accesso senza password usando biometria, PIN, etc., registrati localmente sul dispositivo.
    *   **FIDO2/WebAuthn**: Standard web che permette l'accesso ai siti usando chiavi di sicurezza hardware (es. YubiKey) o metodi biometrici del dispositivo (es. Windows Hello, Touch ID), abilitando l'**autenticazione senza password (passwordless)**. Durante la registrazione, il dispositivo genera una coppia di chiavi crittografiche univoca per il sito; la chiave privata rimane sul dispositivo, quella pubblica viene inviata al server. Per autenticarsi, l'utente sblocca localmente la chiave privata (con biometria/PIN) per firmare una challenge del server.

---

### **Domande da Esame Possibili:**

1.  **Concetti Base:** Spiega la differenza tra **Identity Proofing**, **Enrollment** e **Authentication**. Descrivi i vantaggi di un modello di identità digitale **federato** rispetto a uno **non federato**.
2.  **Fattori e Meccanismi:** Elenca e descrivi i tre principali **fattori di autenticazione**. Cosa si intende per **Autenticazione Multi-Fattore (MFA)**? Fai un esempio pratico. Perché un OTP inviato via SMS è considerato un fattore di possesso meno sicuro di un OTP generato da un'app autenticatore?
3.  **Attacchi e Mitigazioni:** Classifica gli attacchi ai sistemi di autenticazione. Descrivi in dettaglio l'attacco di **SIM Swapping**: a quale fattore si rivolge, come funziona e quali contromisure si possono adottare.
4.  **Gestione Password:** Quali sono le principali **raccomandazioni del NIST SP 800-63** riguardo alla creazione e gestione delle password? Perché oggi si sconsiglia il cambio periodico obbligatorio e l'imposizione di regole di composizione complesse (es. simboli obbligatori)? Cosa sono i **Password Manager** e perché il NIST ne raccomanda l'uso?
5.  **Controllo Accessi:** Descrivi le differenze tra le quattro principali **policy di controllo degli accessi**: **DAC, MAC, RBAC, ABAC**. In quale scenario organizzativo è più appropriato l'RBAC?
6.  **Privileged Access Management (PAM):** Cosa si intende per **Privileged Account**? Descrivi il concetto di **Accesso Just-In-Time (JIT)** nel contesto della PAM e spiega quale problema di sicurezza aiuta a risolvere.
7.  **Protocolli e Standard:** Descrivi il ruolo di un **Trusted Third Party (TTP)** nel protocollo **Needham-Schroeder**. A quale tipologia di attacco (vista nella Parte 3) questo protocollo cerca di opporsi tramite l'uso dei nonce?
8.  **Autenticazione Moderna:** Spiega la differenza fondamentale tra **OAuth 2.0** e **SAML**. A quale scopo è progettato principalmente ciascuno? Descrivi in termini semplici come funziona l'autenticazione **passwordless** con lo standard **FIDO2/WebAuthn**.
