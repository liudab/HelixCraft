# HelixCraft

**AI-driven skrivbordsmjukvara för genteknik** · AI-powered gene engineering tools

[简体中文](README.md) · [English](README_EN.md) · [日本語](README_ja.md) · [한국어](README_ko.md) · [Français](README_fr.md) · [Deutsch](README_de.md) · [Español](README_es.md) · [Português](README_pt.md) · [Русский](README_ru.md) · [Italiano](README_it.md) · [العربية](README_ar.md) · [हिन्दी](README_hi.md) · [ไทย](README_th.md) · [Tiếng Việt](README_vi.md) · [Bahasa Indonesia](README_id.md) · [Türkçe](README_tr.md) · [Nederlands](README_nl.md) · [Polski](README_pl.md) · **Svenska** · [Čeština](README_cs.md)

> HelixCraft är en skrivbordsapplikation för forskning inom molekylärbiologi och genteknik. Den täcker hela arbetsflödet — från att hitta en gen och läsa sekvenser till att designa kloneringar, göra virtuell assembly, verifiera experiment och hantera data: redigering av vektorkartor, sekvensanalys, primerdesign, simulering av restriktionsklyvning och gelelektrofores, kloningsarbetsflöden, analys av sekvenseringskromatogram, uppslag i artdata, proteinanalys och en valfri AI-assistent. All data lagras lokalt på din egen dator — inget konto behövs och inget moln krävs; gränssnittet finns på 20 språk.
> Fullständig dokumentation: [简体中文](README.md) · [English](README_EN.md)

## Vad du kan använda den till

- Öppna en plasmidfil och se dess komponenter och restriktionsklyvningsställen på en gång — och exportera kartan som publikationsklar figur;
- simulera en Gibson-, Golden Gate- eller restriktions-ligeringsplan fullständigt i datorn innan den första reaktionen sätts upp;
- designa kloningsprimrar eller qPCR-primrar som spänner över exongränser, med poängsättning och underlag för bedömning;
- granska sekvenseringskromatogram, sammanfoga reads och alignera resultaten tillbaka mot den rekombinanta vektorn för kontroll;
- annotera spår och band på gelfotografier och göra kvantitativa analyser;
- utgå från en proteinsekvens och analysera fysikalisk-kemiska egenskaper, subcellulär lokalisering, modifieringsställen och tredimensionell struktur;
- hantera vektorer, gener, primrar och sekvensfiler per projekt, överföra dem mellan datorer i laboratoriet och säkerhetskopiera regelbundet.

## Nedladdning

Den senaste versionen finns alltid i [**Releases · kanalen `latest`**](releases/tag/latest):

| Plattform | Installationspaket | Installation |
|---|---|---|
| Windows 10 / 11 (x64) | `HelixCraft.Setup.<version>.exe` | Kör installationsguiden genom att dubbelklicka |
| Debian / Ubuntu (x86_64) | `helixcraft_<version>_amd64.deb` | Dubbelklicka så övertar systemets grafiska installationsprogram, eller `sudo apt install ./<fil>` |

Kanalen `latest` är också datakällan för appens inbyggda ”sök efter uppdateringar”. Äldre versioner finns i [Releases-listan](releases), där varje version har ett eget arkiv. `latest.json` i samma katalog är uppdateringsmanifestet som appen använder; det listar varje installerares filnamn, storlek och SHA-256-kontrollsumma, så att du kan kontrollera att nedladdningen är komplett och oförändrad.

## Installation

### Windows

- `HelixCraft.Setup.<version>.exe` körs genom att dubbelklicka (kräver Windows 10 eller senare, x64); följ guiden — standardinstallation för alla användare, administratörsrättigheter krävs.
- Guiden erbjuder en valfri komponent med **exempeldata** (exempelvektorer, kloningsarbetsflöden och artdataplugin) så att nya användare kan komma igång direkt. Exempeldata importeras bara när motsvarande innehåll inte redan finns — **de skriver aldrig över data du själv har skapat**.
- **Installeras programmet över en befintlig installation bevaras alla data.** Datakatalogen är `%APPDATA%\HelixCraft` (artunderdatabaser ligger i `%APPDATA%\HelixCraftData`); avinstallationen tar inte bort den.

### Linux (Debian / Ubuntu, x86_64)

- Ett dubbelklick på `.deb`-filen lämnar den till systemets grafiska installationsprogram (GNOME Software / App Center / KDE Discover / GDebi); motsvarande terminalkommando är `sudo apt install ./helixcraft_<version>_amd64.deb`.
- Programmet installeras i `/opt/HelixCraft` och användardata ligger i `~/.config/HelixCraft` — **de tas inte bort vid avinstallation**.
- CJK-teckensnitt rekommenderas (paketet anger `Recommends: fonts-noto-cjk`; vid installation med `dpkg -i` följer rekommenderade paket inte med — använd `apt install` i stället).

