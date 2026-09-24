# HelixCraft

Phần mềm desktop hỗ trợ kỹ thuật di truyền nhờ AI · AI-powered gene engineering tools

[简体中文](README.md) · [English](README_EN.md) · [日本語](README_ja.md) · [한국어](README_ko.md) · [Français](README_fr.md) · [Deutsch](README_de.md) · [Español](README_es.md) · [Português](README_pt.md) · [Русский](README_ru.md) · [Italiano](README_it.md) · [العربية](README_ar.md) · [हिन्दी](README_hi.md) · [ไทย](README_th.md) · **Tiếng Việt** · [Bahasa Indonesia](README_id.md) · [Türkçe](README_tr.md) · [Nederlands](README_nl.md) · [Polski](README_pl.md) · [Svenska](README_sv.md) · [Čeština](README_cs.md)

> HelixCraft là phần mềm desktop dành cho nghiên cứu sinh học phân tử và kỹ thuật di truyền, đồng hành trọn vẹn quy trình làm việc "tìm gen → đọc trình tự → thiết kế nhân dòng → lắp ghép ảo → xác minh bằng thí nghiệm → quản lý dữ liệu": chỉnh sửa bản đồ vector, phân tích trình tự, thiết kế primer, mô phỏng cắt enzyme giới hạn và điện di trên gel, quy trình nhân dòng, phân tích sắc ký đồ sequen, tra cứu dữ liệu loài, phân tích protein, cùng một trợ lý AI tùy chọn. Toàn bộ dữ liệu được lưu ngay trên máy tính của bạn — không cần đăng ký tài khoản, không phụ thuộc đám mây; giao diện hỗ trợ 20 ngôn ngữ.
> Tài liệu đầy đủ: [简体中文](README.md) · [English](README_EN.md)

## Bạn có thể làm gì với HelixCraft?

- Mở tệp plasmid để nắm ngay cấu tạo các yếu tố và vị trí cắt enzyme, sau đó xuất hình bản đồ đạt chuẩn công bố khoa học.
- Mô phỏng trọn vẹn trên máy tính phương án Gibson / Golden Gate / nối bằng enzyme giới hạn trước khi phối bất kỳ phản ứng nào.
- Thiết kế primer nhân dòng hoặc primer qPCR vắt qua mối nối exon, kèm điểm số và căn cứ đánh giá cho từng thiết kế.
- Xem sắc ký đồ sequen, lắp ghép các read, rồi đối chiếu kết quả về vector tái tổ hợp để kiểm tra.
- Chú thích và định lượng giếng/băng trên ảnh gel.
- Từ một trình tự protein, phân tích tính chất lý hóa, vị trí định vị nội bào, vị trí biến đổi sau dịch mã và cấu trúc ba chiều.
- Quản lý vector, gen, primer và tệp sequen theo đề tài, truyền giữa các máy tính trong phòng thí nghiệm và sao lưu định kỳ.

## Tải xuống

Phiên bản mới nhất luôn được phát hành tại kênh [**Releases · latest**](releases/tag/latest):

| Nền tảng | Gói cài đặt | Cách cài đặt |
|---|---|---|
| Windows 10 / 11 (x64) | `HelixCraft.Setup.<version>.exe` | Nhấp đúp để chạy trình hướng dẫn cài đặt |
| Debian / Ubuntu (x86_64) | `helixcraft_<version>_amd64.deb` | Nhấp đúp để giao cho trình cài đặt đồ họa của hệ thống, hoặc `sudo apt install ./<tệp>` |

Kênh `latest` đồng thời là nguồn dữ liệu của chức năng "kiểm tra cập nhật" trong ứng dụng, tài sản của kênh được thay thế trọn vẹn theo từng phiên bản; các phiên bản cũ xem tại [danh sách Releases](releases). Trong cùng thư mục, `latest.json` là bản kê khai cập nhật mà ứng dụng sử dụng, liệt kê tên tệp, số byte và mã băm SHA-256 của từng gói cài đặt, giúp bạn xác minh bản tải về có đầy đủ và không bị can thiệp.

## Cài đặt

### Windows

