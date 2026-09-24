# HelixCraft

Software desktop di supporto all'ingegneria genetica basato sull'IA · AI-powered gene engineering tools

[简体中文](README.md) · [English](README_EN.md) · [日本語](README_ja.md) · [한국어](README_ko.md) · [Français](README_fr.md) · [Deutsch](README_de.md) · [Español](README_es.md) · [Português](README_pt.md) · [Русский](README_ru.md) · **Italiano** · [العربية](README_ar.md) · [हिन्दी](README_hi.md) · [ไทย](README_th.md) · [Tiếng Việt](README_vi.md) · [Bahasa Indonesia](README_id.md) · [Türkçe](README_tr.md) · [Nederlands](README_nl.md) · [Polski](README_pl.md) · [Svenska](README_sv.md) · [Čeština](README_cs.md)

> HelixCraft è un software desktop per la ricerca in biologia molecolare e ingegneria genetica che copre l'intero flusso di lavoro «trovare il gene → leggere la sequenza → progettare il clonaggio → assemblaggio in silico → verifica sperimentale → gestione dei dati»: editor delle mappe dei vettori, analisi delle sequenze, progettazione dei primer, simulazione di digestioni di restrizione ed elettroforesi su gel, flussi di lavoro di clonaggio, analisi dei cromatogrammi di sequenziamento, analisi delle proteine e un assistente IA opzionale. Tutti i dati restano memorizzati sul tuo computer, senza registrazione di account né dipendenza dal cloud; l'interfaccia è disponibile in 20 lingue.
> Documentazione completa: [简体中文](README.md) · [English](README_EN.md)

## Cosa puoi fare con HelixCraft

- Aprire il file di un plasmide e vedere a colpo d'occhio la composizione dei suoi elementi e i siti di restrizione, per poi esportare figure della mappa pronte per la pubblicazione.
- Simulare per intero al computer un piano Gibson / Golden Gate / ligazione con enzimi di restrizione, prima di preparare anche una sola reazione.
- Progettare primer di clonaggio o primer qPCR a cavallo delle giunzioni degli esoni, con punteggi ed evidenze a supporto di ogni decisione.
- Consultare i cromatogrammi di sequenziamento, assemblare le read e verificare i risultati riallineandoli sul vettore ricombinante.
- Annotare corsie e bande nelle foto dei gel ed eseguire l'analisi quantitativa.
- Partire da una sequenza proteica per analizzarne le proprietà fisico-chimiche, la localizzazione subcellulare, i siti di modificazione e la struttura tridimensionale.
- Organizzare vettori, geni, primer e file di sequenziamento per progetto, trasferirli tra i computer del laboratorio ed eseguire backup periodici.

## Download

La versione più recente è sempre pubblicata sul canale [**Releases · latest**](releases/tag/latest):

| Piattaforma | Programma di installazione | Modalità di installazione |
|---|---|---|
| Windows 10 / 11 (x64) | `HelixCraft.Setup.<version>.exe` | Doppio clic per avviare la procedura guidata di installazione |
| Debian / Ubuntu (x86_64) | `helixcraft_<version>_amd64.deb` | Doppio clic per passarlo al programma di installazione grafico di sistema, oppure `sudo apt install ./<file>` |

Il canale `latest` è anche la sorgente dati della funzione «Verifica aggiornamenti» integrata nell'app, e i suoi file vengono sostituiti integralmente a ogni versione; le versioni storiche sono conservate nell'[elenco delle Releases](releases). Nella stessa cartella, `latest.json` è il manifesto degli aggiornamenti usato dall'applicazione: riporta per ogni programma di installazione il nome del file, la dimensione in byte e il digest SHA-256, così da poter verificare che il download sia completo e non sia stato manomesso.

## Installazione

### Windows

