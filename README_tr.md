# HelixCraft

**Yapay zekâ destekli gen mühendisliği yardımcı masaüstü yazılımı** · AI-powered gene engineering tools

[简体中文](README.md) · [English](README_EN.md) · [日本語](README_ja.md) · [한국어](README_ko.md) · [Français](README_fr.md) · [Deutsch](README_de.md) · [Español](README_es.md) · [Português](README_pt.md) · [Русский](README_ru.md) · [Italiano](README_it.md) · [العربية](README_ar.md) · [हिन्दी](README_hi.md) · [ไทย](README_th.md) · [Tiếng Việt](README_vi.md) · [Bahasa Indonesia](README_id.md) · **Türkçe** · [Nederlands](README_nl.md) · [Polski](README_pl.md) · [Svenska](README_sv.md) · [Čeština](README_cs.md)

> HelixCraft, moleküler biyoloji ve gen mühendisliği araştırmaları için geliştirilmiş bir masaüstü yazılımıdır. *Gen arama → sekans okuma → klonlama tasarımı → sanal birleştirme → deneysel doğrulama → veri yönetimi* biçimindeki iş akışının tamamını tek çatı altında toplar: vektör haritası düzenleme, sekans analizi, primer tasarımı, restriksiyon kesimi ve jel elektroforezi simülasyonu, klonlama iş akışları, Sanger kromatogram analizi, tür verisi sorgulama, protein analizi ve isteğe bağlı bir yapay zekâ asistanı. Tüm veriler kendi bilgisayarınızda saklanır; hesap kaydı gerekmez, bulut bağımlılığı yoktur. Arayüz 20 dilde kullanılabilir.
> Tam belgeler: [简体中文](README.md) · [English](README_EN.md)

## Neler yapabilirsiniz?

- Plazmit haritası dosyasını açıp bileşenleri ve restriksiyon sitelerini tek bakışta görebilir, tez ve makaleler için yayın kalitesinde harita görselleri dışa aktarabilirsiniz.
- Reaksiyonları kurmadan önce Gibson / Golden Gate / restriksiyon-ligasyon planlarını bilgisayarda baştan sona simüle edebilirsiniz.
- Klonlama primerlarını veya ekson birleşim noktalarından geçen qPCR nicel primerlarını puan ve değerlendirme gerekçeleriyle birlikte tasarlayabilirsiniz.
- Sanger kromatogramlarını inceleyebilir, okumaları birleştirebilir ve sonuçları rekombinant vektörünüze hizalayarak doğrulayabilirsiniz.
- Jel fotoğraflarında şerit (lane) ve bant (band) işaretlemesi yapıp nicel analiz çalıştırabilirsiniz.
- Bir protein sekansından yola çıkarak fizikokimyasal özellikleri, hücrealtı yerleşimi, modifikasyon sitelerini ve üç boyutlu yapısını inceleyebilirsiniz.
- Vektör, gen, primer ve sekans dosyalarını projeye göre yönetebilir, laboratuvar bilgisayarları arasında aktarabilir ve düzenli olarak yedekleyebilirsiniz.

## İndirme

En güncel sürüm her zaman [**Releases · latest kanalı**](releases/tag/latest) altında yayımlanır:

| Platform | Kurulum paketi | Kurulum yöntemi |
|---|---|---|
| Windows 10 / 11 (x64) | `HelixCraft.Setup.<version>.exe` | Çift tıklayarak kurulum sihirbazını çalıştırın |
| Debian / Ubuntu (x86_64) | `helixcraft_<version>_amd64.deb` | Çift tıklayıp sistem grafik yükleyicisine bırakın ya da `sudo apt install ./<dosya>` komutunu çalıştırın |