- Chạy `HelixCraft.Setup.<version>.exe` và làm theo trình hướng dẫn (mặc định cài cho mọi người dùng, cần quyền quản trị viên).
- Trình hướng dẫn cung cấp thành phần tùy chọn **dữ liệu mẫu** (vector mẫu, quy trình nhân dòng và plugin dữ liệu loài) để người dùng mới trải nghiệm ngay; dữ liệu mẫu chỉ được nhập khi nội dung tương ứng chưa tồn tại và **không bao giờ ghi đè dữ liệu bạn đã tạo**.
- **Cài đè lên bản cũ vẫn giữ nguyên toàn bộ dữ liệu.** Thư mục dữ liệu là `%APPDATA%\HelixCraft` (cơ sở dữ liệu loài nằm trong `%APPDATA%\HelixCraftData`); gỡ cài đặt không xóa thư mục này.

### Linux (Debian / Ubuntu, x86_64)

- Nhấp đúp vào tệp `.deb` sẽ được giao cho trình cài đặt đồ họa của hệ thống; lệnh tương đương trong terminal là `sudo apt install ./helixcraft_<version>_amd64.deb`.
- Chương trình cài vào `/opt/HelixCraft`, dữ liệu người dùng nằm tại `~/.config/HelixCraft`; **gỡ cài đặt không xóa**.
- Nên cài sẵn phông chữ CJK cho hệ thống.

## Cập nhật trực tuyến

Khoảng 20 giây sau khi khởi động, ứng dụng tự kiểm tra cập nhật ở chế độ nền (mặc định bật, tối đa một lần mỗi 24 giờ, có thể tắt trong phần cài đặt). Phát hiện phiên bản mới thì chỉ nhắc nhở, **không tự tải xuống**; quá trình tải đi qua HTTPS, hỗ trợ tiếp truyền tại điểm ngắt và kiểm tra SHA-256, gói cài đặt không đạt kiểm tra sẽ bị từ chối. Trên Windows, trình hướng dẫn NSIS hoàn tất việc cài đặt và ứng dụng tự khởi động lại; trên Linux, tệp `.deb` đã tải được giao cho trình cài đặt phần mềm của hệ thống.

## Tính năng chính

