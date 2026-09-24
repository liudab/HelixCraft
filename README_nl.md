# HelixCraft

**AI-ondersteunde desktopsoftware voor gentechnologie** · AI-powered gene engineering tools

[简体中文](README.md) · [English](README_EN.md) · [日本語](README_ja.md) · [한국어](README_ko.md) · [Français](README_fr.md) · [Deutsch](README_de.md) · [Español](README_es.md) · [Português](README_pt.md) · [Русский](README_ru.md) · [Italiano](README_it.md) · [العربية](README_ar.md) · [हिन्दी](README_hi.md) · [ไทย](README_th.md) · [Tiếng Việt](README_vi.md) · [Bahasa Indonesia](README_id.md) · [Türkçe](README_tr.md) · **Nederlands** · [Polski](README_pl.md) · [Svenska](README_sv.md) · [Čeština](README_cs.md)

> HelixCraft is een desktopapplicatie voor onderzoek in moleculaire biologie en gentechnologie. Het ondersteunt de volledige workflow van *een gen opzoeken → sequenties lezen → een klonering ontwerpen → virtuele assemblage → experimentele verificatie → gegevensbeheer*: vectorkaarten bewerken, sequentieanalyse, primerontwerp, simulatie van restrictievertering en gelelektroforese, kloneringsworkflows, analyse van Sanger-chromatogrammen, opzoeken van soortgegevens, eiwitanalyse en een optionele AI-assistent. Alle gegevens blijven op je eigen computer — geen account nodig en geen afhankelijkheid van de cloud. De interface is beschikbaar in 20 talen.
>
> Volledige documentatie: [简体中文](README.md) · [English](README_EN.md)

## Wat kun je ermee doen

- Open een plasmidebestand en zie de elementen en restrictielocaties overzichtelijk voor je, en exporteer daarna een kaartfiguur van publicatiekwaliteit;
- simuleer een Gibson / Golden Gate / restrictie-ligatieplan volledig op de computer voordat je aan de reactie begint;
- ontwerp kloneringsprimers of qPCR-primers die exongrenzen overspannen, met scores en een onderbouwde evaluatie;
- bekijk sequenceringschromatogrammen, assembleer reads en controleer de resultaten door ze terug te alignen op je recombinante vector;
- voorzie gelfoto's van baan- en bandannotaties en voer een kwantitatieve analyse uit;
- analyseer een eiwitsequentie op fysisch-chemische eigenschappen, subcellulaire lokalisatie, modificatieplaatsen en 3D-structuur;
- beheer vectoren, genen, primers en sequenceringsbestanden per project, wissel ze uit tussen labcomputers en maak er regelmatig een back-up van.

## Downloaden

De nieuwste versie is altijd te vinden in het [**Releases · latest-kanaal**](releases/tag/latest):

| Platform | Installatieprogramma | Installatiemethode |
|---|---|---|
| Windows 10 / 11 (x64) | `HelixCraft.Setup.<version>.exe` | Dubbelklikken en de installatiewizard volgen |
| Debian / Ubuntu (x86_64) | `helixcraft_<version>_amd64.deb` | Dubbelklikken (grafische installatie van het systeem) of `sudo apt install ./<file>` |

Het `latest`-kanaal is tegelijk de gegevensbron van de optie “Controleren op updates” in de app; de bijbehorende bestanden worden bij elke release compleet vervangen. Oudere versies vind je in de [Releases-lijst](releases), waar elke versie een eigen archief heeft. Het `latest.json` in dezelfde release is het updatemanifest dat de app gebruikt en bevat per installatieprogramma de bestandsnaam, de grootte en de SHA-256-controlesom, waarmee je de download kunt verifiëren.

## Installatie

### Windows

- Systeemvereiste: Windows 10 of nieuwer (x64). Voer `HelixCraft.Setup.<version>.exe` uit en volg de wizard (standaard voor alle gebruikers geïnstalleerd; administratorrechten vereist).
- De wizard biedt een optioneel onderdeel met **voorbeeldgegevens** aan (voorbeeldvectoren, kloneringsworkflows en soortgegevens-plugins), zodat nieuwe gebruikers direct kunnen starten. Voorbeeldgegevens worden alleen geïmporteerd als de betreffende inhoud nog niet bestaat en **overschrijven nooit gegevens die je zelf hebt aangemaakt**.
- **Een installatie over een bestaande versie behoudt al je gegevens.** De gegevensmap is `%APPDATA%\HelixCraft` (de subdatabases met soortgegevens staan in `%APPDATA%\HelixCraftData`); bij het verwijderen van het programma blijft deze map behouden.

### Linux (Debian / Ubuntu, x86_64)

