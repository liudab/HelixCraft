# HelixCraft

**Komputerowe oprogramowanie do inżynierii genetycznej wspomagane sztuczną inteligencją** · AI-powered gene engineering tools

[简体中文](README.md) · [English](README_EN.md) · [日本語](README_ja.md) · [한국어](README_ko.md) · [Français](README_fr.md) · [Deutsch](README_de.md) · [Español](README_es.md) · [Português](README_pt.md) · [Русский](README_ru.md) · [Italiano](README_it.md) · [العربية](README_ar.md) · [हिन्दी](README_hi.md) · [ไทย](README_th.md) · [Tiếng Việt](README_vi.md) · [Bahasa Indonesia](README_id.md) · [Türkçe](README_tr.md) · [Nederlands](README_nl.md) · **Polski** · [Svenska](README_sv.md) · [Čeština](README_cs.md)

> HelixCraft to aplikacja komputerowa dla badań nad biologią molekularną i inżynierią genetyczną. Obejmuje kompletny przebieg pracy: wyszukanie genu → odczyt sekwencji → zaprojektowanie klonowania → wirtualne (in silico) składanie konstruktów → weryfikacja eksperymentalna → zarządzanie danymi. Oferuje edycję map wektorów, analizę sekwencji, projektowanie starterów, symulację trawienia restrykcyjnego i elektroforezy w żelu, przepływy pracy klonowania, analizę chromatogramów sekwencjonowania, przeglądanie danych gatunkowych, analizę białek oraz opcjonalnego asystenta AI. Wszystkie dane pozostają na twoim komputerze — bez zakładania konta i bez zależności od chmury. Interfejs jest dostępny w 20 językach.
> Pełna dokumentacja: [简体中文](README.md) · [English](README_EN.md)

## Co możesz z nim robić

- Otworzyć plik plazmidu i od razu zobaczyć jego elementy oraz miejsca restrykcyjne, a następnie wyeksportować mapę jako ilustrację do publikacji;
- przetestować na komputerze cały plan Gibson / Golden Gate / trawienia z ligacją, zanim zestawisz pierwszą reakcję;
- zaprojektować startery do klonowania lub startery qPCR obejmujące granice egzonów, z oceną punktową i łatwymi do prześledzenia podstawami oceny;
- przejrzeć chromatogramy sekwencjonowania, złożyć odczyty i dla kontroli zmapować wyniki z powrotem na wektor rekombinowany;
- opisać ścieżki i prążki na zdjęciach żeli oraz wykonać analizę ilościową;
- przeanalizować sekwencję białka pod kątem właściwości fizykochemicznych, lokalizacji subkomórkowej, miejsc modyfikacji i struktury przestrzennej;
- prowadzić rejestry wektorów, genów, starterów i plików sekwencjonowania w podziale na projekty, przesyłać je między komputerami laboratorium i regularnie wykonywać kopie zapasowe.

## Pobieranie

Najnowsza wersja jest zawsze dostępna w kanale [**Releases · `latest`**](releases/tag/latest):

| Platforma | Pakiet instalacyjny | Sposób instalacji |
|---|---|---|
| Windows 10 / 11 (x64) | `HelixCraft.Setup.<version>.exe` | Dwuklik uruchamia kreatora instalacji |
| Debian / Ubuntu (x86_64) | `helixcraft_<version>_amd64.deb` | Dwuklik przekazuje plik graficznemu instalatorowi systemu albo polecenie `sudo apt install ./<plik>` |

Kanał `latest` jest jednocześnie źródłem danych dla funkcji „Sprawdź aktualizacje” w aplikacji, a jego zasoby są zastępowane przy każdym wydaniu. Starsze wersje znajdziesz na [liście wydań](releases) — każde z nich ma osobne archiwum. Leżący w tym samym miejscu plik `latest.json` zawiera nazwę, rozmiar i sumę kontrolną SHA-256 każdego pakietu, co pozwala sprawdzić, czy pobrany plik jest kompletny i niezmodyfikowany.

## Instalacja

### Windows