- **Bản đồ vector và chỉnh sửa trình tự**: bản đồ vòng tròn / tuyến tính liên thông hai chiều với văn bản trình tự — bấm bản đồ để chọn trình tự, bấm trình tự để định vị trên bản đồ; yếu tố được tô màu theo loại, hiển thị chồng lớp cùng vị trí cắt enzyme, vị trí gắn primer, ORF và dấu đột biến; kiểu dáng bản đồ (màu sắc, cỡ chữ, chú giải, ẩn/hiện) tùy biến tự do, có thể xuất SVG / PDF / PNG làm hình minh họa bài báo. Trình tự được chỉnh sửa trực tiếp (gõ, xóa, dán đều được), tọa độ yếu tố tự cập nhật sau khi chèn/xóa; mọi thao tác trên trình tự và yếu tố đều hỗ trợ hoàn tác / làm lại 50 bước.
- **Chú thích thông minh**: so khớp toàn bộ trình tự vector với cơ sở dữ liệu yếu tố để tự nhận diện các yếu tố đã biết (chỉ công nhận khi độ trùng khớp DNA ≥99% hoặc độ khớp bản dịch ≥90%, có xem trước từng mục trước khi nhập hàng loạt), đồng thời tự suy luận các thuộc tính như kháng kháng sinh, vật chủ, promoter, gen báo cáo của vector (kèm độ tin cậy và bằng chứng, không ghi đè thông tin đã có).
- **Dự đoán ORF và tìm kiếm BLAST trực tuyến**: quét cả sáu khung đọc (bao gồm cả ORF vắt qua điểm gốc của plasmid vòng), kết quả hiển thị ngay trên bản đồ, sản phẩm dịch mã có thể lưu vào cơ sở dữ liệu trình tự; chọn bất kỳ đoạn trình tự để gửi lên NCBI (blastn / blastp / blastx và các chương trình khác).
- **Mô phỏng cắt enzyme giới hạn và điện di gel ảo**: cắt đơn / kép / nhiều enzyme cho ngay danh sách fragment theo thời gian thực, xử lý chính xác cả vị trí cắt vắt qua điểm gốc trên plasmid vòng; kết quả cắt chuyển một chạm sang mô phỏng gel — chọn marker thông dụng (DL2000, 1 kb Ladder và các loại khác), nồng độ agarose, điện áp và thời gian chạy, vị trí băng được suy theo mô hình di chuyển đã hiệu chuẩn theo tài liệu khoa học — giúp đoán trước cắt kiểm tra có tách được băng mục tiêu hay không; tự động kiểm tra ảnh hưởng methyl hóa (Dam / Dcm / CpG); có trợ lý đề xuất vị trí cắt ứng viên khi chưa biết chọn chỗ nào.
- **Bản vẽ quy trình nhân dòng**: nối thí nghiệm như vẽ sơ đồ khối — nguồn trình tự → thiết kế primer / tối ưu codon → PCR ảo → cắt enzyme / tinh sạch → lắp ghép → biến nạp / colony PCR / xác minh bằng sequen → lưu về cơ sở dữ liệu, tổng cộng 30 loại nút; đầu ra của mỗi nút đều được **tính theo thời gian thực** — thay đổi đầu vào phía trên, phía dưới lập tức mô phỏng lại; nối xong có thể xem trình tự đầy đủ của plasmid tái tổ hợp cuối cùng, thiết kế chỉ tính là hoàn tất khi khớp với kỳ vọng. Hỗ trợ các chiến lược lắp ghép Gibson, Golden Gate (BsaI / BbsI / BpiI / SapI, kèm gợi ý base bảo vệ), nối T4, nhân dòng TA / TOPO, Gateway LR / BP, BioBrick, cùng hoàn tác / làm lại, tự lưu và nhập / xuất JSON.
- **Bản vẽ dựng phân tử (Beta)**: hợp với lối thiết kế kiểu "chọn khung, lắp yếu tố" — chọn khung (backbone) từ thư viện vector, lấp khoảng trống bằng các yếu tố, chọn phương pháp lắp ghép; phần mềm tự sinh cách tuyến tính hóa, toàn bộ trình tự primer, hỗn hợp phản ứng lắp ghép, đoạn colony PCR xác minh và gợi ý primer sequen; sản phẩm chỉ được lưu vào thư viện khi **khớp từng base với thiết kế**.
- **Thiết kế primer phổ thông và qPCR**: ba chế độ (khu vực chọn / trong khu vực chọn / từ vùng flanking), hơn 50 tham số chỉnh được (Tm, GC, độ dài sản phẩm, độ ổn định đầu 3′…), 20 cặp ứng viên tốt nhất kèm Tm, GC%, rủi ro hairpin / dimer và điểm tổng hợp trên thang 100; trợ lý qPCR tự thực hiện phép so thẳng cắt nối (splice alignment) giữa mRNA và bộ gen, vẽ cấu trúc exon, thiết kế theo chiến lược phân cấp — ưu tiên primer vắt qua mối nối exon, sau đó đến amplicon vắt qua intron — ngăn từ gốc rễ sự nhiễu của DNA bộ gen đối với định lượng; kết quả kèm điểm tuân thủ MIQE, khi lưu tự liên kết với gen; bất kỳ cặp primer nào cũng có thể xác minh trước bằng PCR ảo (in silico); kho primer quản lý theo cặp (qPCR / phổ thông / nhân dòng / kiểm tra), hỗ trợ liên kết gen, phân loại dự án, nhập / xuất Excel và lịch sử thay đổi.
- **Phân tích kết quả sequen**: trình xem sắc ký đồ mở tệp AB1 để xem bốn kênh huỳnh quang và giá trị chất lượng, đối chiếu từng base với trình tự tham chiếu, có thể sửa bằng tay khi cần (kết quả máy sequen luôn là chuẩn, thuật toán không tự ý ghi đè); lắp ghép tự động nhiều read Sanger bằng thuật toán CAP3, cho ra trình tự consensus, độ sâu phủ và cảnh báo vùng chất lượng thấp, contig lắp xong có thể chuyển thẳng sang so thẳng; xác minh vector tái tổ hợp bằng cách so read về vector của bạn — tự chọn hướng chuỗi thuận / nghịch tốt hơn (kể cả vector vòng vắt qua điểm gốc) — sinh sơ đồ "yếu tố vector + bố trí read" tô màu theo mức trùng khớp, chỗ khớp sai / chèn / mất nhìn rõ ngay; còn hỗ trợ so thẳng nhiều trình tự (ClustalW) và dựng cây phát sinh.
- **Phân tích ảnh gel bằng AI**: ba bước — mở ảnh gel → mô hình học sâu tích hợp tự nhận diện giếng và băng (thêm / bớt / kéo chỉnh bằng tay được) → phân tích định lượng; sau khi chọn giếng marker, loại thang marker và chỉ định hàm lượng của băng tham chiếu, phần mềm tự dựng đường chuẩn kích thước, trả ra **kích thước fragment và hàm lượng DNA** của từng băng (phương pháp mật độ quang tích phân), vị trí nhãn có thể kéo; xuất ảnh phân tích có chú thích (PNG / JPG / BMP / TIF) và kết quả JSON; nếu sửa chú thích giữa chừng, phần mềm sẽ nhắc rằng kết quả định lượng đã hết hiệu lực cần tính lại.
- **Phân tích protein**: ba khung xem liên thông — sơ đồ cấu trúc (vùng xuyên màng, peptide tín hiệu, cấu trúc bậc hai) ↔ bảng trình tự amino acid (chọn nhiều đoạn cùng lúc) ↔ cấu trúc 3D (tự tìm từ RCSB PDB / AlphaFold DB) — bấm vào bất kỳ vị trí hay đoạn nào cũng làm sáng đồng thời trình tự và cấu trúc; phân tích cục bộ ra kết quả trong vài giây: khối lượng phân tử, điểm đẳng điện, tính ưa / kỵ nước, thành phần amino acid; dự đoán vị trí nội bào (peptide tín hiệu, vùng xuyên màng, tín hiệu vào nhân… kèm xếp hạng khoang và độ tin cậy); bảy loại vị trí biến đổi sau dịch mã như phosphoryl hóa / ubiquitin hóa / glycosyl hóa; vùng vô trật tự, vùng low-complexity, coiled-coil và vùng kháng nguyên; tinh toán trực tuyến: ứng viên điểm cao nhất được tự động gửi InterProScan quét domain và BLAST tìm trình tự đồng nguồn, chuyển chú thích Swiss-Prot đã xác thực sang trình tự của bạn (chỉ bổ sung, không ghi đè kết luận cục bộ, ghi rõ nguồn).
- **Quản lý dữ liệu phòng thí nghiệm**: năm cơ sở dữ liệu — thư viện vector (vector khuôn / vector tái tổ hợp, hai cấp nhóm làm việc), cơ sở dữ liệu trình tự (tệp sequen, trình tự gen và các trình tự khác trong một khung nhìn thống nhất, lọc theo liên kết gen / dự án / vector / primer), kho primer, thư viện enzyme (hơn 580 enzyme giới hạn kèm trình tự nhận biết, bản đồ cắt, loại, loại đầu, nhiệt độ, có thể tự định nghĩa enzyme) và trình quản lý dự án (gắn vector / gen / primer / tệp sequen theo đề tài); chia sẻ: cả nhóm làm việc vector đóng gói thành một tệp `.hcvec` gửi đồng nghiệp, bên nhận xem trước từng mục rồi mới nhập; hai máy cài HelixCraft trong cùng mạng nội bộ truyền dữ liệu mã hóa qua mã ghép nối 8 chữ số, bên nhận chỉ điền vào chỗ trống, không ghi đè nội dung đã có; sao lưu: tự động sao lưu khi khởi động (giữ 5 bản), sao lưu toàn bộ thủ công (một tệp ZIP) và khôi phục một chạm; xóa có bảo vệ: trước khi xóa vector / gen / primer đều liệt kê hết dữ liệu liên quan bị ảnh hưởng, phạm vi xóa do bạn quyết định.
- **Trợ lý AI (tùy chọn)**: dùng được sau khi cấu hình bất kỳ giao diện mô hình lớn tương thích OpenAI nào (API Key chỉ lưu trên máy bạn): hội thoại dạng stream, nhập bằng giọng nói, đọc to phản hồi, gợi ý prompt; AI biết bạn đang mở gen / vector / cửa sổ nào, có thể chuyển trang, định vị thực thể, truy vấn và sửa dữ liệu theo yêu cầu — mọi sửa đổi đi đúng con đường như chỉnh tay nên hoàn tác được; dán đoạn phương pháp trong tài liệu hoặc mô tả miệng vào, AI trích ra phương án có cấu trúc (khung, đoạn chèn, enzyme, phương pháp lắp ghép), sau đó engine xác định của phần mềm sinh primer và hướng dẫn thí nghiệm — **AI chỉ hiểu văn bản, không tạo ra bất kỳ base nào**; không cấu hình AI, mọi chức năng đều có con đường thủ công trọn vẹn, phần mềm vẫn đầy đủ tính năng.

