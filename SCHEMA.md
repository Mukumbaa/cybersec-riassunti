
Ecco una schematizzazione completa e strutturata di tutto il materiale fornito. Come richiesto, è stata posta particolare enfasi sull'elenco puntuale degli step di framework, procedure e cicli operativi.

---

# **SCHEMA GENERALE DEL CORSO DI CYBERSECURITY**

Il materiale è suddiviso in 4 macro-aree logiche:
1.  **Fondamenti e Gestione (Governance & Management)**
2.  **Tecnologie e Meccanismi Difensivi**
3.  **Minacce e Offensiva (Threats & Offensive)**
4.  **Operazioni, Analisi e Metodologie**

---

## **AREA 1: FONDAMENTI E GESTIONE**

### **1. Introduzione e Storia**
*   **Concetti Base:**
    *   **Triade CIA:** Confidentiality (Riservatezza), Integrity (Integrità), Availability (Disponibilità).
    *   **Modello di Flusso:** Interruzione, Intercettazione, Modifica, Fabbricazione.
*   **Evoluzione Minacce:**
    *   Dagli *Intrusi Occasionali* agli *APT (Advanced Persistent Threats)* e *Stati-Nazione*.
    *   Legge di Schneier: "Attaccare è più facile che difendere".

### **2. Risk Management (Gestione del Rischio)**
*   **Definizioni:**
    *   Rischio (ISO): Effetto dell'incertezza sugli obiettivi.
    *   Rischio (NIST): Funzione di impatto negativo e probabilità.
*   **ISO 31000 - Processo di Risk Management:**
    1.  Comunicazione e Consultazione.
    2.  Definizione del Contesto (interno/esterno, criteri).
    3.  Valutazione del Rischio (Risk Assessment):
        *   Identificazione.
        *   Analisi.
        *   Valutazione (Evaluation).
    4.  Trattamento del Rischio.
    5.  Monitoraggio e Riesame.
*   **NIST RMF (Risk Management Framework) - SP 800-37:**
    1.  Preparare (Prepare).
    2.  Categorizzare (Categorize).
    3.  Selezionare (Select).
    4.  Implementare (Implement).
    5.  Valutare (Assess).
    6.  Autorizzare (Authorize).
    7.  Monitorare (Monitor).
*   **NIST CSF (Cybersecurity Framework) 2.0 - Funzioni:**
    1.  GOVERNARE (Govern).
    2.  IDENTIFICARE (Identify).
    3.  PROTEGGERE (Protect).
    4.  RILEVARE (Detect).
    5.  RISPONDERE (Respond).
    6.  RECUPERARE (Recover).
*   **Opzioni di Trattamento del Rischio:**
    1.  Accettazione/Ritenzione.
    2.  Eliminazione/Evitamento.
    3.  Modifica/Mitigazione.
    4.  Condivisione/Trasferimento (es. Assicurazione).

### **3. Security Management (Gestione della Sicurezza)**
*   **Strumenti Strategici:**
    *   **Security Policy:** Definisce chi accede, a cosa e come.
    *   **Piano di Sicurezza Informatica (Contenuti):**
        1.  Policy.
        2.  Stato attuale.
        3.  Requisiti.
        4.  Controlli raccomandati.
        5.  Accountability (Responsabilità).
        6.  Cronogramma (Timetable).
        7.  Manutenzione del piano.
*   **Incident Response (CSIRT) - Fasi:**
    1.  Reporting (Segnalazione).
    2.  Rilevamento (Detection).
    3.  Triaging (Valutazione priorità).
    4.  Risposta (Response - Contenimento/Eradicazione).
    5.  Post-Mortem (Analisi e Lezioni apprese).
    6.  Educazione.
*   **Business Continuity (BCP):** Ciclo PDCA (Plan-Do-Check-Act) secondo ISO 22301.

### **4. Certificazioni**
*   **Standard ISO:**
    *   ISO/IEC 17024 (Persone).
    *   ISO/IEC 17065 (Prodotti).
