
Questa lezione è un viaggio approfondito attraverso la storia, le minacce e i principi fondamentali della cybersecurity. Copre un arco temporale che va dalle origini della comunicazione fino alle sfide più attuali, con una particolare enfasi sull'evoluzione delle minacce informatiche e sulle strategie di difesa.

**Parte 1: L'Evoluzione della Comunicazione e di Internet**
La lezione inizia riflettendo su come il linguaggio e i mezzi di comunicazione si siano evoluti nel corso dei millenni (dai graffiti preistorici), per poi accelerare esponenzialmente con l'avvento delle tecnologie digitali. Viene spiegato che Internet è nato con due scopi principali:
1.  Come rete privata per scopi di difesa.
2.  Come rete per condividere conoscenze tra ricercatori.
È stato uno strumento rivoluzionario che ha permesso di trasmettere testo, audio, immagini e video attraverso lo stesso canale. Tuttavia, viene sottolineato un punto cruciale: **Internet non è stato progettato** per le comunicazioni personali quotidiane, né per le transazioni sensibili con banche, servizi sanitari o governi. Questa "mancanza di progettazione" originaria per la sicurezza è una delle radici di molte vulnerabilità attuali.

**Parte 2: La Nascita del Cybercrime e l'Evoluzione delle Minacce**
Il documento traccia la storia degli attacchi informatici, partendo dai primi virus sperimentali degli anni '70 e '80 (come il "Brain" per MS-DOS) fino agli attacchi sofisticati dei giorni nostri.
Viene introdotto il concetto di **Cybercrime**, caratterizzato da:
*   **Alto rapporto guadagno/costo**: Permette grandi profitti con investimenti relativamente bassi e rischi materiali minimi.
*   **Beni e rischi intangibili**: Si rubano dati, non oggetti fisici.
*   **Bassa percezione come crimine**: Spesso non viene percepito come un reato grave quanto un furto fisico.

L'evoluzione delle motivazioni degli attaccanti ("Threat Actors") è descritta in una timeline (pag. 21):
*   **Fino al 1995 circa**: **Intrusi occasionali**, mossi da curiosità, desiderio di testare i sistemi e provocare disagi. Attacchi semplici come lo sniffing del traffico.
*   **Era di Internet (2000-2010)**: Compaiono gli **Script Kiddies** (per notorietà) e le prime **cyber-gang** (per profitto). Si diffondono virus, worm, phishing e frodi con carte di credito.
*   **Dal 2010 in poi**: Il panorama si complica con **Hacktivisti** (motivazioni politiche/ideologiche), **Cybercriminali professionisti**, e **Attori sponsorizzati da stati-nazione** (per spionaggio, sabotaggio, guerra cibernetica). Gli attacchi diventano **Advanced Persistent Threats (APT)**, mirati, persistenti e distruttivi (es.: DDoS, violazioni dati).

Tra gli attacchi storici citati ci sono:
*   **Robert Morris Worm (1988)**: Il primo worm a diffondersi su ARPANET.
*   **Code Red (2001)**: Worm che causò miliardi di dollari di danni.
*   **Attacco a Dyn (2016)**: Enorme attacco DDoS che oscurò gran parte di Internet sulla costa est degli USA.
*   **SolarWinds (2020)**: Un **attacco alla catena di fornitura (Supply Chain Attack)** di portata globale, dove il malware ("SUNBURST") fu inserito in un aggiornamento software legittimo, compromettendo migliaia di organizzazioni.

**Parte 3: I Principi Fondamentali della Sicurezza (CIA Triad)**
Il cuore della sicurezza informatica si basa sul **triangolo CIA**:
*   **Riservatezza (Confidentiality)**: Garantire che le informazioni siano accessibili solo a chi è autorizzato. Le minacce sono l'intercettazione e l'esposizione non autorizzata.
*   **Integrità (Integrity)**: Assicurare che le informazioni non siano alterate in modo non autorizzato. Le minacce sono la modifica e la falsificazione.
*   **Disponibilità (Availability)**: Garantire che sistemi e dati siano accessibili quando servono. Le minacce sono gli attacchi Denial of Service (DoS) e il danneggiamento fisico.

Queste proprietà devono essere protette a tutti i livelli: **Hardware, Software, Dati e Linee di Comunicazione**.

**Parte 4: Tassonomia degli Attacchi e Modello del Flusso d'Informazioni**
La lezione presenta un modello utile: qualsiasi azione di un sistema può essere vista come un **flusso di informazioni** da una fonte (source) a una destinazione (sink). Gli attacchi mirano a modificare questo flusso e si classificano in:
1.  **Interruzione (Interruption)**: Il flusso viene bloccato o distrutto (attacco alla Disponibilità).
2.  **Intercettazione (Interception)**: Una parte non autorizzata accede al flusso (attacco alla Riservatezza).
3.  **Modifica (Modification)**: Il flusso viene intercettato e alterato prima di arrivare a destinazione (attacco a Integrità e Riservatezza).
4.  **Fabbricazione (Fabrication)**: Vengono creati flussi di informazioni falsi, spacciandosi per una fonte attendibile (attacco all'Autenticità, collegata all'Integrità).

