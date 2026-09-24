# HelixCraft

**Perangkat lunak desktop pendamping rekayasa genetika berbasis AI** · AI-powered gene engineering tools

[简体中文](README.md) · [English](README_EN.md) · [日本語](README_ja.md) · [한국어](README_ko.md) · [Français](README_fr.md) · [Deutsch](README_de.md) · [Español](README_es.md) · [Português](README_pt.md) · [Русский](README_ru.md) · [Italiano](README_it.md) · [العربية](README_ar.md) · [हिन्दी](README_hi.md) · [ไทย](README_th.md) · [Tiếng Việt](README_vi.md) · **Bahasa Indonesia** · [Türkçe](README_tr.md) · [Nederlands](README_nl.md) · [Polski](README_pl.md) · [Svenska](README_sv.md) · [Čeština](README_cs.md)

> HelixCraft adalah perangkat lunak desktop untuk penelitian biologi molekuler dan rekayasa genetika. Aplikasi ini menemani Anda menyelesaikan alur kerja lengkap "mencari gen → membaca sekuens → mendesain kloning → perakitan virtual → verifikasi eksperimen → manajemen data": penyuntingan peta vektor, analisis sekuens, desain primer, simulasi digesti enzim restriksi dan elektroforesis gel, alur kerja kloning, analisis kromatogram sekuensing, pencarian data spesies, analisis protein, serta asisten AI opsional. Seluruh data tersimpan di komputer Anda sendiri, tanpa perlu mendaftarkan akun dan tanpa ketergantungan pada awan. Antarmuka tersedia dalam 20 bahasa.
> Dokumen lengkap: [简体中文](README.md) · [English](README_EN.md)

## Apa yang bisa Anda lakukan dengan HelixCraft?

- Membuka file plasmid untuk melihat susunan elemen dan situs restriksi secara jelas, lalu mengekspor gambar peta berkualiasi publikasi ilmiah.
- Mensimulasikan rencana Gibson / Golden Gate / ligasi enzim restriksi secara menyeluruh di komputer sebelum menyiapkan reaksi apa pun.
- Mendesain primer kloning atau primer qPCR yang melintasi sambungan ekson, lengkap dengan skor dan dasar evaluasi untuk setiap desain.
- Melihat kromatogram sekuensing, merakit read, lalu menyejajarkan hasil sekuensing kembali ke vektor rekombinan untuk verifikasi.
- Melakukan anotasi dan analisis kuantitatif jalur/pita pada foto gel.
- Menganalisis sifat fisikokimia, lokalisasi subseluler, situs modifikasi, dan struktur tiga dimensi dari sebuah sekuens protein.
- Mengelola vektor, gen, primer, dan file sekuensing per topik penelitian, mentransfernya antar komputer laboratorium, dan mencadangkannya secara berkala.

## Unduh

Versi terbaru selalu dirilis di saluran [**Releases · latest**](releases/tag/latest):

| Platform | Paket instalasi | Cara pemasangan |
|---|---|---|
| Windows 10 / 11 (x64) | `HelixCraft.Setup.<version>.exe` | Klik ganda untuk menjalankan wizard pemasangan |
| Debian / Ubuntu (x86_64) | `helixcraft_<version>_amd64.deb` | Klik ganda untuk menyerahkannya ke penginstal grafis sistem, atau `sudo apt install ./<file>` |

Saluran `latest` sekaligus menjadi sumber data fungsi "periksa pembaruan" di dalam aplikasi; aset saluran ini diganti sepenuhnya pada setiap rilis. Versi-versi lama dapat dilihat di [daftar Releases](releases), setiap versi memiliki arsip tersendiri. Di direktori yang sama, `latest.json` adalah manifes pembaruan yang digunakan aplikasi, memuat nama file, jumlah byte, dan ringkasan SHA-256 setiap paket instalasi, sehingga dapat dipakai untuk memverifikasi bahwa unduhan lengkap dan tidak dimanipulasi.

## Instalasi

### Windows

- Jalankan `HelixCraft.Setup.<version>.exe` dan ikuti wizard pemasangan (secara bawaan memasang untuk semua pengguna, memerlukan hak administrator).
- Wizard menyediakan komponen opsional **data contoh** (vektor contoh, alur kerja kloning, dan plugin data spesies) agar pengguna baru dapat langsung mencoba; data contoh hanya diimpor bila konten terkait belum ada dan **tidak akan pernah menimpa data yang telah Anda buat**.
- **Memasang ulang di atas versi lama tetap mempertahankan seluruh data.** Direktori data adalah `%APPDATA%\HelixCraft` (sub-basis data spesies berada di `%APPDATA%\HelixCraftData`); proses uninstal tidak menghapusnya.