- Uruchom `HelixCraft.Setup.<version>.exe` dwuklikiem i przejdź przez kreatora instalacji (domyślnie instalacja dla wszystkich użytkowników, wymagane uprawnienia administratora).
- Kreator oferuje opcjonalny komponent **danych przykładowych** (przykładowe wektory, przepływy pracy klonowania i wtyczki danych gatunkowych), aby nowi użytkownicy mogli od razu wypróbować program; dane przykładowe są importowane tylko wtedy, gdy dane treści jeszcze nie istnieją — **nigdy nie nadpisują utworzonych przez ciebie danych**.
- **Instalacja „na istniejącą wersję” zachowuje wszystkie dane.** Katalog danych to `%APPDATA%\HelixCraft` (podbazy danych gatunkowych znajdują się w `%APPDATA%\HelixCraftData`); odinstalowanie programu nie usuwa tego katalogu.

### Linux (Debian / Ubuntu, x86_64)

- Dwuklik na pliku `.deb` przekazuje go graficznemu instalatorowi systemu (GNOME Software / App Center / KDE Discover / GDebi); równoważne polecenie w terminalu to `sudo apt install ./helixcraft_<version>_amd64.deb`.
- Program instaluje się w `/opt/HelixCraft`, a dane użytkownika w `~/.config/HelixCraft` — **odinstalowanie nie usuwa tych danych**.
- Zalecane są czcionki CJK (pakiet deklaruje `Recommends: fonts-noto-cjk`; instalacja przez `dpkg -i` pomija zalecane zależności — użyj `apt install`).

## Aktualizacje online

Około 20 sekund po uruchomieniu aplikacja sprawdza w tle dostępność aktualizacji (domyślnie włączone, najwyżej raz na 24 godziny, można wyłączyć w ustawieniach). Odnaleziona nowa wersja jest tylko sygnalizowana — **nic nie jest pobierane automatycznie**; pobieranie odbywa się przez HTTPS z wznawianiem transferu i weryfikacją SHA-256, a pakiety, które nie przejdą weryfikacji, są odrzucane. W systemie Windows instalację przeprowadza kreator NSIS, po czym aplikacja jest automatycznie uruchamiana ponownie; w systemie Linux pobrany plik `.deb` trafia do instalatora pakietów systemu.

## Główne funkcje

