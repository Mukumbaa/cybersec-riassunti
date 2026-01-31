
# Lezione su Sicurezza dei Sistemi Operativi

Questa lezione esplora il ruolo fondamentale del sistema operativo (OS) nella sicurezza informatica, concentrandosi su come l'OS gestisce l'accesso, le autorizzazioni e le risorse in un ambiente multiutente, e su quali meccanismi hardware e software possono essere utilizzati per proteggere l'integrità del sistema.

---

## 1. Il ruolo del Sistema Operativo nella Sicurezza

Il sistema operativo è il **fondamento della sicurezza** in un sistema informatico. Le sue funzioni principali includono:

*   **Gestione di accesso e autorizzazioni**: decide chi (o quale processo) può fare cosa.
*   **Pianificazione dell'esecuzione delle applicazioni**: assicura che i programmi siano eseguiti in modo ordinato e controllato.
*   **Gestione delle risorse condivise**: come memoria, CPU, storage e dispositivi di I/O, tra processi concorrenti.

La capacità dell'OS di far rispettare **domini di sicurezza** (confini logici e fisici tra applicazioni) dipende direttamente dalle funzionalità hardware sottostanti. La gestione della sicurezza non riguarda solo la separazione delle risorse di alto livello (memoria, file), ma anche di quelle di basso livello come le **TLB (Translation Lookaside Buffer)** e le **cache**, che potrebbero essere sfruttate per attacchi laterali (side-channel).

---

## 2. Modello dell'Attaccante (Attacker Model)

Gli attaccanti cercano di compromettere un sistema operativo (o un hypervisor) attraverso varie strade:

1.  **Iniezione di estensioni malevole**: come driver o moduli del kernel dannosi.
2.  **Infezione del processo di boot**: per mantenere il controllo persistente sul sistema.
3.  **Sfruttamento di vulnerabilità software/hardware**: errori di memoria (buffer overflow), mancanza di validazione degli input, bug di concorrenza (race condition, double fetch).
4.  **Attacchi side-channel**: per ottenere informazioni indirettamente, osservando il comportamento fisico del sistema (es. tempo di esecuzione, consumo energetico).

---

## 3. Separazione tra Piano di Controllo e Piano dei Dati

L'OS deve garantire non solo la separazione tra processi, ma anche una netta distinzione tra:
*   **Piano di controllo**: il codice che prende decisioni (es. gestione della memoria, dello scheduler).
*   **Piano dei dati**: le informazioni su cui operano le applicazioni.

La lezione mostra diverse **architetture di design** per gli OS, che influenzano direttamente la sicurezza:
*   **(a) Dominio singolo**: usato in sistemi embedded semplici, nessuna separazione.
*   **(b) OS monolitico** (Linux, Windows): tutto il kernel è in un unico spazio di indirizzamento. Un bug in un driver può compromettere l'intero sistema.
*   **(c) Microkernel** (es. Minix-3): i servizi del sistema operativo girano come processi utente separati, migliorando l'isolamento.
*   **(d) Unikernel / Library OS**: l'applicazione e il necessario codice dell'OS sono compilati in un'unica immagine monolitica ed eseguiti direttamente sull'hypervisor, riducendo drasticamente la superficie d'attacco.

---

## 4. Ambienti di Esecuzione Fidati (Trusted Execution Environment - TEE)

I **TEE** sono un componente hardware/software fondamentale per la sicurezza moderna. Forniscono un ambiente di esecuzione isolato e sicuro all'interno della CPU, separato dal sistema operativo principale (chiamato **Rich Execution Environment - REE**).

**GlobalPlatform** definisce gli standard per i TEE, che devono garantire:
*   **Autenticità**: tutto il codice eseguito nel TEE è autenticato.
*   **Integrità**: le risorse del TEE sono protette da alterazioni.
*   **Riservatezza dei dati**: i dati (incluse le chiavi) sono cifrati o isolati.
*   **Riservatezza del codice delle Applicazioni Fidate (TA)**: il codice delle TA è protetto.
*   **Sicurezza**: resiste ad attacchi software e remoti noti, e a una classe di attacchi hardware.
*   **Protezione dal debug**: impedisce operazioni di debug e trace non autorizzate.

**Root of Trust (RoT)**: è l'elemento hardware o firmware fondamentale da cui parte il processo di **secure boot**. Garantisce che la catena di avvio, fino al caricamento del TEE, sia integra e autentica.

**Architetture TEE a confronto**:
*   **Intel SGX**: per PC client, crea enclave sicure all'interno di singole applicazioni.
*   **AMD SEV**: per server, cifra la memoria delle macchine virtuali.
*   **ARM TrustZone**: per dispositivi mobili e embedded, divide il sistema in un mondo "sicuro" e uno "normale".
*   **Sanctum/Sanctuary**: proposte accademiche che migliorano la protezione contro attacchi side-channel.

**Esempio pratico: Android Trusty TEE** è un OS sicuro che fornisce un TEE per Android, gestendo operazioni critiche come l'autenticazione biometrica e le transazioni finanziarie.

**Vulnerabilità nei TEE**: vengono citati attacchi come **GoFetch**, uno sfruttamento side-channel che estrae chiavi crittografiche sfruttando i prefetcher dipendenti dai dati (DMP) nelle CPU Apple, mostrando che anche ambienti "sicuri" non sono immuni a vulnerabilità microarchitetturali.

---

## 5. Pianificazione della Sicurezza di Sistema

La sicurezza di un sistema va pianificata **prima della sua installazione**. Il processo deve:
1.  **Valutare i rischi** e pianificare il deployment.
2.  **Proteggere l'OS sottostante** e poi le applicazioni chiave.
3.  **Proteggere i contenuti critici**.
4.  **Implementare meccanismi di protezione di rete** adeguati.
5.  **Stabilire processi per il mantenimento** della sicurezza.