### Linux (Debian / Ubuntu, x86_64)

- Klik ganda file `.deb` untuk menyerahkannya ke penginstal grafis sistem; perintah setara di terminal: `sudo apt install ./helixcraft_<version>_amd64.deb`.
- Program terpasang di `/opt/HelixCraft`, data pengguna berada di `~/.config/HelixCraft`; **tidak dihapus saat uninstal**.
- Disarankan sistem telah memasang font CJK.

## Pembaruan daring

Sekitar 20 detik setelah aplikasi dijalankan, aplikasi memeriksa pembaruan di latar belakang (aktif secara bawaan, paling sering sekali dalam 24 jam, dapat dimatikan di pengaturan). Bila versi baru ditemukan, aplikasi hanya memberi tahu dan **tidak mengunduh secara otomatis**; unduhan sepenuhnya melalui HTTPS dengan dukungan lanjutan dari titik jeda serta verifikasi SHA-256, dan paket instalasi yang gagal verifikasi akan ditolak. Di Windows, pemasangan diselesaikan oleh wizard NSIS lalu aplikasi otomatis dimulai ulang; di Linux, file `.deb` yang telah diunduh diserahkan ke penginstal perangkat lunak sistem.

## Fitur utama

- **Peta vektor dan penyuntingan sekuens langsung**: peta sirkular / linier terhubung dua arah dengan teks sekuens — klik peta untuk memilih sekuens, klik sekuens untuk menemukan posisinya di peta; elemen diwarnai menurut jenisnya, dengan tampilan lapisan situs restriksi, posisi pengikatan primer, ORF, dan penanda mutasi; gaya peta (warna, ukuran huruf, legenda, tampil/sembunyi) dapat disesuaikan dengan bebas dan diekspor ke SVG / PDF untuk keperluan publikasi. Sekuens dapat disunting langsung — mengetik, menghapus, dan menempel semuanya bisa — dan koordinat elemen otomatis menyesuaikan setelah penyisipan/penghapusan; seluruh operasi sekuens dan elemen mendukung urungkan/ulangi hingga 50 langkah.
- **Anotasi cerdas**: seluruh sekuens vektor dibandingkan dengan basis data elemen untuk mengenali elemen yang sudah dikenal secara otomatis (hanya diakui bila kesesuaian DNA ≥99% atau kecocokan hasil terjemahan ≥90%, dengan pratinjau per item sebelum impor massal), sekaligus menyimpulkan otomatis bidang seperti resistensi antibiotik, inang, promoter, dan gen reporter vektor (disertai tingkat keyakinan dan bukti; informasi yang sudah ada tidak ditimpa).
- **Prediksi ORF dan pencarian BLAST daring**: pemindaian enam frame baca (termasuk ORF yang melintasi titik asal plasmid sirkular), hasilnya tampil pada peta dan produk terjemahannya dapat disimpan ke basis data sekuens; sekuens pilihan mana pun dapat dikirim ke NCBI (blastn / blastp / blastx dan sebagainya, lima jenis program).
- **Simulasi digesti enzim restriksi dan elektroforesis gel virtual**: digesti satu enzim / dua enzim / banyak enzim langsung menghasilkan daftar fragmen, termasuk penanganan yang benar untuk situs yang melintasi titik asal pada plasmid sirkular; hasil digesti dapat dikirim satu klik ke simulasi gel — pilih marker umum (DL2000, 1 kb Ladder, dan sembilan jenis lainnya), konsentrasi agarosa, tegangan, dan waktu elektroforesis; posisi pita dihitung dengan model migrasi yang terkalibrasi terhadap literatur, sehingga Anda dapat memperkirakan apakah digesti verifikasi dapat memisahkan pita target; pengaruh metilasi (Dam / Dcm / CpG) diperiksa secara otomatis; tersedia asisten yang merekomendasikan situs restriksi kandidat beserta pilihan utama saat Anda belum yakin memakai situs yang mana.
- **Kanvas alur kerja kloning**: rangkai eksperimen seperti menyusun diagram alur — sumber sekuens → desain primer / optimasi kodon → PCR virtual → digesti / pemurnian → perakitan → transformasi / koloni PCR / verifikasi sekuensing → simpan kembali ke basis data, dengan total 30 jenis node; keluaran setiap node **dihitung secara waktu nyata** — ubah masukan di hulu, seluruh langkah di hilir langsung disimulasikan ulang; setelah tersambung, Anda dapat melihat sekuens lengkap plasmid rekombinan akhir, dan desain baru dianggap selesai bila sesuai ekspektasi. Mendukung strategi perakitan Gibson, Golden Gate (BsaI / BbsI / BpiI / SapI, disertai saran basa pelindung), ligasi T4, kloning TA / TOPO, Gateway LR / BP, dan BioBrick, serta urungkan/ulangi, penyimpanan otomatis, dan impor/ekspor JSON.
- **Kanvas konstruksi molekuler (Beta)**: cocok untuk desain bergaya "pilih backbone, isi dengan elemen" — pilih backbone dari pustaka vektor, isi celah dengan elemen, pilih metode perakitan, dan perangkat lunak otomatis menghasilkan cara linearisasi, seluruh sekuens primer, campuran reaksi perakitan, fragmen verifikasi koloni PCR, serta saran primer sekuensing; produk hanya boleh disimpan ke pustaka bila **sesuai basa demi basa dengan desain**.
- **Desain primer umum dan qPCR**: tiga mode (amplifikasi rentang terpilih / mencari primer di dalam rentang terpilih / amplifikasi dari wilayah flanking), lebih dari 50 parameter yang dapat diatur (Tm, GC, panjang produk, stabilitas ujung 3′, dan lainnya); 20 kandidat teratas disertai Tm, GC%, risiko hairpin / dimer, dan skor gabungan berskala 100; wizard qPCR otomatis melakukan penyejajaran splicing antara mRNA dan genom serta menggambar struktur ekson, lalu mendesain secara berjenjang — mengutamakan primer yang melintasi sambungan ekson, kemudian amplikon yang melintasi intron — sehingga interferensi DNA genom terhadap kuantifikasi dicegah sejak mekanismenya; hasil disertai skor kepatuhan MIQE dan otomatis dikaitkan dengan gen saat disimpan; pasangan primer apa pun dapat diverifikasi lebih dahulu dengan PCR virtual (in silico); pustaka primer mengelola primer per pasangan (empat kategori: qPCR / umum / kloning / deteksi), mendukung keterkaitan gen, penugasan proyek, impor/ekspor Excel, dan audit riwayat perubahan.
- **Analisis hasil sekuensing**: penampil kromatogram membuka file AB1 untuk memeriksa puncak fluoresensi empat kanal beserta nilai kualitasnya dan menyejajarkannya basa demi basa dengan sekuens referensi; bila sekuens perlu dikoreksi secara manual, suntingan dapat diedit dan disimpan (keluaran instrumen sekuensing tetap menjadi acuan, algoritma tidak pernah diam-diam menimpanya); banyak read Sanger dirakit otomatis dengan algoritma CAP3, menghasilkan sekuens konsensus contig, kedalaman cakupan, dan penanda wilayah berkualitas rendah, contig yang selesai dapat langsung dikirim ke penyejajaran; verifikasi vektor rekombinan menyejajarkan read ke vektor Anda — otomatis memilih arah untai maju/mundur yang lebih baik (termasuk vektor sirkular yang melintasi titik asal) — dan menghasilkan diagram "elemen vektor + tata letak read" yang diwarnai menurut tingkat kesesuaian, sehingga ketidakcocokan / insersi / delesi terlihat sekilas; juga mendukung penyejajaran banyak sekuens (ClustalW) dan penyusunan pohon filogenetik.
- **Analisis citra gel dengan AI**: tiga langkah — buka foto gel → model deep learning bawaan mengenali jalur dan pita secara otomatis (dapat ditambah/dihapus/disetel dengan menyeret) → analisis kuantitatif; setelah memilih jalur marker dan jenis tangga markanya serta menetapkan kandungan pita referensi, perangkat lunak otomatis memasang kurva standar ukuran dan memberikan **ukuran fragmen serta kandungan DNA** setiap pita (metode densitas optik terintegrasi), posisi label dapat diseret; ekspor gambar analisis beranotasi (PNG / JPG / BMP / TIF) dan hasil kuantifikasi JSON; bila anotasi diubah di tengah jalan, perangkat lunak otomatis mengingatkan bahwa hasil kuantifikasi telah kedaluwarsa dan perlu dihitung ulang.
- **Analisis protein**: tiga tampilan terhubung — diagram topologi (domain transmembran, peptida sinyal, kartun struktur sekunder) ↔ panel sekuens asam amino (pemilihan multi-segmen) ↔ struktur tiga dimensi (otomatis dicari dari RCSB PDB / AlphaFold DB) — mengklik situs atau segmen mana pun akan menyorot sekuens dan struktur sekaligus; analisis lokal menghasilkan hasil dalam hitungan detik: berat molekul, titik isoelektrik, hidrofobisitas, komposisi asam amino; prediksi lokalisasi subseluler (peptida sinyal, domain transmembran, sinyal lokalisasi nukleus, dll., disertai peringkat kompartemen dan tingkat keyakinan); tujuh kelas situs modifikasi pasca-translasi seperti fosforilasi / ubiquitinasi / glikosilasi; serta wilayah tak teratur, wilayah kompleksitas rendah, coiled-coil, dan wilayah antigenik; penyempurnaan daring: kandidat dengan skor tertinggi otomatis dikirim untuk pemindaian domain InterProScan dan pencarian homologi BLAST, memindahkan anotasi Swiss-Prot yang telah terverifikasi ke sekuens Anda (hanya menambahkan, tidak menimpa kesimpulan lokal, dengan pencantuman sumber).
- **Manajemen data laboratorium**: lima basis data — pustaka vektor (vektor templat / vektor rekombinan, pengelompokan grup kerja dua tingkat), basis data sekuens (file sekuensing, sekuens gen, dan sekuens lainnya dalam satu tampilan terpadu, dapat difilter menurut keterkaitan gen / proyek / vektor / primer), pustaka primer, pustaka enzim (580+ enzim restriksi beserta sekuens pengenalan, peta pemotongan, jenis, jenis ujung, dan data suhu, dapat menambahkan enzim kustom), serta manajer proyek (mengaitkan vektor / gen / primer / file sekuensing per topik penelitian); berbagi data: seluruh grup kerja vektor dapat dikemas menjadi satu file `.hcvec` untuk dikirim ke rekan kerja, pihak penerima memeriksa pratinjau per item saat mengimpor; dua komputer yang menjalankan HelixCraft dalam satu jaringan lokal dapat bertukar data secara terenkripsi melalui kode pemasangan 8 digit, penerima hanya mengisi bidang yang kosong dan tidak menimpa suntingan yang sudah ada; pencadangan: cadangan otomatis saat aplikasi dimulai (menyimpan 5 salinan), pencadangan penuh manual (satu file ZIP), dan pemulihan sekali klik; penghapusan terlindungi: sebelum menghapus vektor / gen / primer, semua data terkait yang terdampak ditampilkan lebih dahulu, dan cakupan penghapusan ditentukan oleh Anda.
- **Asisten AI (opsional)**: dapat digunakan setelah mengonfigurasi antarmuka model besar apa pun yang kompatibel dengan OpenAI (API Key hanya disimpan di komputer Anda): obrolan streaming, masukan suara, pembacaan balasan, dan penyempurnaan prompt; AI mengetahui gen / vektor / jendela yang sedang Anda buka dan dapat berpindah halaman, menemukan entitas, serta mengkueri dan mengubah data sesuai permintaan — setiap perubahan melalui jalur yang sama persis dengan penyuntingan manual sehingga dapat diurungkan; tempelkan paragraf metode dari literatur atau deskripsi lisan, AI akan mengekstrak rencana terstruktur (backbone, fragmen sisipan, enzim, metode perakitan), kemudian mesin deterministik perangkat lunak menghasilkan primer dan panduan eksperimen — **AI hanya memahami teks dan tidak menghasilkan satu basa pun**; tanpa konfigurasi AI, semua fitur tetap memiliki jalur manual penuh dan perangkat lunak tetap dapat digunakan secara lengkap.

