
Certamente. Ecco una spiegazione dettagliata, discorsiva e completa dell'intero documento sulla crittografia.

---

## **Spiegazione del Materiale: Crittografia**

Questa lezione fornisce una panoramica completa della **crittografia**, la scienza che permette di proteggere informazioni trasformandole in una forma illeggibile (crittografata) a chi non è autorizzato. Vedremo i concetti fondamentali, gli algoritmi storici e moderni, e le loro applicazioni pratiche per garantire **riservatezza, integrità, autenticità e non ripudio**.

### **Parte 1: Concetti Fondamentali e Primitivi Crittografici**

La crittografia ha tre obiettivi principali:
1.  **Riservatezza (Confidentiality):** Assicurare che solo il destinatario autorizzato possa leggere il messaggio.
2.  **Integrità (Integrity):** Garantire che il messaggio non sia stato alterato durante la trasmissione.
3.  **Autenticità (Authenticity):** Verificare l'identità del mittente e/o del destinatario.

Il processo base coinvolge un **messaggio in chiaro (plaintext)**, una **funzione di cifratura** `E`, e una **chiave segreta (K)**. Il risultato è il **testo cifrato (ciphertext)**: `C = E(K, M)`. Il processo inverso è la decifratura: `M = D(K, C)`.

Esistono due tipi fondamentali di sistemi crittografici:
*   **Simmetrico:** Mittente e destinatario condividono **la stessa chiave segreta** (es., AES, DES). È veloce, ma richiede un canale sicuro per lo scambio iniziale della chiave.
*   **Asimmetrico (o a chiave pubblica):** Ogni utente ha una coppia di chiavi: una **pubblica** (che tutti possono conoscere) e una **privata** (segreta). Ciò che viene cifrato con una può essere decifrato solo con l'altra. Risolve il problema dello scambio delle chiavi, ma è molto più lento.

I metodi base per mascherare un messaggio sono due:
*   **Sostituzione:** Ogni carattere del testo in chiaro viene sostituito con un altro secondo una regola. Obiettivo: **confusione** (es., Cifrario di Cesare, dove ogni lettera è spostata di 3 posizioni: A→D, B→E).
*   **Trasposizione:** L'ordine dei caratteri o dei blocchi del messaggio viene rimescolato secondo una regola. Obiettivo: **diffusione** (rendere la statistica del testo cifrato indipendente da quella del testo in chiaro).

Un algoritmo speciale è l'**OTP (One-Time Pad)**: usa una chiave segreta lunga almeno quanto il messaggio, perfettamente casuale e mai riutilizzata. È matematicamente inviolabile, ma praticamente scomodo per la gestione delle chiavi.

### **Parte 2: Cifrari Simmetrici Moderni e Sicurezza**

Claude Shannon definì i principi per un buon cifrario, tra cui semplicità, assenza di propagazione degli errori e sicurezza che dipende **solo dalla segretezza della chiave** (Principio di Kerckhoffs).

Un cifrario può essere:
*   **A Blocchi (Block Cipher):** Cifra il testo in chiaro a blocchi di dimensione fissa (es., 128 bit per AES). Esempi: DES, AES.
*   **A Flusso (Stream Cipher):** Cifra il testo in chiaro un bit/byte alla volta, combinandolo con un flusso di chiave pseudo-casuale. Esempio: RC4.

**Data Encryption Standard (DES):**
Sviluppato da IBM negli anni '70, DES è un cifrario a blocchi da 64 bit con chiave da 56 bit. La sua struttura a **Rete di Feistel** alterna fasi di sostituzione e permutazione per 16 round. La breve lunghezza della chiave lo rese vulnerabile alla **forza bruta** già negli anni '90 (con macchine specializzate come il "DES cracker"). Per prolungarne la vita, nacquero varianti:
*   **Triple DES (3DES):** Applica DES tre volte (Cifra-Decifra-Cifra) con due o tre chiavi. Fornisce una sicurezza equivalente a chiavi da 112 bit, ma è lento.

**Advanced Encryption Standard (AES):**
Nel 2001, NIST scelse l'algoritmo **Rijndael** come nuovo standard. AES è un cifrario a blocchi da 128 bit con chiavi da 128, 192 o 256 bit. Non è una rete di Feistel, ma esegue ripetutamente 4 operazioni su una matrice di byte: **Sostituzione di Byte (SubBytes)**, **Shift di Righe (ShiftRows)**, **Mistura di Colonne (MixColumns)** e **Aggiunta della Chiave di Round (AddRoundKey)**. È veloce, efficiente in hardware e software e rimane lo standard indiscusso per la cifratura simmetrica.