- Dubbelklik op het `.deb`-bestand; het wordt dan doorgegeven aan de grafische installatie van het systeem (GNOME Software / App Center / KDE Discover / GDebi). Het equivalente terminalcommando is `sudo apt install ./helixcraft_<version>_amd64.deb`.
- Het programma wordt geïnstalleerd in `/opt/HelixCraft`; gebruikersgegevens staan in `~/.config/HelixCraft` en **worden bij het verwijderen van het programma niet gewist**.
- CJK-lettertypen worden aanbevolen (het pakket declareert `Recommends: fonts-noto-cjk`; gebruik daarom `apt install` en niet `dpkg -i`, want `dpkg -i` slaat aanbevolen afhankelijkheden over).

## Online-updates

Ongeveer 20 seconden na het opstarten controleert de app op de achtergrond of er een nieuwe versie is (standaard ingeschakeld, maximaal één keer per 24 uur, uit te schakelen in de instellingen). Een nieuwe versie wordt alleen gemeld — er wordt **niets automatisch gedownload**. Downloads verlopen via HTTPS, met hervatting na onderbreking en SHA-256-verificatie; installatieprogramma's die de verificatie niet doorstaan worden geweigerd. Op Windows voltooit de NSIS-wizard de installatie en start de app daarna automatisch opnieuw; op Linux wordt het gedownloade `.deb`-bestand aan de software-installatie van het systeem meegegeven.

## Belangrijkste functies