## Plugin data spesies

Anotasi gen dan data ekspresi disediakan melalui "plugin data spesies" yang dapat dipasang / diaktifkan / dilepas di halaman pengaturan. Paket instalasi sudah menyertakan data anotasi padi (sekitar 100 ribu entri); data yang diperoleh secara daring otomatis disimpan ke penyimpanan lokal, setelah itu secara bawaan dibaca dari cache lokal (baru terhubung kembali ke jaringan saat tombol penyegaran ditekan), sehingga tetap dapat dilihat saat luring:

- **Padi (Rice)** — RAP-DB, MSU-RGAP, RiceData, RiceXPro: anotasi lokus, struktur ekson, sinonim, fenotipe mutan, peta ekspresi spasial-temporal (angka + gambar), sekuens semua versi, dan konversi ID lintas basis data.
- **Ensembl Plants** — Ensembl Plants, EBI Expression Atlas: pencarian gen di 100+ spesies, unduhan sekuens, anotasi GO, dan ekspresi RNA-Seq.
- **Phytozome** — JGI Phytozome: pencarian gen, model gen, sekuens CDS / cDNA / protein, domain, dan gen homolog.
- **ePlant (BAR)** — BAR eFP Browser: piktograf berwarna ekspresi jaringan beserta tingkat ekspresi per jaringan untuk 13 spesies.

