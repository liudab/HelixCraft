# HelixCraft

**AI-powered gene engineering desktop software**

[简体中文](README.md) · **English**

HelixCraft is a desktop application for molecular biology and gene engineering research. It supports
the complete workflow from *finding a gene → reading sequences → designing clones → in-silico
assembly → experiment verification → data management*: vector map editing, sequence analysis,
primer design, restriction digestion and gel electrophoresis simulation, cloning workflows, Sanger
chromatogram analysis, species data lookup, protein analysis, and an optional AI assistant. All
data stays on your own computer — no account, no cloud dependency. The interface is available in
20 languages.

Typical scenarios:

- Open a plasmid file and see its features and restriction sites at a glance, then export a
  publication-quality map figure;
- Simulate a Gibson / Golden Gate / restriction-ligation plan end-to-end on the computer before
  setting up a single reaction;
- Design cloning primers or exon-junction-spanning qPCR primers with scoring and evaluation
  evidence;
- Review sequencing chromatograms, assemble reads, and align results back to your recombinant
  vector;
- Annotate and quantify lanes/bands on gel photos;
- Analyze a protein sequence for physicochemical properties, subcellular localization, PTM sites
  and 3D structure;
- Organize vectors, genes, primers and sequencing files per project, transfer them between lab
  computers, and back them up.

## Contents