La **pianificazione** deve definire chiaramente:
*   Lo scopo del sistema, il tipo di informazioni gestite e i requisiti di sicurezza.
*   Le categorie di utenti, i loro privilegi e le informazioni accessibili.
*   I metodi di autenticazione e gestione degli accessi.
*   L'accesso del sistema ad altri host (server di file, DB).
*   Le modalità di amministrazione (locale/remota).
*   Le misure di sicurezza aggiuntive (firewall host, antivirus, logging).

---

## 6. Hardening del Sistema Operativo

L'**hardening** è il processo di configurazione di un sistema per ridurne la superficie d'attacco. Include:

**a) Riduzione al minimo delle funzionalità**:
*   Rimozione di **servizi, applicazioni e protocolli non necessari**.
*   Revisione critica delle **configurazioni di default**, spesso orientate alla facilità d'uso piuttosto che alla sicurezza.

**b) Configurazione dei controlli sulle risorse**:
*   Impostazione di **permessi appropriati** su file e directory, seguendo linee guida di hardening specifiche per l'OS.

**c) Installazione di controlli di sicurezza aggiuntivi**:
*   **Software antimalware**.
*   **Firewall basati su host**.
*   **Sistemi di rilevamento/prevenzione delle intrusioni (IDS/IPS)**.
*   **Application whitelisting**: consente solo l'esecuzione di applicazioni pre-approvate.

**d) Utilizzo della crittografia**:
*   Configurazione di **TLS/IPsec/SSH** per la sicurezza delle comunicazioni di rete.
*   Implementazione di **file system crittografici** (es. BitLocker, EFS su Windows; LUKS su Linux) per proteggere i dati a riposo.

---

## 7. Manutenzione della Sicurezza

La sicurezza è un processo continuo. La manutenzione include:
*   **Monitoraggio e analisi dei log**: identificare attività sospette o violazioni.
*   **Backup regolari**: essenziali per il ripristino in caso di incidente. La politica di backup (locale/remoto, online/offline) va definita in fase di pianificazione.
*   **Ripristino da compromissioni**: avere un piano di disaster recovery.
*   **Test regolari della sicurezza** (es. penetration test).
*   **Patch management**: applicazione tempestiva di aggiornamenti di sicurezza per l'OS e le applicazioni critiche.

---

## 8. Hardening Specifico per OS

**Linux/Unix**:
*   **Modello a utenti/gruppi/permessi (rwx)** per risorse.
*   **Exploit locali e remoti**: devono essere mitigati con permessi minimi e aggiornamenti.
*   **Chroot jail**: isola un processo, limitandone la vista del filesystem a una sotto-directory specifica.

**Windows**:
*   **Privilegi a livello di sistema** e controlli di accesso granulari (permessi NTFS e di condivisione combinati).
*   **User Account Control (UAC)**: eleva i privilegi solo quando necessario.
*   **Account di servizio a bassi privilegi**: per processi di servizio di lunga durata.
*   **Registry**: database centrale di configurazione; va manipolato con cautela.
*   **Microsoft Defender**: suite integrata di antimalware e firewall.
*   **Crittografia**: EFS (per file/directory) e BitLocker (crittografia intero disco).
*   **Microsoft Security Compliance Toolkit**: strumento per verificare la conformità alle best practice di sicurezza.

---

## Domande da Esame

1.  **Descrivi le tre funzioni principali di un sistema operativo dal punto di vista della sicurezza. Perché la gestione delle risorse di basso livello (es. cache) è importante in questo contesto?**
2.  **Elenca e spiega brevemente almeno tre metodi attraverso i quali un attaccante può cercare di compromettere un sistema operativo, secondo l'attacker model presentato.**
3.  **Confronta l'architettura monolitica con quella a microkernel in termini di sicurezza. Quali sono i vantaggi e gli svantaggi di ciascun approccio?**
4.  **Cosa si intende per Trusted Execution Environment (TEE)? Elenca tre proprietà fondamentali che un TEE conforme a GlobalPlatform deve garantire.**
5.  **Fai un confronto tra Intel SGX, AMD SEV e ARM TrustZone, indicando per ciascuno il dispositivo target principale e una caratteristica distintiva.**
6.  **Spiega cos'è il "Secure Boot" e quale ruolo gioca il "Root of Trust (RoT)" in questo processo.**
7.  **Quali sono le fasi principali della pianificazione della sicurezza di un sistema? Descrivi cosa si intende per "hardening" del sistema operativo e fornisci due esempi concreti di azioni di hardening.**
8.  **Perché è importante ridurre al minimo i servizi e le applicazioni installate su un server? Quale principio di sicurezza si applica?**
9.  **Descrivi i componenti chiave di un processo di manutenzione della sicurezza continuativa. Perché il monitoraggio dei log è fondamentale?**
10. **Spiega la differenza tra un exploit locale e uno remoto. Come può la funzionalità "chroot jail" in Unix/Linux contribuire a contenere i danni di un exploit?**
11. **Nel contesto della sicurezza Windows, a cosa servono l'UAC (User Account Control) e gli account di servizio a bassi privilegi? Quale principio di sicurezza comune implementano?**
12. **Quali sono le due principali tecnologie di crittografia offerte da Windows per proteggere i dati a riposo? Descrivine brevemente la differenza.**

---
Questa lezione fornisce una visione sistematica di come la sicurezza sia intrinsecamente legata alla progettazione, configurazione e gestione del sistema operativo, sottolineando l'importanza di un approccio proattivo e stratificato che sfrutti sia meccanismi software che supporto hardware dedicato.