`latest` kanalı aynı zamanda uygulama içi "güncellemeleri denetle" işlevinin veri kaynağıdır; paketler her sürümde yenisiyle değiştirilir. Eski sürümler [Releases listesi](releases) altında, sürüm başına ayrı arşivler halinde bulunur. Aynı dizindeki `latest.json` uygulamanın kullandığı güncelleme manifestosudur; her kurulum paketinin dosya adını, bayt sayısını ve SHA-256 özetini listeler, böylece indirmenin eksiksiz ve değiştirilmemiş olduğunu doğrulayabilirsiniz.

## Kurulum

### Windows

- `HelixCraft.Setup.<version>.exe` dosyasını çift tıklatıp sihirbazın adımlarını izleyin (varsayılan olarak tüm kullanıcılar için kurulur, yönetici izni gerekir).
- Sihirbaz, yeni kullanıcıların hemen deneyebilmesi için isteğe bağlı bir **örnek veri** bileşeni sunar (örnek vektörler, klonlama iş akışları ve tür verisi eklentileri). Örnek veri yalnızca ilgili içerik henüz yoksa içe aktarılır; **halihazırda oluşturduğunuz verilerin üzerine asla yazmaz**.
- **Var olan kurulumun üzerine yükleme tüm verileri korur.** Veri dizini `%APPDATA%\HelixCraft` (tür alt veritabanları `%APPDATA%\HelixCraftData` içinde) şeklindedir; programı kaldırmak bu dizinleri silmez.

### Linux (Debian / Ubuntu, x86_64)

- `.deb` dosyasına çift tıklamak, onu sistemin grafik yükleyicisine (GNOME Software / App Center / KDE Discover / GDebi) devreder; terminalde karşılığı `sudo apt install ./helixcraft_<version>_amd64.deb` komutudur.
- Program `/opt/HelixCraft` altına kurulur, kullanıcı verileri `~/.config/HelixCraft` dizininde tutulur; **program kaldırıldığında bunlar silinmez**.
- Sistemde CJK yazı tiplerinin bulunması önerilir (paket `Recommends: fonts-noto-cjk` bildirimini içerir).

## Çevrimiçi güncelleme

Uygulama, açılıştan yaklaşık 20 saniye sonra arka planda güncellemeleri denetler (varsayılan olarak açıktır, 24 saatte en fazla bir kez, ayarlardan kapatılabilir). Yeni bir sürüm bulunduğunda yalnızca bildirilir, **otomatik indirme yapılmaz**. İndirme HTTPS üzerinden yürür, kesinti sonrasında kaldığı yerden devam eder ve SHA-256 ile doğrulanır; doğrulamayı geçemeyen paketler reddedilir. Windows'ta kurulumu NSIS sihirbazı tamamlayıp uygulamayı otomatik olarak yeniden başlatır; Linux'ta indirilen `.deb`, sistem yazılım yükleyicisine bırakılır.

## Temel özellikler