## Automatiska uppdateringar

Cirka 20 sekunder efter start kontrollerar appen i bakgrunden om det finns en ny version (på som standard, högst en gång per 24 timmar, kan stängas av i inställningarna). En ny version **meddelas bara — inget laddas ner automatiskt**; nedladdningen sker över HTTPS med stöd för återupptagning och SHA-256-verifiering, och installationspaket som inte klarar kontrollen avvisas. På Windows sköts installationen av NSIS-guiden som startar om appen automatiskt; på Linux lämnas den nedladdade `.deb`-filen till systemets installationsprogram.

## Huvudfunktioner

- **Vektorkartor och sekvensredigering**: ringformad och linjär karta dubbelriktat länkad mot sekvenstexten — klicka i kartan för att välja sekvens, klicka i sekvensen för att hitta platsen i kartan; komponenter färgade efter typ, med klyvningsställen, primerbindningsställen, ORF:er och mutationsmarkörer som överlägg; kartstil (färger, teckenstorlekar, legend, synlighet) fritt anpassningsbar med export till SVG/PDF/PNG för publikationsfigurer; sekvensen redigeras direkt (skriva/radera/klistra in) och komponentkoordinater justeras automatiskt; alla sekvens- och komponentåtgärder har 50 steg ångra/gör om.
- **Intelligent annotering**: hela vektorsekvensen jämförs mot komponentdatabasen för att identifiera kända element (godkänt först vid ≥99 % DNA-identitet eller ≥90 % matchning i översättning, med förhandsgranskning post för post vid import), och fält som antibiotikaresistens, värdorganism, promotor och reportergen härleds automatiskt med konfidensgrad och belägg — befintliga uppgifter skrivs inte över.
- **ORF-förutsägelse och BLAST-sökning**: avsökning i sex läsramar (inklusive ORF:er som spänner över origo i ringformade plasmider), resultaten visas på kartan när muspekaren svävar över dem och translationsprodukter kan sparas i sekvensdatabasen; markerad sekvens skickas till NCBI (blastn/blastp/blastx med flera program).
- **Restriktionsklyvning och virtuell gelelektrofores**: fragmentlistor i realtid vid enkel-, dubbel- och multiplenzyklyvning (ställen över origo i ringformade plasmider hanteras korrekt); klyvningsresultatet skickas med ett klick till gelsimuleringen med val av markör (DL2000, 1 kb Ladder m.fl.), agaroskoncentration, spänning och körtid, och bandpositionerna följer litteraturkalibrerade migrationsmodeller så att du ser i förväg om det diagnostiska klyvningsmönstret kan separera målbandet; metyleringseffekter (Dam/Dcm/CpG) kontrolleras automatiskt och ställen som blockeras i vanliga stammar markeras; en guide rekommenderar kandidatställen och ett förstahandval när du är osäker var du ska klona.
- **Kloningsarbetsflödes-canvas**: koppla ihop experimentet som ett flödesschema — sekvenskällor → primerdesign/kodonoptimering → virtuell PCR → klyvning/rening → assembly → transformering/kolonie-PCR/sekvenseringsverifiering → spara tillbaka i databasen; 30 nodtyper. Varje nods utdata **beräknas i realtid**: ändras en uppströms indata simuleras allt nedströms omgående. När hela flödet är kopplat kan hela sekvensen av det slutliga rekombinanta plasmidet granskas — designen räknas som klar först när den stämmer med förväntan. Ångra/gör om, autosparande samt JSON-import/-export stöds. Assemblystrategier: Gibson, Golden Gate (BsaI/BbsI/BpiI/SapI, med rekommendationer om skyddsbaser), T4-ligering, TA/TOPO, Gateway LR/BP och BioBrick.
- **Molekylbyggnadscanvas (beta)**: för design enligt mallen ”välj ryggrad, fyll på komponenter” — välj ryggrad ur vektordatabasen, fyll luckorna med komponenter och välj assemblymetod; programmet genererar lineariseringsstrategi, alla primersekvenser, reaktionsuppsättning, förväntade kolonie-PCR-fragment och förslag på sekvenseringsprimrar. **Sparning tillåts bara när produkten stämmer bas för bas med designen.**
- **Primerdesign**: allmän design i tre lägen (amplifiera ett markerat område / hitta primrar inom det / amplifiera från flankerande sekvens) med över 50 justerbara parametrar (Tm, GC-halt, produktlängd, 3′-stabilitet m.m.); topp-20-kandidater var och en med Tm, GC-%, risk för hårnåls- och dimerbildning samt sammanvägd poäng på en 100-gradig skala; avancerad utvärdering (falska primerställen, primereffektivitet, inre stabilitetsprofiler) där du ger återkoppling i fritext (t.ex. ”3′-änden är för stabil”) och programmet söker om riktat; **qPCR-guide** med automatisk splissningsalignering av mRNA mot genomet, uppritad exonstruktur och graderade strategier — primrar över exongränser först, därefter ampliconer som spänner över ett intron — vilket mekaniskt undviker störning från genomiskt DNA i kvantifieringen, med MIQE-poäng och automatisk genkoppling vid sparning; **in silico-PCR** för alla primerpar (förväntad produktstorlek och icke-specifik amplifikation); **primerbibliotek** med parhantering (qPCR/allmän/kloning/detektion), genkoppling, projekttillhörighet, Excel-import/-export och spårbar ändringshistorik.
- **Sekvensanalys**: AB1-kromatogram med fyra fluoresenskanaler och kvalitetsvärden, jämförda bas för bas mot en referenssekvens; manuella korrigeringar är möjliga (instrumentets utdata förblir auktoritativt och skrivs aldrig tyst över). Flera Sanger-reads sammanfogas automatiskt (CAP3) till contiger med täckningsdjup och varningar för regioner med låg kvalitet; en färdig contig kan skickas direkt till alignering. Vid verifieringsalignering mot den rekombinanta vektorn väljs den bästa strandorienteringen automatiskt (även ringformade vektorer över origo), och en översiktsbild med vektorkomponenter och reads färgas efter överensstämmelse — mismatch, insättningar och bortfall syns direkt; även multippelalignering (ClustalW) och fylogenetiska träd ingår.
- **AI-analys av gelbilder**: trestegsguide — öppna gelfotot, en inbyggd djupinlärningsmodell identifierar spår och band automatiskt (lägg till/ta bort och dra för finjustering), därefter kvantitativ analys. Efter val av markörspår, ladertyp och mängden i ett referensband anpassas en storlekskalibreringskurva automatiskt, vilket ger varje bands **fragmentstorlek och DNA-mängd** (integrerad optisk densitet); annoteringarnas positioner kan dras. Export av annoterade analysbilder (PNG/JPG/BMP/TIF) och kvantifieringsresultat som JSON; ändras annoteringarna i efterhand flaggas resultatet automatiskt som inaktuellt.
- **Proteinanalys**: topologi (membranspannande regioner, signalpeptider, sekundärstruktur), aminosyresekvens och 3D-struktur (hämtas automatiskt från RCSB PDB/AlphaFold DB) är tre synkroniserade vyer — klickar du på en position eller ett segment markeras både sekvens och struktur. Lokala analyser på sekunder: molekylvikt, isoelektrisk punkt, hydrofobicitet, aminosyressammansättning, subcellulär lokalisering (med konfidens), sju klasser av posttranslationella modifieringsställen (fosforylering, ubiquitinylering, glykosylering m.fl.) samt ostrukturerade regioner, regioner med låg komplexitet, coiled-coils och antigena segment. Kandidater med högst poäng skickas automatiskt till InterProScan-domänskanning och BLAST-homologisökning, vilka överför kuraterade Swiss-Prot-annoteringar till din sekvens (lägger bara till, skriver aldrig över, med källhänvisning).
- **Laboratoriedatahantering**: fem databaser — vektorer (mall- och rekombinanta vektorer i arbetsgrupper med två nivåer), sekvenser (sekvensfiler, gener och övriga sekvenser i en vy, filtrerbara efter koppling till gen/projekt/vektor/primer), primrar, enzymer (580+ restriktionsenzymer med igenkänningssekvenser, klyvningskartor, typ, ändar och temperaturer — egna enzymer kan läggas till) samt projekt. En hel vektorarbetsgrupp kan packas som en `.hcvec`-fil till kollegor, som förhandsgranskar post för post vid import; två datorer med HelixCraft i samma nätverk kan utbyta data krypterat via en åttasiffrig kopplingskod — mottagaren fyller bara i tomma fält och skriver aldrig över befintliga redigeringar. Automatisk säkerhetskopiering vid start (5 sparas), manuell fullständig säkerhetskopiering (en enda ZIP) och återställning med ett klick; vid radering av vektorer/gener/primrar listas all berörd data först och du väljer omfattningen.
- **Valfri AI-assistent**: fungerar med valfri OpenAI-kompatibel modellendpoint när den konfigurerats (API-nyckeln sparas bara på din dator) — strömmande chatt, röststyrd inmatning, uppläst svar och förfining av prompter. Assistenten vet vilken gen/vektor/fönster du har öppet och kan byta sida, hitta poster samt fråga och ändra data på begäran — ändringar går exakt samma väg som manuell redigering och kan ångras. Klistra in en metodbeskrivning så extraherar AI:n en strukturerad kloningsplan (ryggrad, insert, enzymer, assemblymetod), varefter programmets deterministiska motor tar fram primrar och experimentguide — **AI:n läser bara texten och producerar aldrig en enda bas**. **Utan AI-konfiguration har alla funktioner en fullvärdig manuell väg.**