- Esegui `HelixCraft.Setup.<version>.exe` e segui la procedura guidata (per impostazione predefinita l'installazione è per tutti gli utenti e richiede i permessi di amministratore).
- La procedura guidata offre un componente opzionale di **dati di esempio** (vettori di esempio, flussi di lavoro di clonaggio e plugin di specie) per permettere ai nuovi utenti di iniziare subito; i dati di esempio vengono importati solo se il contenuto corrispondente non esiste ancora e **non sovrascrivono mai i dati che hai già creato**.
- **Installando sopra una copia esistente tutti i dati vengono conservati.** La directory dei dati è `%APPDATA%\HelixCraft` (i sottodatabase delle specie si trovano in `%APPDATA%\HelixCraftData`); la disinstallazione non la elimina.

### Linux (Debian / Ubuntu, x86_64)

- Il doppio clic sul file `.deb` lo consegna al programma di installazione grafico di sistema; il comando equivalente nel terminale è `sudo apt install ./helixcraft_<version>_amd64.deb`.
- Il programma viene installato in `/opt/HelixCraft` e i dati utente risiedono in `~/.config/HelixCraft`; **la disinstallazione non li elimina**.
- Si consiglia di avere installati nel sistema i font CJK per una corretta visualizzazione dei caratteri cinesi, giapponesi e coreani.

## Aggiornamenti online

Circa 20 secondi dopo l'avvio l'applicazione verifica la presenza di aggiornamenti in background (attiva per impostazione predefinita, al massimo una volta ogni 24 ore, disattivabile nelle impostazioni). Quando viene rilevata una nuova versione viene mostrato solo un avviso, **niente viene scaricato automaticamente**. Il download avviene via HTTPS, con supporto alla ripresa dei trasferimenti interrotti e verifica SHA-256, e i programmi di installazione che non superano la verifica vengono rifiutati. Su Windows l'installazione è completata dalla procedura guidata NSIS e l'applicazione si riavvia automaticamente; su Linux il file `.deb` scaricato viene affidato al programma di installazione del sistema.

## Funzioni principali

- **Mappa dei vettori ed editing diretto delle sequenze**: viste circolare e lineare collegate bidirezionalmente al testo della sequenza; elementi colorati per tipo, con siti di restrizione, posizioni di legame dei primer, ORF e marcatori di mutazione sovrapposti; stili completamente personalizzabili (colori, dimensioni dei caratteri, legenda, visibilità) con esportazione in SVG / PDF / PNG per le figure delle pubblicazioni. La sequenza si modifica direttamente (digitando, eliminando, incollando), con riaggiustamento automatico delle coordinate degli elementi e 50 passi di annullamento/ripetizione.
- **Annotazione intelligente**: l'intera sequenza del vettore viene confrontata con il database degli elementi per riconoscere automaticamente quelli noti (accettati solo con identità del DNA ≥99% o corrispondenza della traduzione ≥90%, con anteprima elemento per elemento prima dell'importazione in blocco) e vengono dedotti automaticamente campi come resistenza agli antibiotici, ospite, promotore e gene reporter, con livello di confidenza ed evidenze, senza sovrascrivere le informazioni esistenti.
- **Predizione degli ORF e ricerca BLAST online**: scansione dei sei frame di lettura (inclusi gli ORF che attraversano l'origine nei plasmidi circolari); qualsiasi selezione può essere inviata a NCBI (blastn / blastp / blastx e altri programmi).
- **Simulazione di digestioni ed elettroforesi virtuale su gel**: elenco dei frammenti in tempo reale per digestioni semplici, doppie o multiple, gestendo correttamente anche i siti che attraversano l'origine; i risultati vengono inviati con un clic alla simulazione del gel (11 marcatori comuni come DL2000 e 1 kb Ladder, concentrazione di agarosio, tensione e durata della corsa, con modelli di migrazione calibrati sulla letteratura) per prevedere se la digestione di controllo separerà la banda di interesse; controllo automatico degli effetti della metilazione (Dam / Dcm / CpG) e assistente alla scelta dei siti di restrizione.
- **Tela dei flussi di lavoro di clonaggio**: l'esperimento si collega come un diagramma di flusso — sorgenti di sequenze → progettazione primer / ottimizzazione dei codoni → PCR virtuale → digestione / purificazione → assemblaggio → trasformazione / PCR di colonia / verifica mediante sequenziamento → salvataggio nel database — con 30 tipi di nodi le cui uscite sono calcolate in tempo reale (modificando un ingresso a monte, tutto ciò che sta a valle si risimula immediatamente); la sequenza completa del plasmide ricombinante finale può essere controllata prima di considerare concluso il progetto. Supporta annullamento/ripetizione, salvataggio automatico e import/export JSON. Strategie di assemblaggio: Gibson, Golden Gate (BsaI / BbsI / BpiI / SapI, con suggerimento delle basi protettive), ligazione T4, clonaggio TA / TOPO, Gateway LR / BP, BioBrick.
- **Tela di costruzione molecolare (Beta)**: per il progetto del tipo «scegli lo scheletro e aggiungi gli elementi» — si seleziona lo scheletro nella libreria dei vettori, si riempiono i vuoti con i componenti e si sceglie il metodo di assemblaggio, e il software genera la strategia di linearizzazione, tutte le sequenze dei primer, il mix di assemblaggio, i frammenti attesi della PCR di colonia e i primer di sequenziamento suggeriti; il salvataggio è consentito solo se il prodotto coincide base per base con il progetto.
- **Progettazione primer generale e qPCR**: tre modalità e oltre 50 parametri regolabili (Tm, GC, lunghezza del prodotto, stabilità dell'estremità 3′…), con i 20 migliori candidati corredati da Tm, GC%, rischi di forcella e dimeri e un punteggio complessivo su 100; la procedura guidata qPCR esegue automaticamente l'allineamento di splicing mRNA/genoma, disegna la struttura degli esoni e progetta secondo strategie graduate — prima primer a cavallo delle giunzioni degli esoni, poi ampliconi che attraversano gli introni — evitando per costruzione l'interferenza del DNA genomico, con punteggio di conformità MIQE e collegamento automatico al gene al salvataggio; qualsiasi coppia di primer può essere verificata con una PCR in silico, e le coppie sono gestite nella libreria dei primer con import/export Excel e cronologia delle modifiche.
- **Analisi del sequenziamento**: visualizzatore di cromatogrammi AB1 con le quattro tracce di fluorescenza e i valori di qualità, confrontabili base per base con una sequenza di riferimento (correzioni manuali possibili, ma l'output dello strumento resta autorevole e non viene mai sovrascritto in silenzio); assemblaggio automatico delle read Sanger (algoritmo CAP3) con sequenza consenso dei contig, profondità di copertura e segnalazione delle zone a bassa qualità; verifica dei vettori ricombinanti riallineando le read sul tuo vettore — con scelta automatica dell'orientamento della catena migliore, incluso anche il vettore circolare che attraversa l'origine — tramite uno schema «elementi del vettore + disposizione delle read» colorato per identità, con mismatch / inserzioni / delezioni evidenti a colpo d'occhio; sono disponibili anche l'allineamento multiplo (ClustalW) e la costruzione di alberi filogenetici.
- **Analisi delle immagini di gel con IA**: procedura guidata in tre passi — apertura della foto, rilevamento automatico di corsie e bande da parte di un modello di deep learning integrato (aggiungibili, eliminabili o trascinabili a mano), quindi analisi quantitativa; dopo la scelta della corsia del marcatore e di una banda di riferimento con quantità nota, la curva di calibrazione delle dimensioni viene interpolata automaticamente e fornisce per ogni banda la **dimensione del frammento e la quantità di DNA** (densità ottica integrata); le figure annotate (PNG / JPG / BMP / TIF) e i risultati JSON sono esportabili.
- **Analisi delle proteine**: tre viste collegate (schema topologico ↔ pannello della sequenza di amminoacidi ↔ struttura 3D recuperata da RCSB PDB / AlphaFold DB), dove un clic su qualsiasi posizione o segmento evidenzia contemporaneamente sequenza e struttura; analisi locali in pochi secondi (massa molecolare, punto isoelettrico, idrofobicità, composizione, localizzazione subcellulare, sette classi di siti di modificazione post-traduzionale, regioni disordinate, a bassa complessità, coiled-coil o antigeniche); raffinamento online con scansione dei domini InterProScan e ricerche di omologia BLAST, che trasferisce sulla tua sequenza le annotazioni verificate di Swiss-Prot (solo aggiunte, mai sovrascritture delle conclusioni locali, con indicazione della fonte).
- **Gestione dei dati di laboratorio**: cinque database (vettori, sequenze, primer, enzimi — oltre 580 enzimi di restrizione con sequenze di riconoscimento, mappe di taglio, tipi, estremità e temperature, personalizzabili — e progetti); un intero gruppo di lavoro di vettori può essere impacchettato in un file `.hcvec` da inviare ai colleghi, che decidono voce per voce all'importazione; due computer con HelixCraft nella stessa rete locale possono scambiarsi dati in modo cifrato tramite un codice di abbinamento a 8 cifre, e la ricezione completa solo i campi vuoti senza sovrascrivere le modifiche esistenti; backup automatici all'avvio, backup completo manuale in un unico ZIP e ripristino con un clic; ogni eliminazione elenca prima tutti i dati associati coinvolti, e a te la scelta dell'ambito.
- **Assistente IA opzionale**: funziona con qualsiasi endpoint compatibile con OpenAI una volta configurato (la chiave API resta solo sul tuo computer); conosce il gene, il vettore o la finestra aperti in quel momento e può cambiare pagina, localizzare entità, interrogare e modificare i dati percorrendo esattamente lo stesso percorso dell'editing manuale (quindi con annullamento possibile); interpreta il testo dei protocolli di clonaggio ed estrae un piano strutturato (scheletro, inserto, enzimi, metodo di assemblaggio), ma **l'IA si limita a comprendere il testo e non genera mai alcuna sequenza di basi**. Senza configurare l'IA, ogni funzione conserva un percorso interamente manuale e il software resta pienamente utilizzabile.

## Plugin di dati delle specie

Le annotazioni dei geni e i dati di espressione vengono integrati tramite «plugin di dati delle specie», installabili, attivabili e disinstallabili dalla pagina delle impostazioni. Il pacchetto di installazione include i dati di annotazione del riso (circa 100.000 voci); annotazioni, sequenze e immagini ottenute online vengono salvate automaticamente in una cache locale che viene poi letta per impostazione predefinita, così tutto resta consultabile anche offline. I quattro plugin disponibili:

- **Riso (Rice)** — fonti RAP-DB, MSU-RGAP, RiceData e RiceXPro: annotazione dei loci, struttura degli esoni, sinonimi, fenotipi dei mutanti, mappe di espressione spazio-temporali (valori e immagini), sequenze di tutte le versioni e conversione degli identificatori tra database.
- **Ensembl Plants** — fonti Ensembl Plants ed EBI Expression Atlas: ricerca di geni in oltre 100 specie, download di sequenze, annotazioni GO ed espressione RNA-Seq.
- **Phytozome** — fonte JGI Phytozome: ricerca di geni, modelli genici, sequenze CDS / cDNA / proteiche, domini e geni omologhi.
- **ePlant (BAR)** — fonte BAR eFP Browser: pittogrammi a colori dell'espressione tissutale e livelli di espressione per tessuto per 13 specie.

## Sicurezza e privacy dei dati

- **Tutti i dati sono memorizzati localmente**: nulla viene caricato su alcun server; l'accesso alla rete avviene solo quando richiedi esplicitamente dati online (NCBI, database delle specie, archivi di strutture proteiche, aggiornamenti del software).
- **L'IA è completamente opzionale**: l'assistente richiede la tua chiave API, conservata soltanto sul tuo computer; senza IA, tutte le funzioni mantengono un percorso manuale.
- **L'unione non sovrascrive mai**: l'installazione dei dati di esempio, l'importazione di pacchetti e la ricezione tramite rete locale si limitano a completare i campi vuoti, senza toccare il contenuto esistente.

## Formati di file supportati

| Direzione | Formati |
|------|------|
| Apertura / importazione | GenBank (`.gb` `.gbk`), FASTA (`.fasta` `.fa` `.faa`), SnapGene (`.dna`), EMBL (`.embl`), cromatogrammi (`.ab1`), Excel dei primer (`.xlsx`), annotazioni proteiche (UniProtKB / GFF3 / InterProScan / GenPept), strutture proteiche (PDB / mmCIF), pacchetti HelixCraft (pacchetto di geni / pacchetto di vettori `.hcvec` / pacchetto di proteine `.hcp`) |
| Salvataggio / esportazione | GenBank, FASTA, SnapGene `.dna`, EMBL, immagini delle mappe (SVG / PDF / PNG / JPG / BMP / TIF), figure di gel annotate, Excel dei primer, annotazioni proteiche in 6 formati, pacchetto di geni / `.hcvec` / `.hcp`, pagina web statica dei dettagli del gene, ZIP di backup completo |

## Lingue dell'interfaccia

Dalla versione v0.3.7 tutti i moduli funzionali sono tradotti integralmente in 20 lingue: 简体中文, English, 日本語, 한국어, Français, Deutsch, Español, Português, Русский, Italiano, العربية, हिन्दी, ไทย, Tiếng Việt, Bahasa Indonesia, Türkçe, Nederlands, Polski, Svenska e Čeština. La lingua si cambia in qualsiasi momento in «Impostazioni → Lingua».

## Informazioni su questo repository

Questo repository serve esclusivamente a **distribuire i programmi di installazione e il manifesto degli aggiornamenti online**; non contiene il codice sorgente. La release del tag `latest` costituisce il canale di aggiornamento online (i file vengono sostituiti a ogni versione), mentre i tag `v<version>` archiviano le versioni storiche. Lo stesso repository è ospitato in parallelo su [GitHub](https://github.com/liudab/HelixCraft) e [GitCode](https://gitcode.com/BohanLab/HelixCraft), con i programmi di installazione pubblicati su entrambi.

## Licenza

[MIT](LICENSE)

## Contatti

Bohan Liu @ BohanLab · liubohan@hunau.edu.cn
