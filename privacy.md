
# Lezione su Privacy nella Rilascio di Dati

## Introduzione alla Privacy nella Società dell'Informazione

La privacy è un concetto complesso e sfaccettato, che assume significati diversi a seconda del contesto. Nella società contemporanea, l'informazione è una delle risorse più importanti, caratterizzata da una rapida evoluzione del panorama ICT (Tecnologie dell'Informazione e della Comunicazione), che porta a nuovi problemi ed esigenze di privacy. Una fonte rilevante di tali problemi è la raccolta, conservazione, analisi e rilascio (pubblico o selettivo) di grandi quantità di dati personali e generati dagli utenti, sia nel settore privato che in quello pubblico/governativo.

## Raccolta e Condivisione di Dati Personali

Ogni giorno, nelle attività più comuni, vengono raccolti e potenzialmente rilasciati una quantità e una varietà enormi di dati personali e identificativi. Esempi includono:
- Banche dati governative e aziendali (censimenti, dati demografici, medici, assicurativi, veicoli, ecc.)
- Email e altri contenuti generati dagli utenti tramite servizi Internet collaborativi e social network (post, tweet, foto, video, informazioni sulla posizione, ecc.)
- Dati generati durante la navigazione Internet, creazione di account online, invio di applicazioni, iscrizione a newsletter, partecipazione a sondaggi, associazioni, concorsi, giochi online (inclusi gli interessi degli utenti)
- Shopping online, transazioni finanziarie, ecc.

Le motivazioni principali per questa raccolta sono:
- Fornire servizi in modo più efficiente (risparmio di costi) ed efficace.
- Ricerca e scopi statistici, condivisione di conoscenza (es. studio di trend sociali e politici, studi epidemiologici).
- Requisiti imposti da leggi e regolamenti.

In passato, la diffusione dei dati offriva una protezione della privacy implicita, grazie all'accesso ristretto e ai costi elevati dell'elaborazione. Oggi, invece, è facile raccogliere, conservare e accedere a grandi quantità di dati in forma elettronica. Emergono problemi di proprietà dei dati e mancanza di controllo degli utenti sui propri dati. Inoltre, tecniche efficaci come il data mining e il machine learning permettono di analizzare e correlare dati da fonti diverse, consentendo ai destinatari di inferire informazioni originariamente non destinate alla divulgazione.

## Macrodata e Microdata

Le organizzazioni pubbliche e private spesso devono pubblicare o rilasciare dati su individui, famiglie e imprese (intervistati) per scopi di ricerca o statistici.

**Forme di pubblicazione:**
- **In passato:** rilascio di **macrodata** (informazioni aggregate, statistiche) in forma tabellare. I controlli venivano effettuati prima della pubblicazione. Oppure, database statistici che rispondevano solo a query statistiche, con controlli eseguiti prima della pubblicazione o in tempo reale.
- **Oggi:** rilascio sempre più frequente di **microdata**, ovvero dati dettagliati sugli intervistati, in forma tabellare.