- **Vectorkaart en directe sequentiebewerking**: circulaire en lineaire kaarten zijn in twee richtingen gekoppeld met de sequentietekst; elementen worden per type gekleurd en samengevoegd met restrictielocaties, primerbindingsplaatsen, ORF's en mutatiemarkeringen. De kaartstijl (kleuren, tekstgroottes, legenda, zichtbaarheid) is vrij in te stellen en te exporteren naar SVG / PDF / PNG en meer voor publicatiefiguren. Typen, verwijderen en plakken kan direct in de sequentie; na invoegen of verwijderen passen elementcoördinaten zich automatisch aan, en alle bewerkingen ondersteunen 50 stappen ongedaan maken / opnieuw.
- **Slimme annotatie**: de volledige vector wordt vergeleken met de elementendatabase om bekende elementen automatisch te herkennen (erkend pas bij ≥99% DNA-identiteit of ≥90% vertaalde overeenkomst), en velden zoals antibioticaresistentie, gastheer, promoter en reportergen worden automatisch afgeleid — met betrouwbaarheid en bewijs; bestaande informatie wordt niet overschreven.
- **ORF-voorspelling en online BLAST**: scan in alle zes leesramen (inclusief ORF's die de oorsprong van circulaire plasmiden overspannen) en dien een geselecteerde sequentie in bij NCBI (blastn / blastp / blastx en andere programma's).
- **Restrictievertering en virtuele gelelektroforese**: enkele, dubbele en meervoudige verteringen leveren direct een fragmentlijst op — ook correct voor locaties die bij circulaire plasmiden over de oorsprong heen vallen. Stuur het resultaat naar de gelsimulatie met keuze uit 11 courante markers (o.a. DL2000 en 1 kb Ladder), agaroseconcentratie, spanning en looptijd; de bandposities volgen in de literatuur gevalideerde migratiemodellen, zodat je vooraf kunt inschatten of het verteringspatroon je doelfragment goed onderscheidt. Methyleringseffecten (Dam / Dcm / CpG) worden automatisch gecontroleerd.
- **Kloneringsworkflow-canvas**: bouw je experiment als een stroomdiagram — sequentiebron → primerontwerp / codonoptimalisatie → virtuele PCR → vertering / zuivering → assemblage → transformatie / kolonie-PCR / verificatie door sequencering → opslaan in de database — met in totaal 30 knooppunttypen waarvan de uitvoer **in realtime wordt herberekend** zodra je een invoer bovenstrooms wijzigt. Assemblagestrategieën: Gibson, Golden Gate (BsaI / BbsI / BpiI / SapI, met advies voor beschermende basen), T4-ligatie, TA / TOPO, Gateway LR / BP en BioBrick.
- **Molecuulbouw-canvas (bèta)**: ontwerp volgens het principe “kies een backbone en vul elementen in” — kies het backbone uit de vectorbibliotheek, vul de gaten met elementen en kies een assemblagemethode; de app genereert de linearisatiestrategie, alle primersequenties, de assemblage-opzet en adviezen voor kolonie-PCR-fragmenten en sequenceringsprimers. Het product mag alleen worden opgeslagen als het **base voor base** met het ontwerp overeenkomt.
- **Primerontwerp**: drie modi (amplificeer het geselecteerde gebied / zoek primers binnen de selectie / amplificeer vanuit de flanken) en meer dan 50 instelbare parameters; de Top20-kandidaten krijgen elk Tm, GC%, hairpin- en dimeerrisico's en een totale score op 100 punten. De **qPCR-wizard** maakt automatisch een splicing-alignment van mRNA tegen het genoom, tekent de exonstructuur en ontwerpt volgens een getrapte strategie — bij voorkeur primers over exongrenzen, daarna amplicons die een intron overspannen — zodat genomisch DNA de kwantificering niet verstoort; resultaten krijgen een MIQE-nalevingsscore en worden bij het opslaan aan het gen gekoppeld. Elk primerpaar is vooraf via in-silico PCR te controleren; de **primerbibliotheek** beheert primerparen in vier categorieën (qPCR / algemeen / klonering / detectie) met genkoppelingen, projectindeling, Excel-import/export en een wijzigingshistorie.
- **Sequenceringsanalyse**: bekijk AB1-bestanden in de chromatogramviewer met de fluorescentiesporen van de vier kanalen en de kwaliteitswaarden, en controleer ze base voor base tegen een referentie. Meerdere Sanger-reads worden automatisch geassembleerd (CAP3) tot een contig-consensus met dekkingsdiepte en waarschuwingen voor gebieden met lage kwaliteit. Bij de verificatie van recombinante vectoren worden reads teruggealigneerd op je vector — met automatische keuze van de beste strengrichting (ook over de oorsprong heen) — in een figuur “vectorelementen + readindeling” die per positie op overeenkomst kleurt, zodat mismatches, invoegingen en deleties direct zichtbaar zijn. Ook multiple sequence alignment (ClustalW) en fylogenetische bomen zijn beschikbaar.
- **Gelbeeldanalyse met AI**: open een gelfoto en een ingebouwd deep learning-model herkent automatisch banen en banden (handmatig toevoegen, verwijderen en verslepen mogelijk); na de keuze van de markerbaan, het laddertype en een referentieband met bekende DNA-hoeveelheid wordt automatisch een grootte-ijkcurve berekend en krijgt elke band een **fragmentgrootte en DNA-hoeveelheid** (geïntegreerde optische dichtheid). Export naar geannoteerde figuren (PNG / JPG / BMP / TIF) en JSON-resultaten.
- **Eiwitanalyse**: drie gekoppelde weergaven — topologieschema (transmembraangebieden, signaalpeptiden, secundaire structuur) ↔ aminozuursequentiepaneel ↔ 3D-structuur (automatisch opgehaald uit RCSB PDB / AlphaFold DB). Lokale analyses zijn binnen enkele seconden klaar (moleculargewicht, isoelektrisch punt, hydrofobiciteit, aminozuursamenstelling, subcellulaire lokalisatie met betrouwbaarheid, zeven klassen posttranslationele modificatieplaatsen, ongeordende gebieden, laag-complexiteitsgebieden, coiled-coils en antigenische segmenten); online worden de best scorende kandidaten aangeboden aan InterProScan-domeinscans en BLAST-homologiezoekopdrachten, die gevalideerde Swiss-Prot-annotaties overdragen (alleen aanvullen, met bronvermelding).
- **Laboratoriumgegevensbeheer**: vijf databases — vectordatabase (sjabloon- en recombinante vectoren, werkgroepen in twee niveaus), sequentiedatabase, primerdatabase, enzymdatabase (580+ restrictie-enzymen met herkenningssequenties, restrictiekaarten, type, uiteinden en temperatuurgegevens, plus eigen enzymen) en projectbeheer. Delen kan via een `.hcvec`-bestand of versleuteld binnen het LAN met een koppelingscode van 8 cijfers — de ontvanger vult alleen lege velden aan. Er zijn automatische back-ups bij het starten (5 worden bewaard), een handmatige volledige back-up als één ZIP, en verwijderen gebeurt pas nadat alle geraakte koppelingen zijn opgesomd zodat jij het bereik kiest.
- **Optionele AI-assistent**: werkt na configuratie van een willekeurige OpenAI-compatibele modeldienst (de API-sleutel blijft uitsluitend lokaal). De assistent kent je geopende genen / vectoren / vensters, kan pagina's wisselen, entiteiten opzoeken en gegevens aanpassen via exact hetzelfde (ongedaan te maken) pad als handmatig bewerken. Bij het parseren van kloonplannen als platte tekst extraheert de AI een gestructureerd plan (backbone, insert, enzymen, assemblagemethode), waarna de deterministische engine van de app primers en een experimentgids genereert — **de AI leest alleen tekst en produceert zelf nooit een base**. Zonder AI is elke functie volledig handmatig te gebruiken.