### **Parte 3: Funzioni Hash e Autenticazione**

Le **funzioni hash crittografiche** sono algoritmi unidirezionali che prendono un input di lunghezza qualsiasi e producono un'impronta digitale a lunghezza fissa (**digest** o **hash**), come una "impronta digitale" del dato. Proprietà fondamentali:
1.  **Unidirezionalità:** Dato l'hash `h`, è computazionalmente impossibile trovare un input `m` tale che `hash(m) = h`.
2.  **Resistenza alle collisioni:** È difficile trovare due input diversi `m1` e `m2` con lo stesso hash (`hash(m1) = hash(m2)`).
3.  **Effetto valanga:** Un piccolo cambiamento nell'input produce un hash completamente diverso.

Standard importanti: **MD5** (128 bit, rotto), **SHA-1** (160 bit, deprecato), **SHA-2** (SHA-256, SHA-512) e **SHA-3**, il nuovo standard basato su un principio diverso (spugna).

Le funzioni hash sono fondamentali per:
*   **Codici di Autenticazione di Messaggio (MAC/HMAC):** Per assicurare integrità e autenticità di un messaggio. Il mittente calcola un hash del messaggio concatenato con una chiave segreta condivisa. Il destinatario ripete il calcolo; se i MAC coincidono, il messaggio è autentico e integro.
*   **Firme Digitali:** Per fornire anche **non ripudio**.

### **Parte 4: Crittografia Asimmetrica (a Chiave Pubblica)**

Risolve il problema dello scambio delle chiavi. Si basa su problemi matematici difficili da risolvere, ma le cui operazioni inverse sono facili.

**Diffie-Hellman (DH):**
Non è un algoritmo di cifratura, ma un protocollo per lo **scambio di chiavi**. Permette a due parti (Alice e Bob) di generare un segreto condiviso su un canale insicuro, basandosi sul **problema del logaritmo discreto**. In sostanza, mescolano pubblicamente i loro "ingredienti segreti" (le chiavi private) per ottenere un "colore segreto" comune (la chiave di sessione) che un osservatore esterno non può ricavare.

**RSA (Rivest-Shamir-Adleman):**
L'algoritmo a chiave pubblica più famoso, basato sulla difficoltà di **fattorizzare il prodotto di due numeri primi molto grandi**.
*   **Generazione chiavi:** Si scelgono due primi grandi `p` e `q`, si calcola `n = p*q` (modulo pubblico). Si sceglie un esponente pubblico `e` e si calcola un esponente privato `d` tale che `e*d ≡ 1 mod (p-1)(q-1)`.
*   **Cifratura:** `C = M^e mod n`.
*   **Decifratura:** `M = C^d mod n`.

RSA può essere usato sia per cifratura (con la chiave pubblica del destinatario) che per **firma digitale** (con la propria chiave privata).

**Firme Digitali:**
Sono l'equivalente elettronico di una firma autografa. Il mittente calcola l'hash del messaggio e lo "cifra" (firma) con la sua **chiave privata**, producendo la firma. Chiunque può verificarla decifrandola con la **chiave pubblica** del mittente e confrontando l'hash risultante con quello calcolato sul messaggio ricevuto. Questo garantisce **autenticità, integrità e non ripudio**.

### **Parte 5: Infrastrutture a Chiave Pubblica (PKI) e Certificati**

Come facciamo a fidarci che una chiave pubblica appartenga davvero a una certa persona? La risposta è il **certificato digitale**.