## Plugin dữ liệu loài

Chú thích gen và dữ liệu biểu hiện được tiếp nạp qua "plugin dữ liệu loài", có thể cài đặt / bật / gỡ trong trang cài đặt. Gói cài đặt tích hợp sẵn dữ liệu chú thích lúa (khoảng 100 nghìn mục); dữ liệu lấy trực tuyến sẽ tự động lưu về máy, sau đó mặc định đọc từ bộ nhớ đệm cục bộ (chỉ kết nối lại khi bấm làm mới), nên xem được cả khi ngoại tuyến:

- **Lúa (Rice)** — RAP-DB, MSU-RGAP, RiceData, RiceXPro: chú thích locus, cấu trúc exon, tên đồng nghĩa, kiểu hình mutant, bản đồ biểu hiện không gian – thời gian (số liệu + hình ảnh), trình tự các phiên bản, quy đổi mã số chéo giữa các cơ sở dữ liệu.
- **Ensembl Plants** — Ensembl Plants, EBI Expression Atlas: tìm gen trên hơn 100 loài, tải trình tự, chú thích GO, biểu hiện RNA-Seq.
- **Phytozome** — JGI Phytozome: tìm gen, mô hình gen, trình tự CDS / cDNA / protein, domain, gen đồng nguồn.
- **ePlant (BAR)** — BAR eFP Browser: biểu đồ tượng hình màu về biểu hiện mô và mức biểu hiện theo từng mô cho 13 loài.