*   **Common Criteria (ISO 15408) - Certificazione Prodotto:**
    *   Uso di Protection Profiles (PP).
    *   Livelli di Garanzia: EAL1 (minimo) fino a EAL7 (formale verificato).

---

## **AREA 2: TECNOLOGIE E MECCANISMI DIFENSIVI**

### **1. Autenticazione e Access Control**
*   **Fattori di Autenticazione:** Conoscenza (Sai), Possesso (Hai), Inerenza (Sei).
*   **Linee Guida Password (NIST SP 800-63):** Lunghezza 8-64+, no regole composizione complesse, no scadenza periodica, uso password manager.
*   **Protocollo Needham-Schroeder (con TTP):**
    1.  A richiede a TTP connessione con B.
    2.  TTP invia ad A la chiave di sessione e un ticket per B (cifrato).
    3.  A invia il ticket a B.
    4.  B decifra il ticket e usa il nonce per verificare A.
*   **FIDO2/WebAuthn (Passwordless):**
    1.  Registrazione: Generazione coppia chiavi sul dispositivo (privata protetta da bio/PIN).
    2.  Autenticazione: Server invia challenge -> Utente sblocca chiave privata -> Firma challenge -> Server verifica con chiave pubblica.
*   **Gestione Accessi Privilegiati (PAM) - Ciclo:**
    1.  Inventario account.
    2.  Identificazione utenti.
    3.  Pulizia accessi.
    4.  Gestione accesso (JIT, PASM, PEDM).
    5.  Audit/Logging.
    6.  Automazione.

### **2. Crittografia**
*   **Obiettivi:** Riservatezza, Integrità, Autenticità, Non Ripudio.
*   **Algoritmi:** Simmetrici (AES, DES), Asimmetrici (RSA, Diffie-Hellman), Hash (SHA-256).
*   **Firma Digitale (Processo):**
    1.  Mittente calcola Hash del messaggio.
    2.  Mittente cifra Hash con propria Chiave Privata (= Firma).
    3.  Destinatario decifra Firma con Chiave Pubblica del Mittente.
    4.  Destinatario ricalcola Hash del messaggio e confronta.
*   **PKI (Public Key Infrastructure):** Gerarchia di fiducia basata su CA (Certificate Authority) e Certificati Digitali.

### **3. Sicurezza Sistemi Operativi (OS Security)**
*   **Concetti:** Trusted Execution Environment (TEE), Root of Trust (RoT), Secure Boot.
*   **Processo di Hardening:**
    1.  Rimozione servizi/app non necessari.
    2.  Revisione configurazioni default.
    3.  Configurazione permessi (File/Dir).
    4.  Installazione controlli aggiuntivi (Antimalware, FW).
    5.  Uso crittografia (Disk encryption).
*   **Manutenzione Sicurezza:**
    1.  Monitoraggio Log.
    2.  Backup regolari.
    3.  Patch Management.
    4.  Test periodici.

### **4. Cloud & IoT**
*   **Modelli Servizio:** IaaS, PaaS, SaaS (Responsabilità Condivisa).
*   **Framework CSA STAR:**
    *   Livello 1: Autovalutazione.
    *   Livello 2: Audit di terza parte.
*   **IoT:** Architettura a strati (Device, Gateway, Cloud, App). Sfide: Patching difficile, Trust Boundaries.

### **5. Privacy e Data Release**
*   **Tecniche:** De-identificazione, k-Anonimato, l-Diversità, t-Vicinanza.
*   **Differential Privacy (Processo concettuale):**
    *   Aggiunta di rumore controllato (perturbazione) ai dati o alle query affinché il risultato sia probabilisticamente identico con o senza i dati di un singolo individuo.

---

## **AREA 3: MINACCE E OFFENSIVA**

### **1. Malware**
*   **Classificazione:** Virus, Worm, Trojan, Ransomware, Spyware, Rootkit.
*   **Lifecycle Virus:** Infezione -> Trigger -> Payload.
*   **Advanced Persistent Threat (APT):** Attacchi mirati, multistadio, persistenti.