Un certificato è un documento elettronico che **collega un'identità (es., un nome, un dominio web) a una chiave pubblica**, ed è **firmato digitalmente da un'Autorità di Certificazione (CA)** di fiducia (es., Let's Encrypt, DigiCert). La **firma della CA** sul certificato ci dice: "Io, ente di fiducia, certifico che questa chiave pubblica appartiene a questo soggetto".

La **PKI (Public Key Infrastructure)** è l'insieme di ruoli, politiche, procedure, hardware e software necessari per creare, gestire, distribuire, utilizzare e revocare certificati digitali. I certificati sono organizzati in **catene di fiducia gerarchiche**, che vanno dalla CA **root** (auto-firmata e pre-installata nei browser) fino all'utente finale.

### **Parte 6: Applicazioni Pratiche e Protocolli**

La crittografia è il motore della sicurezza moderna:
*   **SSL/TLS:** Protegge le comunicazioni web (HTTPS). Combina cifratura simmetrica (AES) per velocità, scambio di chiavi asimmetrico (RSA o Diffie-Hellman) e certificati per autenticare il server.
*   **Signal Protocol:** Usato da WhatsApp e Signal. Un protocollo di messaggistica **end-to-end encrypted** di stato dell'arte. Utilizza l'algoritmo **Double Ratchet**, che fornisce **secrecy forward (segretà futura)** e **post-compromise security**: anche se una chiave viene compromessa, le sessioni future e passate rimangono protette, grazie a una continua rigenerazione di chiavi basata su scambi Diffie-Hellman.
*   **VPN (Virtual Private Network):** Crea un "tunnel" cifrato attraverso Internet, permettendo a utenti remoti o sedi di accedere alla rete aziendale come se fossero locali.
*   **SSH (Secure Shell):** Sostituisce protocolli di accesso remoto non sicuri (telnet), fornendo un canale cifrato e autenticato per la shell.
*   **WPA2/WPA3:** Gli standard di sicurezza per le reti Wi-Fi. Usano una gerarchia di chiavi derivata da una passphrase e un "four-way handshake" per autenticare i client e stabilire chiavi di sessione uniche, cifrando il traffico con AES.
*   **Tor:** Una rete di anonimizzazione che instrada il traffico attraverso una serie di nodi volontari ("relay"), cifrandolo a strati. Ogni nodo conosce solo il nodo precedente e il successivo, rendendo molto difficile tracciare l'origine del traffico.

### **Parte 7: Sfide Future e Crittografia Post-Quantistica**

L'avvento dei **computer quantistici** rappresenta una minaccia esistenziale per gli algoritmi a chiave pubblica attuali. L'algoritmo di **Shor** permetterebbe a un computer quantistico sufficientemente potente di risolvere in tempi brevi sia il problema della fattorizzazione (rompendo RSA) che quello del logaritmo discreto (rompendo Diffie-Hellman e ECC).

**Crittografia Post-Quantistica (PQC)** è il campo di ricerca che sviluppa nuovi algoritmi crittografici resistenti agli attacchi quantistici, basati su problemi matematici diversi (es., reticoli, codici di correzione d'errore). NIST e altre agenzie (come l'italiana ACN) stanno già aggiornando le linee guida per prepararsi a questa transizione, che sarà necessaria per proteggere la sicurezza a lungo termine delle nostre comunicazioni e dati.

---

### **Domande da Esame**

1.  **Concetti Fondamentali:** Spiega la differenza fondamentale tra un sistema crittografico **simmetrico** e uno **asimmetrico**. Per ognuno, indica un vantaggio e uno svantaggio principale. Cosa si intende per "principio di Kerckhoffs" e perché è importante?
2.  **Algoritmi Simmetrici:** Descrivi brevemente la struttura e la storia del **DES**. Perché è stato considerato insicuro? Come ha cercato di rimediare il **Triple DES (3DES)** e perché oggi si preferisce l'**AES**? Quali sono i vantaggi di AES?
3.  **Funzioni Hash:** Elenca e spiega le tre proprietà fondamentali di una **funzione hash crittografica**. A cosa serve un **HMAC (Hash-based Message Authentication Code)**? Descrivi il processo attraverso cui un mittente crea un HMAC e un destinatario lo verifica.
4.  **Crittografia a Chiave Pubblica:** Spiega come funziona lo **scambio di chiavi di Diffie-Hellman**. Perché due parti possono generare un segreto condiviso su un canale insicuro senza che un eavesdropper possa ricavarlo? Qual è il problema matematico su cui si basa la sua sicurezza?
5.  **RSA e Firme Digitali:** Descrivere i passi principali per **generare una coppia di chiavi RSA**. Spiega poi come viene utilizzato RSA per creare una **firma digitale** su un documento. Quali garanzie di sicurezza fornisce questa firma (es., integrità, non ripudio)?
6.  **PKI e Certificati:** Che cos'è un **certificato digitale** e qual è il ruolo di un'**Autorità di Certificazione (CA)** all'interno di una **PKI**? Perché, quando navighiamo su un sito HTTPS, possiamo fidarci della sua identità?
7.  **Protocolli e Applicazioni:** Scegli **UNO** dei seguenti protocolli e descrivi come utilizza la crittografia per garantire la sicurezza:
    *   **SSL/TLS** (per HTTPS)
    *   **Signal Protocol** (per la messaggistica)
    *   **WPA2** (per il Wi-Fi)
8.  **Sfide Future:** Perché i **computer quantistici** rappresentano una minaccia per gli algoritmi a chiave pubblica attuali come RSA e Diffie-Hellman? Cosa si intende per **crittografia post-quantistica** e qual è l'obiettivo della ricerca in questo campo?