- **Mapy wektorów i edycja sekwencji**: widoki kołowy i liniowy są dwukierunkowo sprzężone z tekstem sekwencji — klik na mapie zaznacza sekwencję, a klik w sekwencji lokalizuje pozycję na mapie; elementy są kolorowane według typu, a na mapie nakładają się miejsca restrykcyjne, pozycje starterów, ORF-y i znaczniki mutacji; styl mapy (kolory, rozmiary czcionek, legenda, widoczność) jest w pełni konfigurowalny, z eksportem do SVG / PDF / PNG i innych formatów na potrzeby publikacji; sekwencję edytuje się bezpośrednio (wpisywanie, usuwanie, wklejanie), współrzędne elementów przeliczają się automatycznie, a wszystkie operacje na sekwencji i elementach obsługują 50 kroków cofania i ponawiania.
- **Inteligentna adnotacja**: porównanie pełnej sekwencji wektora z biblioteką elementów rozpoznaje znane elementy (wymagane ≥99% tożsamości DNA lub ≥90% zgodności translacji, z podglądem każdej pozycji przed importem seryjnym) i automatycznie wnioskuje pola takie jak oporność na antybiotyki, gospodarz, promotor czy gen reportera (z podaniem pewności i dowodów; istniejące informacje nie są nadpisywane).
- **Predykcja ORF i wyszukiwanie BLAST**: skanowanie w sześciu ramkach odczytu (również ORF-ów przechodzących przez origin plazmidów kołowych); wyniki wyświetlają się na mapie, a po kliknięciu lokalizują pozycję w sekwencji, a produkty translacji można zapisać do bazy sekwencji; zaznaczony fragment można przesłać do NCBI (blastn / blastp / blastx i inne programy).
- **Symulacja trawienia restrykcyjnego i wirtualna elektroforeza w żelu**: w czasie rzeczywistym powstają listy fragmentów dla trawienia pojedynczym, dwoma i wieloma enzymami (miejsca przechodzące przez origin plazmidów kołowych są obsłużone poprawnie); wyniki trawienia jednym kliknięciem trafiają do symulacji żelu, w której wybierasz marker (DL2000, 1 kb Ladder i 9 innych popularnych), stężenie agarozu, napięcie i czas elektroforezy, a pozycje prążków są wyliczane wg modeli migracji skalibrowanych na literaturze; automatyczna kontrola wpływu metylacji (Dam / Dcm / CpG) wskazuje miejsca blokowane w popularnych szczepach; asystent wyboru miejsc restrykcyjnych proponuje kandydatów i preferowane rozwiązanie, gdy nie wiesz, gdzie sklonować.
- **Płótno przepływu pracy klonowania**: eksperyment składasz jak schemat blokowy — źródła sekwencji → projektowanie starterów / optymalizacja kodonów → wirtualne PCR → trawienie / oczyszczanie → składanie → transformacja / PCR kolonii / weryfikacja sekwencjonowaniem → zapis z powrotem do bazy danych, łącznie 30 typów węzłów; wyjścia każdego węzła są **obliczane w czasie rzeczywistym** — zmiana danych wejściowych natychmiast ponawia symulację po stronie elementów podrzędnych, a po domknięciu grafu można obejrzeć pełną sekwencję końcowego plazmidu rekombinowanego (projekt uznaje się za ukończony dopiero, gdy jest zgodny z oczekiwaniami); dostępne są cofanie/ponawianie, automatyczny zapis oraz import/eksport JSON. Obsługiwane strategie składania: Gibson, Golden Gate (BsaI / BbsI / BpiI / SapI, z zaleceniami zasad ochronnych), ligacja T4, klonowanie TA / TOPO, Gateway LR / BP, BioBrick.
- **Płótno konstruowania cząsteczek (Beta)**: projektowanie w stylu „wybierz szkielet i wstaw elementy” — wybierasz szkielet z biblioteki wektorów, wypełniasz luki elementami i wskazujesz metodę składania, a program automatycznie generuje sposób linearyzacji, wszystkie sekwencje starterów, zestaw reakcji składania, przewidywane fragmenty PCR kolonii i propozycje starterów do sekwencjonowania; **zapis do bazy jest możliwy tylko wtedy, gdy produkt jest zgodny z projektem co do każdej zasady**.
- **Projektowanie starterów ogólnych i qPCR**: trzy tryby projektowania (amplifikacja zaznaczonego zakresu / szukanie starterów w zaznaczeniu / amplifikacja od regionów flankujących), ponad 50 regulowanych parametrów (Tm, GC, długość produktu, stabilność końca 3′ i inne), lista Top20 kandydatów z Tm, zawartością GC%, ryzykiem struktur hairpin i dimerów oraz oceną 100-punktową; pogłębiona analiza (miejsca nieprawidłowej inicjacji, wydajność starterów, profile stabilności wewnętrznej) z możliwością przekazania uwag („koniec 3′ zbyt stabilny”, „Tm za niskie”), na które program odpowiada ukierunkowanym ponownym wyszukiwaniem; kreator qPCR automatycznie wykonuje porównanie splicingowe mRNA z genomem, rysuje strukturę egzonów i projektuje według hierarchii strategii — najpierw startery obejmujące granice egzonów, następnie amplikony przecinające intron — co eliminuje zakłócenia od genomowego DNA; wyniki otrzymują ocenę zgodności z MIQE i są przy zapisie automatycznie wiązane z genem; każdą parę starterów można wcześniej sprawdzić w wirtualnym PCR (oczekiwana wielkość produktu, brak niespecyficznych amplifikacji); baza starterów prowadzona według par (qPCR / ogólne / klonowanie / detekcja) z powiązaniami genów i projektów, importem/eksportem Excel oraz historią zmian.
- **Analiza wyników sekwencjonowania**: przeglądarka chromatogramów otwiera pliki AB1 z czterokanałowymi śladami fluorescencji i wartościami jakości, z porównaniem z sekwencją referencyjną podstawami po podstawie i możliwością ręcznych poprawek (wynik sekwencatora pozostaje autorytatywny i nie jest po cichu nadpisywany); wiele odczytów Sanger jest automatycznie składanych (algorytm CAP3) z sekwencją konsensusową kontigu, głębokością pokrycia i ostrzeżeniami o obszarach niskiej jakości; weryfikacja wektora rekombinowanego mapuje odczyty na twój wektor z automatycznym wyborem lepszej orientacji nici (również wektory kołowe przechodzące przez origin) i tworzy diagram „elementy wektora + układ odczytów” kolorowany według zgodności, na którym niedopasowania, insercje i delecje widać od razu; dostępne są też dopasowanie wielu sekwencji (ClustalW) i budowa drzew filogenetycznych.
- **Analiza obrazów żeli oparta na AI**: kreator z trzech kroków — otwierasz zdjęcie żelu, wbudowany model głębokiego uczenia automatycznie rozpoznaje ścieżki i prążki (można je dodawać, usuwać i dopasowywać przeciąganiem), następnie wykonujesz analizę ilościową; po wybraniu ścieżki markera, typu drabinki i zawartości prążka referencyjnego program automatycznie dopasowuje krzywą kalibracji rozmiarów i podaje dla każdego prążka **rozmiar fragmentu i ilość DNA** (metoda zintegrowanej gęstości optycznej), a pozycje opisów można przeciągać; eksport obejmują opatrzone adnotacjami obrazy (PNG / JPG / BMP / TIF) i wyniki ilościowe w formacie JSON.
- **Analiza białek**: trzy sprzężone widoki — schemat topologii (regiony transbłonowe, peptydy sygnałowe, struktura drugorzędowa) ↔ panel sekwencji aminokwasowej (wielosegmentowe zaznaczanie) ↔ struktura 3D (automatycznie pobierana z RCSB PDB / AlphaFold DB) — kliknięcie dowolnej pozycji lub segmentu synchronicznie podświetla sekwencję i strukturę; lokalna analiza daje wyniki w kilka sekund (masa cząsteczkowa, punkt izoelektryczny, hydrofobowość, skład aminokwasowy; przewidywanie lokalizacji subkomórkowej z rankingiem przedziałów i pewnością; siedem klas miejsc modyfikacji potranslacyjnych, m.in. fosforylacja, ubikwitynacja, glikozylacja; regiony nieuporządkowane, o niskiej złożoności, coiled-coil i antygenowe); online program zgłasza najlepiej oceniane kandydatury do skanowania domen InterProScan i wyszukiwania homologii BLAST, przenosząc zweryfikowane adnotacje Swiss-Prot na twoją sekwencję (tylko uzupełniają, nigdy nie nadpisują wniosków lokalnych, ze wskazaniem źródła).
- **Zarządzanie danymi laboratoryjnymi**: pięć baz danych — wektorów (wektory matrycowe i rekombinowane, dwupoziomowe grupy robocze), sekwencji (pliki sekwencjonowania, sekwencje genów i inne sekwencje w jednym widoku z filtrowaniem po powiązaniach gen/projekt/wektor/starter), starterów, enzymów (ponad 580 enzymów restrykcyjnych z miejscami rozpoznania, mapami cięć, typami, końcami i temperaturami oraz możliwością definiowania własnych) i projektów (przypisywanie wektorów/genów/starterów/plików sekwencjonowania do badań); całą grupę roboczą wektorów można spakować do pliku `.hcvec` i przekazać współpracownikom (przy imporcie zatwierdzają pozycje pojedynczo), a dwa komputery z HelixCraft w tej samej sieci lokalnej mogą wymieniać dane szyfrowanym kanałem z ośmiocyfrowym kodem parowania (odbiornik tylko wypełnia puste pola i nie nadpisze istniejących edycji); automatyczne kopie zapasowe przy starcie (zachowywanych 5), ręczna pełna kopia w jednym pliku ZIP i przywracanie jednym kliknięciem; przed usunięciem wektora/genu/startera wypisywane są wszystkie powiązane dane, a zakres usuwania wybierasz ty.
- **Opcjonalny asystent AI**: działa po skonfigurowaniu dowolnego interfejsu zgodnego z OpenAI (klucz API przechowywany wyłącznie lokalnie) i oferuje czat strumieniowy, wprowadzanie głosem, odczytywanie odpowiedzi na głos oraz dopracowywanie promptów; zna otwarte przez ciebie geny/wektory/okna i na życzenie przełącza strony, lokalizuje obiekty oraz odpytuje i modyfikuje dane — modyfikacje przechodzą dokładnie tą samą ścieżką co ręczna edycja i można je cofnąć; potrafi wyłuskać z wklejonego fragmentu metodki lub opisu ustnego ustrukturyzowany protokół (szkielet, insert, enzymy, metoda składania), po czym deterministyczny silnik programu generuje startery i wskazówki do eksperymentu — **AI zajmuje się wyłącznie rozumieniem tekstu i nie generuje żadnych sekwencji zasad**; **bez skonfigurowanego AI wszystkie funkcje mają czysto ręczną ścieżkę, a program pozostaje w pełni sprawny.**