## Soortgegevens-plugins

Genannotaties en expressiegegevens worden aangeleverd via soortgegevens-plugins, die je in de instellingen kunt installeren, inschakelen en weer verwijderen. Het installatieprogramma bevat rijstannotatiegegevens (circa 100.000 items); verder zijn online bronnen per plugin beschikbaar:

- **Rijst (Rice)** — RAP-DB, MSU-RGAP, RiceData, RiceXPro: locusannotaties, exonstructuur, synoniemen, mutantfenotypen, spatiotemporele expressiekaarten (getallen + afbeeldingen), sequenties per versie en conversie van ID's tussen databases.
- **Ensembl Plants** — Ensembl Plants, EBI Expression Atlas: genen zoeken in meer dan 100 soorten, sequentiedownload, GO-annotaties en RNA-Seq-expressie.
- **Phytozome** — JGI Phytozome: genen zoeken, genmodellen, CDS- / cDNA- / eiwitsequenties, domeinen en homologe genen.
- **ePlant (BAR)** — BAR eFP Browser: gekleurde weefselexpressie-overzichten en expressieniveaus per weefsel voor 13 soorten.

Online opgevraagde annotaties, sequenties en afbeeldingen worden automatisch lokaal opgeslagen en worden daarna standaard uit de lokale cache gelezen (vernieuwen gaat handmatig), zodat alles ook offline te bekijken blijft. Zonder plugins kun je genen van elke soort bovendien rechtstreeks uit NCBI importeren.

## Gegevensveiligheid en privacy

- **Alle gegevens blijven lokaal**: er wordt niets naar servers geüpload; netwerkcontact is er alleen als je zelf online gegevens opvraagt (NCBI, soortdatabases, eiwitstructuurdatabases, software-updates).
- **AI is volledig optioneel**: de assistent werkt alleen met een eigen API-sleutel, die uitsluitend op je eigen computer wordt bewaard; zonder AI heeft elke functie een handmatig alternatief.
- **Samenvoegen in plaats van overschrijven**: voorbeeldgegevens installeren, datapakketten importeren en gegevens via het LAN ontvangen vullen alleen lege velden aan — je bestaande inhoud blijft onaangetast.

## Ondersteunde bestandsindelingen

| Richting | Indelingen |
|------|------|
| Openen / importeren | GenBank (`.gb` `.gbk`), FASTA (`.fasta` `.fa` `.faa`), SnapGene (`.dna`), EMBL (`.embl`), chromatogrammen (`.ab1`), primer-Excel (`.xlsx`), eiwitannotaties (UniProtKB / GFF3 / InterProScan / GenPept), eiwitstructuren (PDB / mmCIF), HelixCraft-pakketten (genpakket / `.hcvec`-vectorpakket / `.hcp`-eiwitpakket) |
| Opslaan / exporteren | GenBank, FASTA, SnapGene `.dna`, EMBL, kaartfiguren (SVG / PDF / PNG / JPG / BMP / TIF), geannoteerde gelfiguren, primer-Excel, eiwitannotaties in 6 indelingen, gendatapakket / `.hcvec` / `.hcp`, statische webpagina met gendetails, volledige back-up als ZIP |

## Interfacetalen

Alle functiemodules zijn sinds v0.3.7 volledig beschikbaar in 20 talen: 简体中文, English, 日本語, 한국어, Français, Deutsch, Español, Português, Русский, Italiano, العربية, हिन्दी, ไทย, Tiếng Việt, Bahasa Indonesia, Türkçe, Nederlands, Polski, Svenska, Čeština. Wisselen kan op elk moment via “Instellingen → Taal”; de eerste pagina van de installatiewizard biedt eveneens een taalkeuze. Vertaalde projectbeschrijvingen vind je via de talenbalk bovenaan.

## Over deze repository

Deze repository dient uitsluitend voor de **distributie van installatieprogramma's en het online-updatemanifest** en bevat geen broncode. De release op de tag `latest` is het online-updatekanaal (de bijbehorende bestanden worden bij elke versie vervangen); releases op `v<version>`-tags zijn historische archieven.

Dezelfde repository wordt synchroon bijgehouden op [GitHub](https://github.com/liudab/HelixCraft) en [GitCode](https://gitcode.com/BohanLab/HelixCraft); installatieprogramma's verschijnen aan beide kanten. De gegevensbron van “Controleren op updates” in de app is het GitHub `latest`-kanaal (downloads verlopen automatisch via mirrorservers voor versnelling).

## Licentie

[MIT](LICENSE)

## Contact

Bohan Liu @ BohanLab · liubohan@hunau.edu.cn