### **2. Social Engineering**
*   **Principi Psicologici:** Simpatia, Autorità, Reciprocità, Urgenza, Riprova Sociale.
*   **Ciclo dell'Attacco di Social Engineering:**
    1.  Ricerca (Investigation/OSINT).
    2.  Adescamento (Hook/Pretexting).
    3.  Sfruttamento (Play).
    4.  Uscita (Exit).
    5.  Ritocco (Cleanup).

### **3. Software Vulnerabilities**
*   **Tassonomia:** CWE (Debolezze) vs CVE (Vulnerabilità specifiche).
*   **Categorie Critiche:** Buffer Overflow (Memoria), Injection (SQL, OS), Race Conditions.
*   **Sviluppo Sicuro (Secure Coding):**
    1.  Validazione input.
    2.  Uso linguaggi Memory-Safe.
    3.  Principio del Minimo Privilegio.
    4.  Analisi Statica (SAST) e Dinamica (DAST).

### **4. Adversarial Machine Learning**
*   **Attacchi al ciclo di vita ML:**
    *   **Poisoning:** In fase di Training (modifica dati).
    *   **Evasion:** In fase di Test/Inference (es. Adversarial Examples).

---

## **AREA 4: OPERAZIONI, ANALISI E METODOLOGIE**

### **1. Threat Modeling (Modellazione delle Minacce)**
*   **Processo di Threat Modeling (4 Domande):**
    1.  Cosa stiamo costruendo? (Modellazione sistema/DFD).
    2.  Cosa può andare storto? (Identificazione minacce).
    3.  Cosa faremo al riguardo? (Mitigazioni).
    4.  Abbiamo fatto un buon lavoro? (Validazione).
*   **Modello STRIDE (Identificazione):**
    *   **S**poofing (Autenticazione).
    *   **T**ampering (Integrità).
    *   **R**epudiation (Non ripudio).
    *   **I**nformation Disclosure (Riservatezza).
    *   **D**enial of Service (Disponibilità).
    *   **E**levation of Privilege (Autorizzazione).
*   **Modello DREAD (Valutazione):** Damage, Reproducibility, Exploitability, Affected Users, Discoverability.

### **2. Cyber Threat Intelligence (CTI)**
*   **Livelli:** Tattico (IOC), Operativo (TTPs), Strategico (Business/Impact).
*   **Cyber Kill Chain (Lockheed Martin) - 7 Fasi:**
    1.  Ricognizione (Reconnaissance).
    2.  Armamento (Weaponization).
    3.  Consegna (Delivery).
    4.  Sfruttamento (Exploitation).
    5.  Installazione (Installation).
    6.  Comando e Controllo (C2).
    7.  Azioni sugli obiettivi (Actions on Objectives).
*   **MITRE ATT&CK:** Matrice di Tattiche (Perché) e Tecniche (Come).

### **3. OSINT (Open Source Intelligence)**
*   **Ciclo dell'Intelligence:**
    1.  Pianificazione e Direzione.
    2.  Raccolta (Collection).
    3.  Elaborazione (Processing).
    4.  Analisi e Produzione.
    5.  Diffusione (Dissemination).
    6.  Valutazione e Feedback.

### **4. Pentesting & Ethical Hacking**
*   **Definizione:** Sfruttamento intelligente delle regole del sistema per scopi non previsti.
*   **Fasi implicite:** Scansione (Nmap), Enumerazione, Exploitation (Metasploit), Post-Exploitation.
*   **Strumenti:** Kali Linux, Metasploit, Nmap, Wireshark.

### **5. Machine Learning per la Sicurezza**
*   **Applicazioni:** Rilevamento Malware (Statico/Dinamico), Phishing, IDS.
*   **Valutazione (Matrice di Confusione):**
    *   TP (Veri Positivi), FP (Falsi Positivi).
    *   TN (Veri Negativi), FN (Falsi Negativi).
*   **Metriche:** Accuratezza, Precisione, Recall, F-Score.
