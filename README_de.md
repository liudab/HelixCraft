# HelixCraft

**KI-gestützte Desktop-Software für Gentechnik** · AI-powered gene engineering tools

[简体中文](README.md) · [English](README_EN.md) · [日本語](README_ja.md) · [한국어](README_ko.md) · [Français](README_fr.md) · **Deutsch** · [Español](README_es.md) · [Português](README_pt.md) · [Русский](README_ru.md) · [Italiano](README_it.md) · [العربية](README_ar.md) · [हिन्दी](README_hi.md) · [ไทย](README_th.md) · [Tiếng Việt](README_vi.md) · [Bahasa Indonesia](README_id.md) · [Türkçe](README_tr.md) · [Nederlands](README_nl.md) · [Polski](README_pl.md) · [Svenska](README_sv.md) · [Čeština](README_cs.md)

> HelixCraft ist eine Desktop-Software für die Forschung in Molekularbiologie und Gentechnik. Sie deckt den vollständigen Arbeitsablauf ab — vom Auffinden von Genen über das Lesen von Sequenzen und das Planen von Klonierungen bis zur virtuellen Assembly, experimentellen Verifikation und Datenverwaltung: Vektorkarten-Editor, Sequenzanalyse, Primerdesign, Restriktionsverdau- und Gelelektrophorese-Simulation, Klonierungs-Workflows, Sequenzier-Chromatogramme, Proteinanalyse und ein optionaler KI-Assistent. Alle Daten bleiben lokal auf Ihrem eigenen Rechner — keine Registrierung, keine Cloud-Abhängigkeit; die Oberfläche ist in 20 Sprachen verfügbar.
> Vollständige Dokumentation: [简体中文](README.md) · [English](README_EN.md)

## Was Sie damit machen können

- Eine Plasmid-Datei öffnen und sich Elemente und Restriktionsschnittstellen auf einen Blick erschließen — und die Karte als Publikationsabbild exportieren;
- Gibson-, Golden-Gate- oder Restriktions-Ligations-Pläne vor dem Ansetzen der ersten Reaktion vollständig am Computer durchspielen;
- Klonierungs-Primer oder über Exongrenzen hinweggehende qPCR-Primer mit Bewertung und nachvollziehbarer Beurteilungsgrundlage entwerfen;
- Sequenzier-Chromatogramme sichten, Reads zusammenbauen und die Ergebnisse zur Kontrolle an den rekombinanten Vektor zurückalignieren;
- Gelfotos mit Spur- und Bandenannotationen versehen und quantitativ auswerten;
- von einer Proteinsequenz aus physikochemische Eigenschaften, subzelluläre Lokalisierung, Modifikationsstellen und 3D-Struktur analysieren;
- Vektoren, Gene, Primer und Sequenzierdateien projektbezogen verwalten, zwischen Laborrechnern übertragen und regelmäßig sichern.

## Download

Die neueste Version ist stets im [**Releases · `latest`-Kanal**](releases/tag/latest) verfügbar:

| Plattform | Installationspaket | Installation |
|---|---|---|
| Windows 10 / 11 (x64) | `HelixCraft.Setup.<version>.exe` | Installationsassistent per Doppelklick ausführen |
| Debian / Ubuntu (x86_64) | `helixcraft_<version>_amd64.deb` | Per Doppelklick an den grafischen System-Installer übergeben oder `sudo apt install ./<Datei>` |

Der `latest`-Kanal ist zugleich die Datenquelle der In-App-Funktion „Nach Updates suchen". Ältere Versionen finden Sie in der [Releases-Liste](releases). Die neben den Paketen liegende `latest.json` enthält Name, Größe und SHA-256-Prüfsumme jedes Installers und dient der Verifikation des Downloads.

## Installation

### Windows

- `HelixCraft.Setup.<version>.exe` per Doppelklick ausführen und dem Assistenten folgen (Standardinstallation für alle Benutzer, Administratorrechte erforderlich).
- Der Assistent bietet eine optionale **Beispieldaten**-Komponente (Beispielvektoren, Klonierungs-Workflows und Spezies-Daten-Plugins). Beispieldaten werden nur importiert, wenn die entsprechenden Inhalte noch nicht existieren — **bereits angelegte Daten werden nie überschrieben**.
- **Wird über eine bestehende Installation installiert, bleiben sämtliche Daten erhalten.** Das Datenverzeichnis ist `%APPDATA%\HelixCraft` (Spezies-Unterdatenbanken unter `%APPDATA%\HelixCraftData`); die Deinstallation entfernt es nicht.

### Linux (Debian / Ubuntu, x86_64)

- Ein Doppelklick auf die `.deb`-Datei übergibt sie an den grafischen System-Installer (GNOME Software / App Center / KDE Discover / GDebi); im Terminal: `sudo apt install ./helixcraft_<version>_amd64.deb`.
- Das Programm wird unter `/opt/HelixCraft` installiert, die Benutzerdaten liegen unter `~/.config/HelixCraft` und **bleiben bei der Deinstallation erhalten**.
- CJK-Schriftarten werden empfohlen (das Paket schlägt `fonts-noto-cjk` vor; mit `dpkg -i` werden Empfehlungen nicht mitinstalliert — bitte `apt install` verwenden).