## Artdataplugin

Genannoteringar och expressionsdata ansluts via artdataplugin, som kan installeras, aktiveras och tas bort på inställningssidan. Installationspaketet innehåller redan risannoteringsdata (ca 100 000 poster). Annoteringar, sekvenser och bilder som hämtas online sparas automatiskt i den lokala cachen och läses därefter från den (uppdatering sker först när du själv klickar på uppdatera), så allt visas även offline. Även utan plugin kan gener från valfri art importeras direkt från NCBI.

| Plugin | Datakällor | Innehåll |
|---|---|---|
| Ris | RAP-DB, MSU-RGAP, RiceData, RiceXPro | locusannoteringar, exonstruktur, synonymer, mutantfenotyper, expressionskartor i tid och rum (värden + bilder), sekvenser i alla versioner, ID-översättning mellan databaser |
| Ensembl Plants | Ensembl Plants, EBI Expression Atlas | gensökning i över 100 arter, sekvensnedladdning, GO-annoteringar, RNA-Seq-expression |
| Phytozome | JGI Phytozome | gensökning, genmodeller, CDS-/cDNA-/proteinsekvenser, domäner, homologer |
| ePlant (BAR) | BAR eFP Browser | färgade uttryckspiktogram per vävnad och uttrycksvärden per vävnad för 13 arter |