- **Vektör haritası ve sekans düzenleme**: Halkasal/doğrusal harita ile sekans metni çift yönlü bağlantılıdır; haritaya tıklayınca sekans seçilir, sekansa tıklayınca haritada ilgili konuma gidilir. Bileşenler türe göre renklendirilir; restriksiyon siteleri, primer bağlanma konumları, ORF'ler ve mutasyon işaretleri üst üste gösterilebilir. Harita stili (renkler, punto, gösterge, görünürlük) serbestçe özelleştirilebilir ve makale görseli olarak SVG / PDF / PNG vb. biçimlerde dışa aktarılabilir. Sekans, yazarak/silerek/yapıştırarak doğrudan düzenlenebilir; ekleme ve silme sonrasında bileşen koordinatları otomatik güncellenir. Sekans ve bileşen işlemlerinin tümü 50 adıma kadar geri al/yinele destekler.
- **Akıllı işaretleme**: Vektörün tüm sekansı bileşen veritabanıyla karşılaştırılarak bilinen bileşenler otomatik tanınır (tanıma için DNA özdeşliği ≥%99 veya çeviri eşleşmesi ≥%90 aranır; toplu içe aktarmadan önce tek tek önizlenip onaylanır) ve antibiyotik direnci, konakçı, promoter, rapor geni gibi alanlar güven düzeyi ve kanıt bilgisiyle otomatik çıkarılır. Mevcut bilgiler üzerine yazılmaz.
- **ORF tahmini ve BLAST çevrimiçi arama**: Altı okuma çerçevesinde tarama yapılır (halkasal plazmitlerde orijin üzerinden geçen ORF'ler dahil); ORF sonuçları harita üzerinde imleçle gezilip tıklanarak konumlandırılabilir, çeviri ürünleri sekans veritabanına kaydedilebilir. Seçili sekans NCBI'ye gönderilerek BLAST araması yapılabilir (blastn / blastp / blastx dahil beş program).
- **Restriksiyon kesimi simülasyonu ve sanal jel elektroforezi**: Tek/çift/çok enzimli kesimlerde parça listesi gerçek zamanlı üretilir; halkasal plazmitlerde orijin üzerinden geçen siteler de doğru işlenir. Kesim sonuçları tek tıkla jel simülasyonuna gönderilir; marker (DL2000, 1kb Ladder vb. 11 yaygın tip), agaroz konsantrasyonu, voltaj ve elektroforez süresi seçilerek bant konumları literatüre kalibre edilmiş göç modelleriyle öngörülür, böylece kesim doğrulamasının hedef bandı ayırıp ayıramayacağı önceden görülür. Dam / Dcm / CpG metilasyon etkisi otomatik denetlenir, yaygın suşlarda bloke olacak siteler bildirilir. Emin olamadığınızda **restriksiyon sitesi seçim asistanı**, aday siteleri ve önerilen ilk seçeneği sihirbaz biçiminde sunar.
- **Klonlama iş akışı tuvali**: Deneyi akış şeması gibi kurun — sekans kaynağı → primer tasarımı / kodon optimizasyonu → sanal PCR → kesim / saflaştırma → birleştirme (assembly) → transformasyon / koloni PCR / sekanslama doğrulaması → veritabanına kayıt; toplam 30 düğüm türü. Her düğümün çıktısı **gerçek zamanlı hesaplanır**: yukarı akıştaki bir girdiyi değiştirdiğinizde aşağı akış anında yeniden simüle edilir. Gibson, Golden Gate (BsaI / BbsI / BpiI / SapI, koruyucu baz önerileriyle), T4 ligasyonu, TA / TOPO klonlama, Gateway LR / BP ve BioBrick birleştirme stratejileri desteklenir; bağlantı tamamlandığında son rekombinant plazmidin tüm sekansı incelenebilir — tasarım, beklentinizle uyuştuğunda tamamlanmış sayılır. Geri al/yinele, otomatik kaydetme ve JSON içe/dışa aktarma desteklenir.
- **Moleküler yapı tuvali (Beta)**: "İskeleti seç, bileşenleri yerleştir" tarzı tasarımlar içindir — vektör kütüphanesinden iskeleti seçin, boşluklara bileşenleri ekleyin, birleştirme yöntemini seçin; yazılım lineerleştirme stratejisini, tüm primer sekanslarını, birleştirme reaksiyon kurulumunu, koloni PCR doğrulama parçalarını ve sekanslama primer önerilerini otomatik üretir. Ürün, tasarımla **baz bazına uyuşmadıkça veritabanına kabul edilmez**.
- **Primer tasarımı**: Genel primer tasarımı üç mod sunar (seçili bölgeyi çoğaltma / seçili bölge içinde arama / flank bölgelerinden çoğaltma); Tm, GC, ürün uzunluğu, 3′ uç kararlılığı gibi 50'den fazla parametre ayarlanabilir. En iyi 20 aday, her biri için Tm, GC%, saç tokası / dimer riski ve 100 üzerinden genel puanla birlikte listelenir. Sonuçlardan memnun kalmadığınızda görüşünüzü yazarsınız ("3′ uç fazla kararlı", "Tm düşük" gibi), yazılım geri bildirimi çözümleyip hedefli bir yeniden arama yapar. **qPCR nicel primer sihirbazı**, mRNA ile genomun splisaj hizalamasını otomatik yapar, ekson yapısını çıkarır ve kademeli stratejiyle tasarlar — öncelik, primerların ekson birleşim noktalarından geçmesi; ardından amplikonun bir intronu kapsaması — böylece genomik DNA bulaşmasının nicellemeyi bozması ilke düzeyinde önlenir; sonuçlar MIQE uyumluluk puanıyla gelir, kaydedilirken genle otomatik ilişkilendirilir. Herhangi bir primer çifti, sipariş vermeden önce **sanal PCR** ile sınanabilir: beklenen ürün boyutu ve spesifik olmayan çoğalma olup olmadığı görülür. Tasarlanan primerlar **primer veritabanında** çift bazında yönetilir (qPCR / genel / klonlama / tespit); gen ilişkilendirme, proje ataması, Excel içe/dışa aktarma ve değişiklik geçmişi denetimi desteklenir.
- **Sekanslama sonuçlarının analizi**: AB1 dosyaları, dört kanallı floresan pikleri ve kalite değerleriyle açılır; referans sekansla baz bazına karşılaştırma yapılabilir. Çok sayıda Sanger okuması CAP3 algoritmasıyla otomatik olarak örtüştürülerek birleştirilir; kontig konsensüs sekansı, kapsama derinliği ve düşük kaliteli bölge uyarılarıyla üretilir, hazır kontig tek tıkla hizalamaya gönderilebilir. **Rekombinant vektör doğrulaması**: okumalar vektörünüze eşlenir, artı/eksi iplikten daha iyi yön otomatik seçilir (orijin üzerinden geçen halkasal vektörler dahil) ve "vektör bileşenleri + okuma dizilimi" şeması özdeşlik derecesine göre renklendirilir — uyumsuzluk / ekleme / silme tek bakışta seçilir. ClustalW ile çoklu dizilim hizalaması ve filogenetik ağaç oluşturma da desteklenir.
- **Jel görüntüsü analizi (AI destekli)**: Üç adımlı sihirbaz — jel fotoğrafını açın, yerleşik derin öğrenme modeli şeritleri ve bantları otomatik tanısın (elle ekleme/çıkarma ve sürükleyerek ince ayar yapılabilir), nicel analize geçin. Marker şeridi ile merdiven tipi ve bir referans bandın miktarı belirtildikten sonra boyut kalibrasyon eğrisi otomatik uydurulur; her bandın **parça boyutu ve DNA miktarı** (tümleşik optik yoğunluk yöntemi) verilir, etiket konumları sürüklenerek ayarlanabilir. Etiketli analiz görselleri (PNG / JPG / BMP / TIF) ve JSON nicel sonuçlar dışa aktarılır.
- **Protein analizi**: Topoloji şeması (transmembran bölgeler, sinyal peptitleri, ikincil yapı karikatürleri) ↔ amino asit dizisi paneli (çok bölgeli seçim) ↔ üç boyutlu yapı (RCSB PDB / AlphaFold DB'den otomatik yüklenir) üçlü görünümü eşgüdümlü çalışır; herhangi bir konuma veya bölgeye tıklandığında dizi ve yapı birlikte vurgulanır. Yerel analiz saniyeler içinde sonuç verir: moleküler ağırlık, izoelektrik nokta, hidrofobisite, amino asit bileşimi; hücrealtı yerleşim tahmini (sinyal peptidi, transmembran bölge, nükleer yerleşim sinyali vb., hücre bölmesi sıralaması ve güven değerleriyle); fosforilasyon / ubikuitinasyon / glikozilasyon dahil yedi sınıf translasyon sonrası modifikasyon sitesi; düzensiz bölgeler, düşük karmaşıklık bölgeleri, koil-koil ve antijenik bölgeler. En yüksek puanlı aday siteler, otomatik olarak InterProScan alan taramasına ve BLAST homoloji aramasına gönderilir; Swiss-Prot'teki doğrulanmış açıklamalar dizinize aktarılır (yalnızca eklenir, yerel sonuçlar üzerine yazılmaz, kaynak belirtilir).
- **Laboratuvar veri yönetimi**: Beş veritabanı — vektör kütüphanesi (şablon / rekombinant vektörler, iki düzeyli çalışma grubu gruplandırması), sekans veritabanı (sekanslama dosyaları, gen sekansları ve diğer sekanslar tek görünümde; gen / proje / vektör / primer ilişkilerine göre filtrelenebilir), primer veritabanı, enzim veritabanı (580+ restriksiyon enzimi için tanıma sekansları, kesim haritaları, tipler, uçlar ve sıcaklık bilgileri; özel enzim tanımlanabilir) ve proje yöneticisi (konu başına vektör / gen / primer / sekans dosyası iliştirme). Veri paylaşımı: tüm vektör çalışma grubu tek `.hcvec` dosyasına paketlenip gönderilebilir, karşı taraf içe aktarırken kayıtları tek tek önizler; aynı yerel ağdaki HelixCraft'li iki bilgisayar, 8 haneli eşleştirme koduyla şifreli kanal üzerinden veri alışverişi yapabilir, alıcı yalnızca boş alanları doldurur. Otomatik yedekleme (5 kopya saklanır), elle tam yedekleme (tek ZIP) ve tek tıkla geri yükleme; silmeden önce etkilenen tüm ilişkili veriler listelenir, kapsamı siz belirlersiniz.
- **Yapay zekâ asistanı (isteğe bağlı)**: OpenAI uyumlu herhangi bir büyük dil modeli arayüzü yapılandırıldığında kullanılabilir (API anahtarı yalnızca yerelde saklanır): akışkan sohbet, sesli giriş, yanıtların seslendirilmesi, istem (prompt) cilalama. Yapay zekâ, o an açık olan gen / vektör / pencereyi bilir; sayfa değiştirebilir, varlık bulabilir, veri sorgulayıp değiştirebilir — değişiklikler elle düzenlemeyle birebir aynı yoldan geçer ve geri alınabilir. Literatürdeki yöntem paragrafını veya sözlü tarifi yapıştırın; AI bunu yapılandırılmış bir klonlama planına (iskelet, eklenecek parça, enzimler, birleştirme yöntemi) dönüştürür, ardından yazılımın deterministik motoru primerları ve deney kılavuzunu üretir — **AI yalnızca metni anlamakla görevlidir, tek bir baz bile üretmez**. AI yapılandırılmasa bile tüm işlevlerin tamamen manuel yolları vardır, yazılım eksiksiz kullanılabilir.

## Tür verisi eklentileri

Gen açıklamaları (anotasyon) ve ekspresyon verileri "tür verisi eklentileri" aracılığıyla alınır; eklentiler ayarlar sayfasından kurulabilir / etkinleştirilebilir / kaldırılabilir. Kurulum paketi pirinç anotasyon verisini (~100 bin kayıt) içerir; çevrimiçi kaynaklardan alınan açıklamalar, sekanslar ve görseller otomatik olarak yerel önbelleğe kaydedilir, sonrasında varsayılan olarak yerel önbellek okunur (yalnızca yenile dendiğinde yeniden ağa çıkılır), böylece çevrimdışıyken de görüntülenebilir. Eklenti kurulmasa bile NCBI'den herhangi bir türün geni doğrudan içe aktarılabilir.

| Eklenti | Kapsanan veri kaynakları | Neler elde edersiniz |
|------|-----------|--------------|
| Pirinç (Rice) | RAP-DB, MSU-RGAP, RiceData, RiceXPro | Lokus açıklamaları, ekson yapısı, eş anlamlılar, mutant fenotipleri, uzay-zaman ekspresyon haritaları (sayısal değer + görsel), sürümlere göre sekanslar, veritabanları arası kimlik (ID) dönüşümü |
| Ensembl Plants | Ensembl Plants, EBI Expression Atlas | 100'den fazla türde gen arama, sekans indirme, GO açıklamaları, RNA-Seq ekspresyon verileri |
| Phytozome | JGI Phytozome | Gen arama, gen modelleri, CDS / cDNA / protein sekansları, protein alanları (domain), homolog genler |
| ePlant (BAR) | BAR eFP Browser | 13 tür için doku ekspresyonunu gösteren renkli piktografiler ve doku bazında ekspresyon düzeyleri |

## Veri güvenliği ve gizlilik

- **Tüm veriler yerelde saklanır**: Hiçbir veri sunucuya yüklenmez; ağ bağlantısı yalnızca siz çevrimiçi veri (NCBI, tür veritabanları, protein yapı depoları, yazılım güncellemeleri) talep ettiğinde gerçekleşir.
- **Yapay zekâ tamamen isteğe bağlıdır**: AI asistanı ek bir işlevdir; API anahtarı yalnızca yerelde saklanır. AI yapılandırılmadığında tüm işlevlerin manuel yolları vardır.
- **Birleştirme üzerine yazmaz**: Örnek veri kurulumu, veri paketi içe aktarma ve yerel ağ üzerinden alma işlemleri yalnızca boş alanları doldurur; mevcut içeriğinize dokunulmaz.

## Desteklenen dosya biçimleri

| Yön | Biçimler |
|------|------|
| Açma / içe aktarma | GenBank (`.gb` `.gbk`), FASTA (`.fasta` `.fa` `.faa`), SnapGene (`.dna`), EMBL (`.embl`), sekanslama kromatogramları (`.ab1`), primer Excel (`.xlsx`), protein açıklamaları (UniProtKB / GFF3 / InterProScan / GenPept), protein yapıları (PDB / mmCIF), HelixCraft paketleri (gen paketi / `.hcvec` vektör paketi / `.hcp` protein paketi) |
| Kaydetme / dışa aktarma | GenBank, FASTA, SnapGene `.dna`, EMBL, harita görselleri (SVG / PDF / PNG / JPG / BMP / TIF), açıklamalı jel görselleri, primer Excel, altı biçimde protein açıklaması, gen veri paketi / `.hcvec` / `.hcp`, gen ayrıntısı statik web sayfası, tam yedek ZIP |

## Arayüz dilleri

v0.3.7 sürümünden bu yana tüm işlev modülleri 20 dilde eksiksiz desteklenmektedir: 简体中文, English, 日本語, 한국어, Français, Deutsch, Español, Português, Русский, Italiano, العربية, हिन्दी, ไทย, Tiếng Việt, Bahasa Indonesia, Türkçe, Nederlands, Polski, Svenska, Čeština. Dil, "Ayarlar → Dil" bölümünden istediğiniz an değiştirilebilir.

## Bu depo hakkında

Bu depo yalnızca **kurulum paketlerini ve çevrimiçi güncelleme manifestosunu dağıtmak** için vardır; uygulamanın kaynak kodunu içermez. `latest` etiketli Release, çevrimiçi güncelleme kanalıdır (paketler her sürümde yenisiyle değiştirilir); `v<version>` etiketli Release'ler geçmiş sürümlerin arşivleridir. Aynı depo [GitHub](https://github.com/liudab/HelixCraft) ve [GitCode](https://gitcode.com/BohanLab/HelixCraft) üzerinde eşzamanlı olarak barındırılır; kurulum paketleri her iki tarafta da yayımlanır.

## Lisans

[MIT](LICENSE)

## İletişim

Bohan Liu @ BohanLab · liubohan@hunau.edu.cn