[Download](#download) · [Installation](#installation) · [Auto-update](#auto-update) ·
[Feature overview](#feature-overview) · [Species data plugins](#species-data-plugins) ·
[Data safety & privacy](#data-safety--privacy) · [Supported file formats](#supported-file-formats)

## Download

The latest version is always published on the
[**Releases · `latest` channel**](releases/tag/latest):

| Platform | Installer | How to install |
|---|---|---|
| Windows 10 / 11 (x64) | `HelixCraft.Setup.<version>.exe` | Run the installer wizard |
| Debian / Ubuntu (x86_64) | `helixcraft_<version>_amd64.deb` | Double-click, or `sudo apt install ./<file>` |

The `latest` channel is also the data source of the in-app "check for updates"; its assets are
replaced on every release. Older versions are archived under their own
[release tags](releases).

### Verifying the download

`latest.json` in the same release is the update manifest used by the app. It lists every
installer's file name, size and SHA-256 digest, so you can verify the download is complete and
untampered:

```bash
# Linux
sha256sum helixcraft_<version>_amd64.deb
# Windows PowerShell
Get-FileHash .\HelixCraft.Setup.<version>.exe -Algorithm SHA256
```

## Installation

### Windows

- Requirements: Windows 10 or later (x64).
- Run `HelixCraft.Setup.<version>.exe` and follow the wizard (all-users install by default,
  administrator privileges required).
- The wizard offers an optional **sample data** component (sample vectors, cloning workflows and
  species data plugins) so new users can explore right away. Sample data is imported only when the
  corresponding content does not exist yet — **it never overwrites data you have created**.
- **Installing over an existing copy keeps all your data.** Data lives in `%APPDATA%\HelixCraft`
  (species sub-databases in `%APPDATA%\HelixCraftData`); uninstalling does not remove it.

### Linux (Debian / Ubuntu, x86_64)

- Double-clicking the `.deb` hands it to the system graphical installer (GNOME Software /
  App Center / KDE Discover / GDebi); the terminal equivalent is
  `sudo apt install ./helixcraft_<version>_amd64.deb`.
- The app installs to `/opt/HelixCraft`; user data lives in `~/.config/HelixCraft` and **is not
  removed on uninstall**.
- CJK fonts are recommended (the package declares `Recommends: fonts-noto-cjk`; installing with
  `dpkg -i` skips dependencies — use `apt install` instead).
- Dependencies are declared as alternatives such as `libgtk-3-0 | libgtk-3-0t64`, so the t64
  rename introduced in Ubuntu 24.04 does not break dependency resolution.
- No AppImage is provided.

### Opening files directly

After installation, double-clicking (or dragging onto the app window) opens files in HelixCraft:
GenBank (`.gb` `.gbk`), FASTA (`.fasta` `.fa`), SnapGene (`.dna`), EMBL (`.embl`) → sequence
editor; `.ab1` chromatograms → chromatogram viewer; protein sequences (`.faa` `.genpept`) and
protein packages (`.hcp`) → protein sequence/structure viewer; `.tif` gel images → gel image
analysis.

## Auto-update

About 20 seconds after launch the app checks for updates in the background (on by default, at most
once per 24 hours, can be disabled in settings). A new version is **announced only — nothing is
downloaded automatically**; downloads go over HTTPS with resume support and SHA-256 verification,
and installers failing verification are rejected. On Windows the NSIS wizard completes the
installation and restarts the app; on Linux the downloaded `.deb` is handed to the system software
installer, and if the system cannot launch one, the app shows the installer path with a "reveal in
folder" action.

## Feature overview

### Find and study a gene

- **Multiple ways to find genes**: search the local gene database; import by NCBI Gene ID /
  Accession; look up by species-database identifiers through plugins (rice RAP-DB / MSU / RiceData
  IDs, Ensembl Plants stable IDs, Phytozome gene IDs); import local GenBank / FASTA files or gene
  data packages shared by colleagues.
- **One detail page with everything**: annotations aggregated from species databases (alleles,
  mutant phenotypes, GO / InterPro, references); spatio-temporal expression (expression charts and
  tissue heatmaps); unified management of the gene's genomic / mRNA / CDS / protein sequences, with
  on-demand download from NCBI.
- Transcript variants open individually; protein sequences hand off to the protein structure
  viewer in one click. Duplicate entries can be merged; deletion lists affected data first and
  lets you choose the scope.

### Vector maps & sequence editing

- **Circular / linear map and sequence text, bidirectionally linked**: click the map to select the
  sequence, click the sequence to locate it on the map. Features are colored by type; restriction
  sites, primer binding positions, ORFs and mutation markers overlay on top. Map styling (colors,
  font sizes, legend, visibility) is fully customizable and exportable to SVG / PDF / PNG and more
  for publication figures.
- **Direct sequence editing**: type, delete and paste freely — feature coordinates adjust
  automatically after insertions/deletions. All sequence and feature operations support 50-step
  undo/redo.
- **Smart annotation**: the whole vector is compared against the component database to identify
  known elements (≥99% DNA identity or ≥90% translated match, with per-item preview before batch
  import), and the carrier's antibiotic resistance, host, promoter and reporter fields are inferred
  automatically (with confidence and evidence; existing values are never overwritten).
- **ORF prediction**: six-frame scanning (including ORFs spanning the origin of circular plasmids),
  results hover on the map, and translated products can be saved to the sequence database.
- **BLAST online search**: submit a selection to NCBI (blastn / blastp / blastx and other
  programs).
- **Amino-acid substitution design**: describe mutations as `G168A`; the app validates the original
  residue, picks the minimal-change synonymous codon and writes it back into the sequence.

### Digestion simulation & virtual electrophoresis

- Single / double / multi-enzyme digests give fragment lists in real time, correctly handling sites
  spanning the origin of circular plasmids.
- **Virtual gel electrophoresis**: send digest results to the gel simulation, choose a marker
  (DL2000, 1 kb Ladder and 9 other common ladders), agarose concentration, voltage and run time;
  band positions follow literature-calibrated migration models, so you can preview whether the
  diagnostic digest will separate your target band.
- Methylation effects (Dam / Dcm / CpG) are checked automatically, flagging sites blocked in
  common strains.
- **Restriction site assistant**: a wizard recommends candidate sites and a first choice when you
  are not sure where to clone.

### Designing cloning experiments (in-silico rehearsal)

- **Cloning workflow canvas**: wire the experiment up like a flowchart — sequence sources → primer
  design / codon optimization → virtual PCR → digest / purification → assembly → transformation /
  colony PCR / sequencing verification → save back to the database; 30 node types in total. Every
  node's output is **computed in real time**: change an upstream input and everything downstream
  re-simulates immediately. When the graph is complete you can inspect the full sequence of the
  final recombinant plasmid — a design counts only when it matches your expectation. Undo/redo,
  autosave and JSON import/export are supported.
- **Assembly strategies**: Gibson, Golden Gate (BsaI / BbsI / BpiI / SapI, with spacer-base
  recommendations), T4 ligation, TA / TOPO cloning, Gateway LR / BP, BioBrick.
- **Molecular build canvas (Beta)**: for "pick a backbone, drop in features" design — choose the
  backbone from the vector library, fill gaps with components, pick an assembly method, and the
  app generates the linearization strategy, all primer sequences, the assembly setup, expected
  colony-PCR fragments and sequencing-primer suggestions. **Delivery requires the compiled product
  to match your design base-for-base.**
- **Cloning system knowledge base**: a semantic model of cloning systems (vector compatibility and
  conversion paths) helps plan routes "from vector A to vector B".

### Primer design

- **General primer design**: three modes (amplify a selection / within a selection / from flanking
  regions); 50+ tunable parameters (Tm, GC, product length, 3′ stability, ...); top-20 candidates
  each with Tm, GC%, hairpin/dimer risk and a 100-point aggregate score.
- **Deep evaluation & human-in-the-loop**: false-priming sites, primer efficiency and stability
  profiles; when unsatisfied, just give feedback ("3′ end too stable", "Tm too low") and the app
  re-searches in a targeted way.
- **qPCR primer wizard**: automatically aligns mRNA against the genome, draws the exon structure,
  and designs in graded strategies — primers spanning exon junctions first, intron-spanning
  amplicons next — mechanistically avoiding genomic DNA interference. Results come with an MIQE
  compliance score and are linked to the gene on save.
- **In-silico PCR**: check expected product sizes and off-target amplification for any primer
  pair before ordering.
- **Primer database**: primer-pair management (qPCR / general / cloning / detection), gene links,
  project assignment, Excel import/export and an audit log of changes.

### Sequencing analysis

- **Chromatogram viewer**: open AB1 files to inspect the four-channel fluorescence traces and
  quality values, compare against a reference base by base. Manual corrections are possible — the
  instrument output remains authoritative and is never silently overwritten.
- **Read assembly**: multiple Sanger reads are assembled automatically (CAP3-style), producing
  contig consensus sequences with coverage depth and low-quality region hints; a finished contig
  can be sent straight to alignment.
- **Recombinant vector verification**: reads are aligned back onto your vector, automatically
  picking the better strand orientation (circular vectors spanning the origin included). A
  "vector features + read layout" diagram colors columns by conservation, making mismatches,
  insertions and deletions obvious. Multiple sequence alignment (ClustalW) and phylogenetic trees
  are also available.

### Gel image analysis

- **Three-step wizard**: open a gel photo → a built-in deep-learning model detects lanes and bands
  automatically (add/remove/drag to fine-tune) → quantitative analysis.
- **Quantitation**: after choosing the marker lane, ladder type and a reference band amount, a
  size calibration curve is fitted automatically, giving each band's **fragment size and DNA
  amount** (integrated optical density); label positions are draggable.
- **Export**: annotated analysis figures (PNG / JPG / BMP / TIF) and quantitation results as JSON.
  Editing annotations later automatically flags the quantitation as stale for recalculation.

### Protein analysis

- **Three linked views**: topology diagram (transmembrane regions, signal peptides, secondary
  structure cartoons) ↔ amino-acid sequence panel (multi-segment selection) ↔ 3D structure
  (fetched on demand from RCSB PDB / AlphaFold DB). Clicking any site or segment highlights both
  the sequence and the structure.
- **Local analysis in seconds**: molecular weight, isoelectric point, hydrophobicity, amino-acid
  composition; subcellular localization prediction (signal peptides, transmembrane regions, NLS,
  with compartment ranking and confidence); seven classes of PTM sites including phosphorylation,
  ubiquitination and glycosylation; disordered, low-complexity, coiled-coil and antigenic regions.
- **Online refinement**: top-scoring candidates are submitted to InterProScan domain scans and
  BLAST homology searches, transferring curated Swiss-Prot annotations onto your sequence
  (additions only, never overwriting local conclusions, with source labels).
- **Protein annotations**: import/export compatible with UniProtKB / GFF3 / InterProScan /
  GenPept and more; a protein package (`.hcp`) bundles sequence, structure, annotations and
  rendering settings into one shareable file.

### Laboratory data management

- **Five databases**: vector database (template / recombinant vectors, two-level work groups);
  sequence database (sequencing files, gene sequences and other sequences in one view, filterable
  by gene / project / vector / primer associations); primer database; enzyme database (580+
  restriction enzymes with recognition sequences, cut maps, types, ends and temperatures, plus
  custom enzymes); project manager (attach vectors / genes / primers / sequencing files per
  project).
- **Sharing**: an entire vector work group can be packed into one `.hcvec` file for colleagues,
  who preview item by item on import; two computers running HelixCraft on the same LAN can
  exchange data over an encrypted 8-digit-pairing-code channel — the receiver only fills in blank
  fields and never overwrites existing edits.
- **Backup & restore**: automatic backups on launch (5 kept), manual full backup (a single ZIP)
  and one-click restore.
- **Protected deletion**: deleting vectors / genes / primers lists all affected associations
  first; you choose the scope.

### AI assistant (optional)

- Works with any OpenAI-compatible model endpoint once configured (the API key stays on your
  machine): streaming chat, voice input, spoken replies and prompt polishing.
- **Aware of and able to operate the app**: it knows which gene / vector / window you have open
  and can switch pages, locate entities, query and modify data on request — modifications go
  through exactly the same path as manual edits and can be undone.
- **Cloning protocol text parsing**: paste a methods paragraph from a paper; the AI extracts a
  structured protocol (backbone, insert, enzymes, assembly method), and the app's deterministic
  engine then generates primers and an experiment guide — **the AI only reads the text and never
  produces a single base**.
- **Without an AI key, every feature has a fully manual path — the app remains complete.**

## Species data plugins

Gene annotations and expression data arrive via "species plugins", installable / toggleable in
settings. The installer bundles rice annotation data (~100k entries); more online sources are
available through plugins:

| Plugin | Data sources | What you get |
|------|-----------|--------------|
| Rice | RAP-DB, MSU-RGAP, RiceData, RiceXPro | locus annotations, exon structure, synonyms, mutant phenotypes, spatio-temporal expression charts (values + images), sequences in all versions, cross-database ID conversion |
| Ensembl Plants | Ensembl Plants, EBI Expression Atlas | gene search across 100+ species, sequence download, GO annotations, RNA-Seq expression |
| Phytozome | JGI Phytozome | gene search, gene models, CDS / cDNA / protein sequences, domains, homologs |
| ePlant (BAR) | BAR eFP Browser | colorized tissue-expression pictographs and per-tissue levels for 13 species |

Online-fetched annotations, sequences and images are saved locally automatically; afterwards the
local cache is read by default (refresh is manual), so everything remains viewable offline. Even
without plugins, genes of any species can be imported directly from NCBI.

## Data safety & privacy

- **All data stays local**: nothing is uploaded; network access happens only when you explicitly
  request online data (NCBI, species databases, protein structure repositories, software updates).
- **AI is fully optional**: the assistant requires your own API key, stored locally only.
- **Merges never overwrite**: installing sample data, importing packages and receiving LAN
  transfers only fill in blank fields — your existing content is untouched.

## Supported file formats

| Direction | Formats |
|------|------|
| Open / import | GenBank (`.gb` `.gbk`), FASTA (`.fasta` `.fa` `.faa`), SnapGene (`.dna`), EMBL (`.embl`), chromatograms (`.ab1`), primer Excel (`.xlsx`), protein annotations (UniProtKB / GFF3 / InterProScan / GenPept), protein structures (PDB / mmCIF), HelixCraft packages (gene package / `.hcvec` vector package / `.hcp` protein package) |
| Save / export | GenBank, FASTA, SnapGene `.dna`, EMBL, map figures (SVG / PDF / PNG / JPG / BMP / TIF), annotated gel figures, primer Excel, protein annotations in 6 formats, gene data package / `.hcvec` / `.hcp`, static gene detail web page, full backup ZIP |

## Interface languages

简体中文、English、日本語、한국어、Français、Deutsch、Español、Português、Русский、Italiano、
العربية、हिन्दी、ไทย、Tiếng Việt、Bahasa Indonesia、Türkçe、Nederlands、Polski、Svenska、Čeština.

## About this repository

This repository hosts **installers and the online update manifest only** — it does not contain the
application source code. The `latest` tag's release is the auto-update channel (assets replaced on
every version); `v<version>` tags are archived historical releases.

The repository is mirrored on [GitHub](https://github.com/liudab/HelixCraft) and
[GitCode](https://gitcode.com/BohanLab/HelixCraft) with installers published on both. The in-app
"check for updates" reads the GitHub `latest` channel (downloads go through acceleration mirrors
automatically).

## License

[MIT](LICENSE)

## Contact

Bohan Liu @ BohanLab · liubohan@hunau.edu.cn