## Online-Updates

Etwa 20 Sekunden nach dem Start prüft die Anwendung im Hintergrund auf neue Versionen (standardmäßig aktiviert, höchstens einmal pro 24 Stunden, in den Einstellungen abschaltbar). Gefundene Updates werden nur gemeldet und **nicht automatisch heruntergeladen**; der Download erfolgt über HTTPS mit fortsetzbaren Übertragungen und SHA-256-Prüfung. Unter Windows übernimmt der NSIS-Assistent die Installation inklusive automatischem Neustart; unter Linux wird die geladene `.deb`-Datei an den System-Paket-Installer übergeben.

## Hauptfunktionen

- **Vektorkarten und Sequenzbearbeitung**: ringförmige und lineare Karten bidirektional mit dem Sequenztext verknüpft; Elemente nach Typ eingefärbt, Schnittstellen, Primerbindungsstellen, ORFs und Mutationsmarker als Overlay; Kartenstil frei anpassbar, Export als SVG/PDF/PNG; direktes Bearbeiten der Sequenz mit 50 Schritten Undo/Redo.
- **Intelligente Annotation**: der Abgleich der vollen Vektorsequenz mit der Elementdatenbank erkennt bekannte Elemente (≥99 % DNA-Identität bzw. ≥90 % translationsbasierter Treffer); Antibiotikaresistenz, Wirt, Promotor, Reportergen u. a. werden mit Konfidenz und Beleg abgeleitet, ohne bestehende Angaben zu überschreiben.
- **ORF-Vorhersage und BLAST-Suche**: Sechs-Leserahmen-Scan (auch für ORFs, die bei ringförmigen Plasmiden über den Ursprung reichen); die Auswahl wird an NCBI übergeben (blastn/blastp/blastx u. a.).
- **Restriktionsverdau und virtuelle Gelelektrophorese**: Echtzeit-Fragmentlisten für Einzel-, Doppel- und Mehrfachverdaue (ringförmige Plasmide auch über den Ursprung korrekt); Gel-Simulation mit gängigen Markern (DL2000, 1-kb-Ladder u. a.), Agarosekonzentration, Spannung und Laufzeit; automatische Methylierungsprüfung (Dam/Dcm/CpG); Assistent für die Schnittstellenwahl.
- **Klonierungs-Workflow-Canvas**: das Experiment wie ein Flussdiagramm verdrahten — 30 Knotentypen von Sequenzquellen über Primerdesign/virtuelle PCR und Assembly bis zur Kolonie-PCR/Sequenzierung und Rückgabe in die Datenbank; jede Ausgabe wird **in Echtzeit berechnet**; Assembly-Strategien: Gibson, Golden Gate (BsaI/BbsI/BpiI/SapI, mit Schutzbasen-Empfehlung), T4-Ligation, TA/TOPO, Gateway LR/BP, BioBrick; abschließende Prüfung der vollen rekombinanten Plasmidsequenz.
- **Molecular-Build-Canvas (Beta)**: „Backbone wählen, Elemente einsetzen" — lineare Rekombination, sämtliche Primer, der Reaktionsansatz, Kolonie-PCR-Fragmente und Sequenzierprimer werden automatisch erzeugt; die Ablage verlangt basenweise Übereinstimmung von Design und Produkt.
- **Primerdesign**: allgemeines Design in drei Modi mit über 50 einstellbaren Parametern und Top-20-Kandidaten (Tm, GC-Gehalt, Haarnadel-/Dimer-Risiko, Gesamtscore); qPCR-Assistent mit automatischem Spleiß-Alignment (mRNA gegen Genom) und MIQE-Score; In-silico-PCR; Primerdatenbank (qPCR/allgemein/Klonierung/Detektion) mit Excel-Import/-Export.
- **Sequenzieranalyse**: AB1-Chromatogramme mit vier Fluoreszenzkanälen, Qualitätswerten und Basis-für-Basis-Abgleich; CAP3-Assembly mehrerer Sanger-Reads zu Kontigen; Verifikations-Alignment der Reads am rekombinanten Vektor (auch ringförmig), dazu ClustalW und phylogenetische Bäume.
- **KI-Gelbild-Analyse**: ein eingebautes Deep-Learning-Modell erkennt Spuren und Banden automatisch (manuell feinjustierbar); Quantifizierung von Fragmentgröße und DNA-Menge per integrierter optischer Dichte; Export annotierter Abbildungen und JSON-Ergebnisse.
- **Proteinanalyse**: Topologieschema, Sequenz und 3D-Struktur (RCSB PDB/AlphaFold DB) synchron gekoppelt; lokale Sofortanalyse von Molekulargewicht, pI, subzellulärer Lokalisierung und Modifikationsstellen; Online-Verfeinerung per InterProScan und BLAST.
- **Labor-Datenverwaltung**: fünf Datenbanken (Vektoren, Sequenzen, Primer, 580+ Restriktionsenzyme, Projekte); Arbeitsgruppen als `.hcvec` paketieren und teilen, verschlüsselter LAN-Austausch per 8-stelligem Kopplungscode, automatische Backups, Löschschutz mit Auflistung aller Betroffenheiten.
- **Optionaler KI-Assistent**: versteht Klonierungspläne als Text und bedient die Software über denselben Pfad wie manuelle Bearbeitung (rückgängig machbar) — die KI erzeugt nie Basensequenzen; **ohne KI-Konfiguration bleibt jede Funktion manuell vollständig nutzbar.**