## An toàn và quyền riêng tư của dữ liệu

- **Toàn bộ dữ liệu lưu tại chỗ**: không tải lên bất kỳ máy chủ nào; việc kết nối mạng chỉ xảy ra khi bạn chủ động yêu cầu dữ liệu trực tuyến (NCBI, cơ sở dữ liệu loài, kho cấu trúc protein, cập nhật phần mềm).
- **AI hoàn toàn tùy chọn**: trợ lý dùng API Key của riêng bạn và chỉ lưu trên máy; không cấu hình AI thì mọi chức năng đều có con đường thủ công.
- **Chỉ bổ sung, không ghi đè**: cài dữ liệu mẫu, nhập gói dữ liệu hay nhận truyền qua mạng nội bộ đều chỉ điền vào các trường còn trống, không đụng đến nội dung sẵn có của bạn.

## Định dạng tệp được hỗ trợ

| Chiều | Định dạng |
|------|------|
| Mở / nhập | GenBank (`.gb` `.gbk`), FASTA (`.fasta` `.fa` `.faa`), SnapGene (`.dna`), EMBL (`.embl`), sắc ký đồ (`.ab1`), Excel primer (`.xlsx`), chú thích protein (UniProtKB / GFF3 / InterProScan / GenPept), cấu trúc protein (PDB / mmCIF), gói HelixCraft (gói gen / gói vector `.hcvec` / gói protein `.hcp`) |
| Lưu / xuất | GenBank, FASTA, SnapGene `.dna`, EMBL, hình bản đồ (SVG / PDF / PNG / JPG / BMP / TIF), ảnh gel có chú thích, Excel primer, chú thích protein 6 định dạng, gói dữ liệu gen / `.hcvec` / `.hcp`, trang web tĩnh chi tiết gen, ZIP sao lưu toàn bộ |

## Ngôn ngữ giao diện

Từ phiên bản v0.3.7, mọi mô-đun chức năng đã được dịch trọn vẹn sang 20 ngôn ngữ: 简体中文, English, 日本語, 한국어, Français, Deutsch, Español, Português, Русский, Italiano, العربية, हिन्दी, ไทย, Tiếng Việt, Bahasa Indonesia, Türkçe, Nederlands, Polski, Svenska, Čeština. Có thể chuyển đổi bất cứ lúc nào trong "Cài đặt → Ngôn ngữ"; màn hình đầu tiên của trình cài đặt cũng cho phép chọn ngôn ngữ giao diện. Tài liệu mô tả của từng ngôn ngữ xem ở dải điều hướng ngôn ngữ ở đầu trang.

## Về kho lưu trữ này

Kho lưu trữ này chỉ dùng để **phân phối gói cài đặt và bản kê khai cập nhật trực tuyến**, không chứa mã nguồn. Release của nhãn `latest` là kênh cập nhật trực tuyến (tài sản được thay thế trọn vẹn theo từng phiên bản), các nhãn `v<phiên bản>` là nơi lưu các phiên bản lịch sử. Cùng một kho được đồng bộ trên [GitHub](https://github.com/liudab/HelixCraft) và [GitCode](https://gitcode.com/BohanLab/HelixCraft), gói cài đặt phát hành đồng thời ở cả hai nơi; nguồn dữ liệu của chức năng "kiểm tra cập nhật" trong ứng dụng là kênh `latest` trên GitHub (tự động tải qua bản mirror tăng tốc).

## Giấy phép

[MIT](LICENSE)

## Liên hệ

Bohan Liu @ BohanLab · liubohan@hunau.edu.cn