## Wtyczki danych gatunkowych

Adnotacje genów i dane ekspresji są podłączane przez „wtyczki danych gatunkowych”, które można instalować, włączać i odinstalowywać na stronie ustawień. Pakiet instalacyjny zawiera dane adnotacyjne ryżu (ok. 100 tys. wpisów), a pozyskane online adnotacje, sekwencje i obrazy są automatycznie zapisywane w lokalnej pamięci podręcznej i domyślnie odczytywane z niej (ponowne pobranie tylko na wyraźne odświeżenie), dzięki czemu dane są dostępne także offline.

| Wtyczka | Źródła danych | Co otrzymujesz |
|---|---|---|
| Ryż (Rice) | RAP-DB, MSU-RGAP, RiceData, RiceXPro | adnotacje loci, struktura egzonów, synonimy, fenotypy mutantów, mapy ekspresji przestrzenno-czasowej (wartości i obrazy), sekwencje wszystkich wersji, wzajemna wymiana identyfikatorów między bazami |
| Ensembl Plants | Ensembl Plants, EBI Expression Atlas | wyszukiwanie genów w ponad 100 gatunkach, pobieranie sekwencji, adnotacje GO, ekspresja RNA-Seq |
| Phytozome | JGI Phytozome | wyszukiwanie genów, modele genów, sekwencje CDS / cDNA / białkowe, domeny, geny homologiczne |
| ePlant (BAR) | BAR eFP Browser | kolorowe piktogramy ekspresji tkankowej i poziomy ekspresji dla poszczególnych tkanek u 13 gatunków |