## Keamanan dan privasi data

- **Seluruh data tersimpan secara lokal**: tidak ada yang diunggah ke server mana pun; koneksi jaringan hanya terjadi saat Anda secara aktif meminta data daring (NCBI, basis data spesies, repositori struktur protein, pembaruan perangkat lunak).
- **AI sepenuhnya opsional**: asisten AI bersifat opsional dan API Key hanya disimpan di komputer sendiri; tanpa konfigurasi AI, semua fitur tetap memiliki jalur manual.
- **Hanya menambah, tidak menimpa**: pemasangan data contoh, impor paket data, maupun penerimaan transfer jaringan lokal semuanya hanya mengisi bidang yang masih kosong dan tidak menyentuh konten yang sudah Anda miliki.

## Format file yang didukung

| Arah | Format |
|------|------|
| Buka / impor | GenBank (`.gb` `.gbk`), FASTA (`.fasta` `.fa` `.faa`), SnapGene (`.dna`), EMBL (`.embl`), kromatogram (`.ab1`), Excel primer (`.xlsx`), anotasi protein (UniProtKB / GFF3 / InterProScan / GenPept), struktur protein (PDB / mmCIF), paket HelixCraft (paket gen / paket vektor `.hcvec` / paket protein `.hcp`) |
| Simpan / ekspor | GenBank, FASTA, SnapGene `.dna`, EMBL, gambar peta (SVG / PDF / PNG / JPG / BMP / TIF), gambar gel beranotasi, Excel primer, anotasi protein dalam 6 format, paket data gen / `.hcvec` / `.hcp`, halaman web statis detail gen, ZIP cadangan penuh |