## Datasäkerhet och integritet

- **All data lagras lokalt**: inget laddas upp till någon server; nätverksåtkomst sker bara när du själv begär onlinedata (NCBI, artdatabaser, proteinstrukturbibliotek och programuppdateringar).
- **AI är helt valfri**: assistenten kräver din egen API-nyckel, som bara sparas lokalt; utan AI finns för varje funktion en manuell väg.
- **Sammanfogning skriver aldrig över**: exempeldata, importerade datapaket och LAN-mottagning fyller bara i tomma fält och rör inte ditt befintliga innehåll.

## Filformat som stöds

| Riktning | Format |
|---|---|
| Öppna/importera | GenBank (`.gb` `.gbk`), FASTA (`.fasta` `.fa` `.faa`), SnapGene (`.dna`), EMBL (`.embl`), kromatogram (`.ab1`), primer-Excel (`.xlsx`), proteinannoteringar (UniProtKB/GFF3/InterProScan/GenPept), proteinstrukturer (PDB/mmCIF), HelixCraft-paket (genpaket/`.hcvec` vektorpaket/`.hcp` proteinpaket) |
| Spara/exportera | GenBank, FASTA, SnapGene `.dna`, EMBL, kartfigurer (SVG/PDF/PNG/JPG/BMP/TIF), annoterade gelfigurer, primer-Excel, proteinannoteringar i 6 format, genpaket/`.hcvec`/`.hcp`, statisk webbsida med gendetaljer, fullständig säkerhetskopia som ZIP |

## Gränssnittsspråk

Sedan v0.3.7 är alla funktionsmoduler fullständigt översatta till 20 språk: 简体中文, English, 日本語, 한국어, Français, Deutsch, Español, Português, Русский, Italiano, العربية, हिन्दी, ไทย, Tiếng Việt, Bahasa Indonesia, Türkçe, Nederlands, Polski, Svenska, Čeština. Byt språk när som helst under ”Inställningar → Språk”; installationsguidens första sida erbjuder också ett språkval.

## Om det här arkivet

Det här arkivet används endast för att **distribuera installationspaket och manifestet för onlineuppdateringar** och innehåller ingen källkod. Releasen för taggen `latest` är kanalen för onlineuppdateringar (tillgångarna ersätts i sin helhet vid varje ny version), och releaser under `v<version>`-taggar är historiska arkiv. Samma arkiv hålls synkroniserat på [GitHub](https://github.com/liudab/HelixCraft) och [GitCode](https://gitcode.com/BohanLab/HelixCraft); installationspaketen publiceras på båda platserna.

## Licens

[MIT](LICENSE)

## Kontakt

Bohan Liu @ BohanLab · liubohan@hunau.edu.cn