Questa classificazione è legata alle **Conseguenze delle Minacce** definite nello standard RFC2828: **Divulgazione Non Autorizzata, Inganno, Interruzione e Usurpazione**.

**Parte 5: Il Panorama Attuale delle Minacce (Threat Landscape)**
Vengono descritti i principali attori delle minacce odierne e le loro motivazioni:
*   **Cybercriminali**: Guidati dal profitto (furto di dati, ransomware).
*   **Insider (Dipendenti)**: Motivati da vendetta o guadagno personale.
*   **Attori Statali/Nazione**: Per spionaggio, vantaggio militare, economico o politico.
*   **Hacktivisti**: Per cause politiche o sociali, cercano visibilità.
*   **Organizzazioni Terroristiche**: Attività cyber prevalentemente di disturbo, usano il web per comunicazione e reclutamento.

Viene menzionata la **Cyber Kill Chain** di Lockheed Martin, un modello a fasi che descrive la progressione di un attacco informatico (dalla ricognizione all'esfiltrazione dei dati), utile per pianificare la difesa.

**Parte 6: Strategie e Contromisure di Cybersecurity**
La difesa si articola in una strategia strutturata:
1.  **Policy di Sicurezza**: Le regole formali che definiscono come proteggere le risorse.
2.  **Implementazione**: Si attua su quattro fronti:
    *   **Prevenzione**: Controlli di accesso fisici e logici (firewall, principio del minimo privilegio), cifratura (crittografia), patch software.
    *   **Rilevamento (Detection)**: Antivirus, sistemi di Intrusion Detection/Prevention (IDS/IPS), sistemi SIEM per analisi dei log.
    *   **Risposta (Response)**: Piani per contenere e neutralizzare un attacco in corso.
    *   **Ripristino (Recovery)**: Backup, piani di disaster recovery.
3.  **Garanzia (Assurance)**: La fiducia che il sistema sia stato progettato e implementato correttamente.
4.  **Valutazione (Evaluation)**: Processo di verifica (es.: certificazioni Common Criteria).

**Parte 7: Sfide Future e Considerazioni Critiche**
La lezione si conclude esplorando le sfide che rendono la cybersecurity difficile:
*   **Complessità e Superficie d'Attacco**: Internet è un sistema immenso e complesso. Il difensore deve proteggere tutto, l'attaccante deve trovare un solo punto debole.
*   **Software Insecure**: Molto software è rilasciato con vulnerabilità.
*   **Consumerization e BYOD (Bring Your Own Device)**: I dipendenti usano dispositivi personali per lavoro, espandendo la superficie d'attacco.
*   **Internet of Things (IoT)**: Ogni dispositivo connesso (frigoriferi, auto, termostati) è un computer potenzialmente vulnerabile. La "privacy" assume nuovi significati in un mondo di sensori sempre attivi.
*   **Feudal Security**: La teoria secondo cui ci affidiamo a pochi grandi fornitori (Google, Apple, Microsoft, Amazon) per la nostra sicurezza, come in un sistema feudale.
*   **Leggi che inibiscono la ricerca**: A volte le normative ostacolano la ricerca sulla sicurezza.

Vengono citati i **"Truismi" di Bruce Schneier**, esperto di sicurezza, che riassumono efficacemente la sfida: "Su Internet, **attaccare è più facile che difendere**".

---

### **Domande da Esame Possibili:**

1.  **Storia e Concetti Base:** Spiega perché, nonostante le sue origini, Internet si è rivelato intrinsecamente vulnerabile per le applicazioni commerciali e personali odierne. Fai un esempio di un attacco storico e descrivilo brevemente.
2.  **Threat Actors:** Descrivi l'evoluzione delle motivazioni degli attaccanti informatici dagli anni '90 a oggi. Quali sono le principali categorie di "Threat Actor" attuali e quali sono i loro obiettivi?
3.  **CIA Triad e Modelli di Attacco:** Definisci la Triade CIA. Utilizzando il modello del flusso di informazioni, spiega in cosa consistono e quale proprietà della CIA violano gli attacchi di: a) Intercettazione, b) Modifica, c) Interruzione.
4.  **Tipologie di Attacchi:** Cosa sono gli **Advanced Persistent Threats (APT)**? In che modo l'attacco a SolarWinds del 2020 rappresenta un esempio particolarmente pericoloso di attacco alla catena di fornitura (Supply Chain Attack)?
5.  **Strategie di Difesa:** Elenca e descri i quattro pilastri dell'**Implementazione della Sicurezza** (Prevenzione, Rilevamento, Risposta, Ripristino). Fai un esempio di strumento o pratica per ciascuno di essi.
6.  **Sfide Attuali e Future:** Secondo Bruce Schneier, perché "su Internet, attaccare è più facile che difendere"? Collega questa affermazione alle sfide poste dall'Internet of Things (IoT) e dal fenomeno BYOD.