## Bahasa antarmuka

Sejak v0.3.7, seluruh modul fitur telah mendukung penuh 20 bahasa: 简体中文, English, 日本語, 한국어, Français, Deutsch, Español, Português, Русский, Italiano, العربية, हिन्दी, ไทย, Tiếng Việt, Bahasa Indonesia, Türkçe, Nederlands, Polski, Svenska, Čeština. Bahasa dapat diganti kapan saja melalui "Pengaturan → Bahasa"; layar pertama wizard instalasi juga menawarkan pilihan bahasa antarmuka. Dokumen penjelasan dalam berbagai bahasa dapat dilihat pada bilah navigasi bahasa di bagian atas.

## Tentang repositori ini

Repositori ini hanya digunakan untuk **mendistribusikan paket instalasi dan manifes pembaruan daring**, tidak memuat kode sumber. Release pada tag `latest` adalah saluran pembaruan daring (asetnya diganti sepenuhnya pada setiap versi), sedangkan tag `v<version>` adalah arsip versi-versi lama. Repositori yang sama disinkronkan di [GitHub](https://github.com/liudab/HelixCraft) dan [GitCode](https://gitcode.com/BohanLab/HelixCraft); paket instalasi dirilis serentak di kedua tempat, dan sumber data fungsi "periksa pembaruan" dalam aplikasi adalah saluran `latest` di GitHub (unduhan otomatis melewati mirror percepatan).

## Lisensi

[MIT](LICENSE)

## Kontak

Bohan Liu @ BohanLab · liubohan@hunau.edu.cn