## Spezies-Daten-Plugins

Genannotationen und Expressionsdaten werden über Spezies-Plugins angebunden, die in den Einstellungen installiert, aktiviert und entfernt werden können. Das Installationspaket enthält Reis-Annotationsdaten (ca. 100.000 Einträge); online abgerufene Annotationen, Sequenzen und Bilder werden automatisch lokal zwischengespeichert und bleiben offline verfügbar. Auch ohne Plugin können Gene jeder Spezies direkt über NCBI importiert werden.

| Plugin | Datenquellen | Inhalt |
|---|---|---|
| Reis | RAP-DB, MSU-RGAP, RiceData, RiceXPro | Locus-Annotationen, Exonstruktur, Synonyme, Mutantenphänotypen, Expressionskarten, Sequenzen aller Versionen, ID-Austausch zwischen Datenbanken |
| Ensembl Plants | Ensembl Plants, EBI Expression Atlas | Gensuche in über 100 Spezies, Sequenzdownload, GO-Annotationen, RNA-Seq-Expression |
| Phytozome | JGI Phytozome | Gensuche, Genmodelle, CDS-/cDNA-/Proteinsequenzen, Domänen, Homologe |
| ePlant (BAR) | BAR eFP Browser | farbige Gewebe-Expressionsbilder und Expressionswerte pro Gewebe für 13 Spezies |

## Datensicherheit und Datenschutz

- **Alle Daten werden lokal gespeichert**: nichts wird auf Server hochgeladen; Netzwerkzugriffe erfolgen nur, wenn Sie Online-Daten anfordern (NCBI, Speziesdatenbanken, Proteinstrukturen, Software-Updates).
- **KI ist vollständig optional**: der Assistent benötigt Ihren eigenen API-Schlüssel, der nur lokal gespeichert wird; ohne KI gibt es für jede Funktion einen manuellen Weg.
- **Zusammenführen überschreibt nie**: Beispieldaten, Datenpakete und LAN-Übertragungen füllen nur leere Felder und berühren bestehende Inhalte nicht.

## Unterstützte Dateiformate

| Richtung | Formate |
|---|---|
| Öffnen/Import | GenBank (`.gb` `.gbk`), FASTA (`.fasta` `.fa` `.faa`), SnapGene (`.dna`), EMBL (`.embl`), Chromatogramme (`.ab1`), Primer-Excel (`.xlsx`), Proteinannotationen (UniProtKB/GFF3/InterProScan/GenPept), Proteinstrukturen (PDB/mmCIF), HelixCraft-Pakete (Genpaket/`.hcvec`/`.hcp`) |
| Speichern/Export | GenBank, FASTA, SnapGene `.dna`, EMBL, Kartenabbildungen (SVG/PDF/PNG/JPG/BMP/TIF), annotierte Gelfiguren, Primer-Excel, Proteinannotationen in 6 Formaten, Genpaket/`.hcvec`/`.hcp`, statische Gen-Detailseite, vollständiges Backup als ZIP |

## Oberflächensprachen

Seit v0.3.7 sind alle Funktionsmodule vollständig in 20 Sprachen verfügbar: 简体中文, English, 日本語, 한국어, Français, Deutsch, Español, Português, Русский, Italiano, العربية, हिन्दी, ไทย, Tiếng Việt, Bahasa Indonesia, Türkçe, Nederlands, Polski, Svenska, Čeština — jederzeit umschaltbar unter „Einstellungen → Sprache".

## Über dieses Repository

Dieses Repository dient ausschließlich der **Verteilung der Installationspakete und des Online-Update-Manifests** und enthält keinen Quellcode. Der Release zum `latest`-Tag ist der Online-Update-Kanal; Releases zu `v<version>`-Tags sind historische Archive. Dasselbe Repository wird synchron auf [GitHub](https://github.com/liudab/HelixCraft) und [GitCode](https://gitcode.com/BohanLab/HelixCraft) gehostet; die Installationspakete erscheinen auf beiden Plattformen.

## Lizenz

[MIT](LICENSE)

## Kontakt

Bohan Liu @ BohanLab · liubohan@hunau.edu.cn