Esempi di fonti sono gli istituti statistici come EUROSTAT (UE) e ISTAT (Italia), che pubblicano sia macrodata che microdata (quest'ultimi spesso su richiesta o con accesso riservato).

**Macrodata:** sono valori stimati di caratteristiche statistiche di una data popolazione (informazioni aggregate), rilasciati in forma tabellare. La caratteristica statistica è una misura che riassume i valori di alcune proprietà/attributi (variabili) degli intervistati (es. età media delle persone in una regione). Le tabelle di macrodata si categorizzano in base al contenuto delle celle:
- **Conteggio (Count):** numero di intervistati che hanno lo stesso valore su tutti gli attributi di analisi.
- **Frequenza (Frequency):** percentuale di intervistati sulla popolazione totale che hanno lo stesso valore.
- **Magnitudine (Magnitude):** valore aggregato (es. media) di una quantità di interesse (es. età).

**Protezione dei Macrodata:** L'obiettivo è garantire la riservatezza, assicurando che nessuna informazione su singoli intervistati possa essere derivata dai macrodata. L'approccio principale è l'offuscamento selettivo di **celle sensibili** (celle facilmente associabili a un singolo intervistato). Le strategie di scoperta e protezione dipendono dal tipo di tabella.
- Per tabelle di **conteggio e frequenza**, una strategia comune è la **regola della soglia (threshold rule)**: una cella è sensibile se il numero di intervistati è inferiore a una soglia data. Tecniche di protezione includono la **soppressione della cella** (rimozione del valore) e l'**arrotondamento** (arrotondamento per eccesso o difetto a un multiplo di un numero base).
- Per tabelle di **magnitudine**, una strategia è la **regola (n,k)**: una cella è sensibile se *n* o meno intervistati contribuiscono al *k%* o più del valore totale. Anche qui si usano tecniche come la soppressione.

In generale, le tecniche di protezione per tabelle statistiche si basano su:
1. **Limitare le informazioni rilasciabili** (es. vincoli sulle query disponibili, limitazione dei dati recuperabili).
2. **Restituire all'utente un risultato modificato**, offline (modificando i dati memorizzati) o in tempo reale (durante il calcolo del risultato della query).

## Rilascio di Microdata e De-Identificazione

Il passo base per proteggere la privacy (anonimato) degli intervistati nel rilascio di microdata è la **de-identificazione**: nascondere (rimuovere o cifrare) gli attributi che identificano personalmente (es. codice fiscale, nome, indirizzo).

Tuttavia, la de-identificazione **non garantisce l'anonimato**. I destinatari dei microdata de-identificati potrebbero avere **conoscenze esterne** (ad esempio, altri dataset non de-identificati che condividono alcuni attributi) che, tramite analisi e correlazione (**data linking**), possono portare a:
- **Identificazione (Identity disclosure):** ri-identificare alcuni intervistati o ridurre l'incertezza sulla loro identità.
- **Divulgazione di attributi (Attribute disclosure):** rivelare informazioni sensibili sugli intervistati (es. malattie).
- **Divulgazione inferenziale (Inferential disclosure):** informazioni che possono essere inferite con alta probabilità dalle proprietà statistiche dei dati rilasciati.

**Esempi Reali di Violazioni della Privacy:**
1. **Incidente AOL (2006):** AOL rilasciò 20 milioni di record di query di ricerca di 650.000 utenti, sostituendo gli identificatori con ID numerici. Giornalisti del New York Times riuscirono a ri-identificare un'utente (Thelma Arnold) basandosi sulle informazioni contenute nelle sue query.
2. **Incidente Netflix (2006):** Netflix rilasciò 100 milioni di record di valutazioni di film per un concorso. Ricercatori dimostrarono che alcuni record potevano essere ri-identificati collegandoli a valutazioni pubbliche su IMDb. Una causa legale portò alla cancellazione di un secondo concorso.
3. **Identificazione di partecipanti a ricerche genetiche (2013):** Studi dimostrarono che l'identità dei partecipanti poteva essere scoperta incrociando i loro dati con database genetico-genealogici pubblici.

Uno studio sui dati del censimento USA 2000 mostrò che una frazione significativa della popolazione era identificabile in modo univoco da data di nascita completa, sesso e codice postale (ZIP) o contea.

## Tecniche di Protezione dei Microdata

Le tecniche di protezione si possono categorizzare in:
- **Masking (Mascheramento):** Trasformazione dei dati originali, mantenendo la validità dell'analisi statistica.
  - **Non perturbativo (conservativo della verità):** Soppressione di dati e/o rimozione di dettagli (es. campionamento di tuple, soppressione locale di valori, generalizzazione di valori).
  - **Perturbativo:** Modifica dei dati originali (es. arrotondamento, iniezione di rumore casuale su attributi continui).
- **Sintetiche (Synthetic):** Sostituzione delle tuple originali con tuple sintetiche, preservando le proprietà statistiche chiave.
  - **Completamente sintetiche:** Vengono rilasciati solo dati sintetici.
  - **Parzialmente sintetiche:** Viene rilasciato un mix di dati sintetici e originali.

Le definizioni di privacy si dividono in:
- **Definizioni Sintattiche:** Hanno come target gli **intervistati**. Impostano requisiti sintattici, con un grado numerico di privacy per ciascun intervistato (es. *k*-Anonimato).
- **Definizioni Semantiche:** Hanno come target **qualsiasi individuo**, sia intervistati che non. Impostano requisiti semantici da soddisfare tramite il meccanismo di rilascio dati (es. **Differential Privacy**).

## k-Anonimato

L'obiettivo è ridurre il rischio di ri-identificazione degli intervistati nei microdata. L'agenzia statistica impone che qualsiasi informazione rilasciata debba essere indistinguibilmente relata ad almeno un certo numero *k* di individui. Più alto è *k*, maggiore è l'incertezza sull'identità di un intervistato.

**Ipotesi principali del *k*-Anonimato:**
- Tutti i dati rilasciati sono in una singola tabella.
- Dopo il rilascio, la tabella non viene mai modificata.
- Ogni tupla si riferisce a un intervistato distinto.
- L'unica conoscenza esterna disponibile ai destinatari consiste in dataset pubblici non anonimi che condividono alcuni attributi con la tabella (attributi **quasi-identificatori, QI**).

**Categorizzazione degli attributi:**
- **Identificatori (Identifiers):** Attributi che permettono l'identificazione univoca (es. CF, nome, indirizzo). Vengono sempre rimossi o mascherati prima del rilascio.
- **Quasi-Identificatori (QI):** Insieme di attributi disponibili anche in dataset pubblici non anonimi, che possono essere sfruttati per ri-identificare gli intervistati (es. data di nascita, sesso, CAP).
- **Attributi Confidenziali (Confidential attributes):** Informazioni sensibili da proteggere (es. malattie), che però non permettono la ri-identificazione.
- **Attributi Non-Confidenziali (Non-confidential attributes):** Non considerati sensibili, possono essere rilasciati senza danni.

**Definizione di *k*-Anonimato (Pratica):** Una tabella rilasciata è *k*-anonima se, e solo se, ogni combinazione di valori del QI appare con zero o almeno *k* occorrenze nella tabella stessa.
Soddisfare questa definizione è una condizione sufficiente (ma non necessaria) per soddisfare il requisito originale.

**Come rendere *k*-anonima una tabella:** Si usano due operatori di mascheramento non-perturbativo:
- **Generalizzazione:** Modifica dei valori del QI, sostituendoli con valori più generali (es. da data precisa a solo anno; da CAP a prefisso più generale). Può essere a livello di cella o di attributo. Spesso si basa su **gerarchie di generalizzazione** predefinite per ogni attributo. Riduce la *precisione* dei dati.
- **Soppressione:** Rimozione selettiva di elementi di dati (celle, attributi, intere tuple). Riduce la *completezza* dei dati.
Esiste un **trade-off** tra utilità dei dati (piccola perdita di informazione) e protezione della privacy (grande perdita di informazione). L'obiettivo degli algoritmi è trovare un'istanza *k*-anonima che minimizzi la perdita di informazione.

## Protezione dalla Divulgazione di Attributi Sensibili

Il *k*-Anonimato protegge l'identità, ma **non** protegge dagli attacchi che mirano a divulgare gli attributi sensibili (es. malattie). Due attacchi principali:
1. **Attacco di Omogeneità (Homogeneity attack):** Se in una classe di equivalenza (insieme di tuple con stesso valore del QI) tutti gli individui hanno lo stesso valore dell'attributo sensibile, un attaccante che sa che una persona è in quella classe può inferire il suo attributo sensibile.
2. **Attacco di Conoscenza Esterna (External knowledge attack):** Un attaccante conosce alcuni fatti specifici su un individuo (es. pratica sport agonistico). Combinando questa conoscenza con la distribuzione dei valori sensibili nella sua classe di equivalenza, può ridurre l'incertezza o determinare il valore sensibile.

Per contrastare questi attacchi si introduce il requisito **ℓ-Diversità (ℓ-Diversity)**: Estende il *k*-Anonimato richiedendo che in ogni classe di equivalenza ci siano almeno **ℓ** valori "ben rappresentati" per l'attributo sensibile. L'idea è che un attaccante debba escludere almeno *ℓ-1* valori per inferire quello corretto.
- L'attacco di omogeneità non è più possibile.
- L'attacco di conoscenza esterna è meno efficace.
Anche ℓ-Diversità si realizza con generalizzazione e soppressione.

Tuttavia, tabelle *k*-anonime e *ℓ*-diverse sono ancora vulnerabili ad altri attacchi:
- **Attacco di Skewness (Asimmetria):** La distribuzione dei valori sensibili in una classe di equivalenza è diversa (skewed) rispetto alla distribuzione nell'intera popolazione o tabella. Un attaccante può aggiornare la sua probabilità a posteriori su un individuo.
- **Attacco di Similarità (Similarity attack):** I valori sensibili in una classe di equivalenza sono sintatticamente diversi ma semanticamente simili (es. tutte malattie cardiovascolari). Un attaccante può inferire la categoria sensibile.

Per contrastare questi attacchi si introduce il requisito **t-Vicinanza (t-Closeness)**: Richiede che la distribuzione dei valori dell'attributo sensibile in ogni classe di equivalenza sia simile (con distanza inferiore a una soglia *t*) alla distribuzione osservabile nell'intero dataset rilasciato. Questo riduce l'efficacia di skewness e similarity attack. Anche *t*-Closeness si realizza con generalizzazione e soppressione.

## Limiti degli Approcci Sintattici e Differential Privacy

Gli approcci sintattici (*k*-Anonimato, ℓ-Diversità, t-Vicinanza) hanno limiti:
- Considerano solo forme specifiche di conoscenza esterna.
- Partono dall'assunzione (irrealistica) che il titolare dei dati conosca tutta la conoscenza esterna disponibile ai destinatari.
- Proteggono solo la privacy degli **intervistati** (rischio di identificazione e divulgazione di attributi).
- **Non proteggono i non-intervistati.** I dati rilasciati possono essere usati per inferire informazioni su individui non rappresentati nella tabella (es. combinando medie di gruppo con conoscenze personali).

**Differential Privacy (DP)** è una nozione di privacy **semantica** che mira a proteggere la privacy di **entrambi** gli intervistati e i non-intervistati.
- **Obiettivo principale:** Garantire che l'inclusione o l'esclusione delle informazioni di un singolo individuo da un database **non alteri in modo significativo** il risultato di qualsiasi analisi eseguita su quel database.
- Non fa assunzioni sulla conoscenza esterna disponibile al destinatario.
- Protegge minimizzando l'aumento di rischio per un individuo derivante dalla sua partecipazione (o meno) a un database.

**Definizione formale (ε-Differential Privacy):**
Dati due database *D* e *D'* che differiscono per al più una tupla, un meccanismo di rilascio randomizzato *K(·)* soddisfa ε-DP se per ogni possibile sottoinsieme di risultati *S*:
\[ P[K(D) \in S] \leq e^{\epsilon} \times P[K(D') \in S] \]
Il parametro ε > 0 misura il grado di protezione della privacy (ε più piccolo = privacy più forte). Informalmente, la distribuzione di probabilità dei risultati dell'analisi deve essere "essenzialmente la stessa" indipendentemente dalla presenza o assenza di un singolo individuo.

**Come si realizza la DP:** Aggiungendo **rumore controllato** ai dati originali o ai risultati delle query. È quindi una tecnica di mascheramento **perturbativa** (non conserva la verità dei dati originali).
- **Scenario Interattivo:** Si aggiunge rumore al risultato di ogni query eseguita sul database privato.
- **Scenario Non-Interattivo:** Si rilascia pubblicamente un dataset (es. una matrice di frequenze) a cui è stato aggiunto rumore.

La DP offre garanzie di privacy forti ma impone condizioni severe, e il rumore richiesto può distorcere significativamente i dati, limitandone l'utilità. Possibili soluzie includono rilassamenti della DP o la sua combinazione con *k*-Anonimato per ridurre la quantità di rumore.

## Applicazioni degli Approcci di Privacy

I concetti di privacy, in particolare *k*-Anonimato, sono stati adattati a vari scenari applicativi:
1. **Servizi Basati sulla Localizzazione (LBS):** Per proteggere la posizione degli utenti (che può essere sia un QI che un dato sensibile), si offusca la posizione in un'area "clandestina" che includa almeno *k* utenti diversi, rendendo la richiesta indistinguibile.
2. **Pubblicazione di Traiettorie/Movimenti:** Per analisi dei flussi, si applicano versioni come *(k,δ)-Anonimato* (almeno *k* traiettorie simili entro un raggio δ) o *Trajectory k-Anonimato* (raggruppamento e perturbazione di traiettorie simili).
3. **Analisi di Social Network:** I grafi delle relazioni sociali (nodi=utenti anonimi, archi=relazioni) possono essere protetti con versioni come *k-degree Anonimato* (ogni nodo ha lo stesso grado di almeno *k-1* altri nodi) o *k-neighborhood Anonimato* (il sottografo del vicinato di ogni nodo è isomorfo a quello di almeno *k-1* altri nodi).
4. **Contact Tracing:** App per tracciare i contatti per malattie possono essere progettate per garantire forme di *k*-Anonimato, limitando la possibilità di identificare individui specifici dai log di prossimità.

---

## Domande da Esame

1. **Spiega la differenza tra macrodata e microdata, fornendo esempi per ciascuno e descrivendo i rischi di privacy associati al loro rilascio.**
2. **Descrivi il processo di de-identificazione dei microdata. Perché da solo non è sufficiente a garantire l'anonimato?**
3. **Illustra con un esempio concreto come il data linking tramite conoscenze esterne può portare alla ri-identificazione in un dataset di microdata de-identificati.**
4. **Definisci il concetto di *k*-Anonimato. Quali sono le sue ipotesi fondamentali e come si categorizzano gli attributi in una tabella per applicarlo?**
5. **Spiega le due principali tecniche operative (con esempi) per rendere *k*-anonima una tabella di microdata. Qual è il trade-off intrinseco in questo processo?**
6. **Descrivi l'"attacco di omogeneità" e l'"attacco di conoscenza esterna" a una tabella *k*-anonima. Come il requisito di ℓ-Diversità mira a contrastarli?**
7. **Cosa sono l'"attacco di skewness" e l'"attacco di similarità"? Come il requisito di t-Vicinanza cerca di mitigare questi rischi?**
8. **Confronta gli approcci sintattici (es. *k*-Anonimato) e l'approccio semantico della Differential Privacy in termini di obiettivi di privacy, assunzioni e tecniche di protezione.**
9. **Spiega la definizione formale di ε-Differential Privacy. Perché si dice che protegga anche i non-intervistati?**
10. **Quali sono i principali limiti della Differential Privacy e quali soluzie vengono proposte per mitigarli?**
11. **Come può essere adattato il concetto di *k*-Anonimato per proteggere la privacy nei Servizi Basati sulla Localizzazione (LBS)? Descrivi il meccanismo di "cloaking".**
12. **Descrivi due diverse versioni del requisito di *k*-Anonimato applicate alla pubblicazione di dati di traiettoria o movimento.**
13. **In che modo l'analisi dei social network presenta rischi di privacy specifici? Come possono essere applicati i concetti di *k-degree Anonimato* e *k-neighborhood Anonimato*?**
14. **Discuti, con un esempio, come i dati aggregati (macrodata) possano comunque portare a violazioni della privacy dei non-intervistati. Perché la Differential Privacy è più adatta a gestire questo scenario?**
15. **Partendo da un semplice dataset di esempio, mostra i passaggi per renderlo *k*-anonimo (con un *k* a scelta) e discuti come si potrebbero poi applicare i requisiti di ℓ-Diversità e t-Vicinanza.**