## Bezpieczeństwo i prywatność danych

- **Wszystkie dane są przechowywane lokalnie**: nic nie jest wysyłane na serwery; połączenia sieciowe następują tylko wtedy, gdy sam poprosisz o dane online (NCBI, bazy danych gatunkowych, banki struktur białek, aktualizacje programu).
- **AI jest w pełni opcjonalne**: asystent wymaga własnego klucza API, przechowywanego wyłącznie lokalnie.
- **Scalanie nigdy nie nadpisuje**: instalacja danych przykładowych, import pakietów i odbiór transmisji w sieci lokalnej tylko wypełniają puste pola — twoja istniejąca zawartość pozostaje nietknięta.

## Obsługiwane formaty plików

| Kierunek | Formaty |
|---|---|
| Otwieranie / import | GenBank (`.gb` `.gbk`), FASTA (`.fasta` `.fa` `.faa`), SnapGene (`.dna`), EMBL (`.embl`), chromatogramy (`.ab1`), Excel ze starterami (`.xlsx`), adnotacje białek (UniProtKB / GFF3 / InterProScan / GenPept), struktury białek (PDB / mmCIF), pakiety HelixCraft (pakiet genów / pakiet wektorów `.hcvec` / pakiet białek `.hcp`) |
| Zapis / eksport | GenBank, FASTA, SnapGene `.dna`, EMBL, obrazy map (SVG / PDF / PNG / JPG / BMP / TIF), opatrzone adnotacjami obrazy żeli, Excel ze starterami, adnotacje białek w 6 formatach, pakiety danych genów / `.hcvec` / `.hcp`, statyczna strona WWW ze szczegółami genu, pełna kopia zapasowa w formacie ZIP |

## Języki interfejsu

Od wersji v0.3.7 wszystkie moduły funkcjonalne są dostępne w pełnym tłumaczeniu na 20 języków: 简体中文, English, 日本語, 한국어, Français, Deutsch, Español, Português, Русский, Italiano, العربية, हिन्दी, ไทย, Tiếng Việt, Bahasa Indonesia, Türkçe, Nederlands, Polski, Svenska, Čeština — język można zmienić w każdej chwili w „Ustawienia → Język”.

## O tym repozytorium

To repozytorium służy wyłącznie do **dystrybucji pakietów instalacyjnych i manifestu aktualizacji online** i nie zawiera kodu źródłowego. Wydanie oznaczone tagiem `latest` jest kanałem aktualizacji online (zasoby zastępowane przy każdym wydaniu), a wydania z tagami `v<version>` to archiwa wcześniejszych wersji. To samo repozytorium jest równolegle hostowane na [GitHub](https://github.com/liudab/HelixCraft) i [GitCode](https://gitcode.com/BohanLab/HelixCraft), a pakiety instalacyjne publikowane są na obu platformach.

## Licencja

[MIT](LICENSE)

## Kontakt

Bohan Liu @ BohanLab · liubohan@hunau.edu.cn
