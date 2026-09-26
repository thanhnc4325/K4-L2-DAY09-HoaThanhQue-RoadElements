# ⚠️ MÔ PHỎNG NỘI BỘ — KHÔNG PHẢI BLIND TEST VỚI NHÓM PEER

Nhóm chưa nhận được bài của nhóm peer trước hạn nộp. Thư mục này **không** thay thế blind handoff thật và **không**
nằm trong `peer_output/`, nên gate G5 vẫn chưa đạt, đúng với thực tế.

## Dữ liệu dùng

- `zeen_blind5_annotations.xml`: trích 5 ảnh blind (GTS19, GTS03, GTS25, GTS08, GTS14) từ lần gắn nhãn thử toàn bộ
  28 ảnh trên CVAT của thành viên **Zeen** (export CVAT for images 1.1, 26/09/2026 04:24 UTC). Đây là dữ liệu thật,
  không chỉnh sửa.
- Gold: `project/04_edge_cases/gold_decisions.csv` (13 decision). Gold **chưa freeze** bằng `lab9.py freeze`
  tại thời điểm chấm.

## Giới hạn — đọc trước khi dùng số liệu

1. Người vẽ là thành viên trong nhóm, không phải người lạ; không có blind window 15 phút và không có phiếu 5 câu.
2. Người vẽ dùng **guideline v1**; gold và guideline hiện tại là **v2** (đã sửa sau chính lần gắn nhãn này).
3. Gold được viết **sau** khi đã xem export này → có nguy cơ thiên lệch. Mọi decision đã được viết theo rule trong
   guideline v2, không theo đáp án của người vẽ (ví dụ GTS25 d2 vẫn chấm 0).
4. Chấm tay, không qua `lab9.py score` / `lab9.py gts` (hai lệnh này yêu cầu freeze).

## Kết quả (chấm tay theo công thức README)

| Thành phần | Kết quả |
|---|---|
| D — decision không phải geometry | 10/11 = 90.9 |
| C — critical | 4/4 = 100 |
| G — geometry | 2/2 = 100 |
| I — independence | 100 (0 câu hỏi ghi nhận; **không có** blind window thật) |
| **GTS mô phỏng** | 0.6·90.9 + 0.2·100 + 0.1·100 + 0.1·100 = **94.5** |

Decision sai duy nhất: **GTS25 d2** — gán `yes` thay vì `unknown` + `needs_review`. Nguyên nhân: guideline gap ở v1
(bước "lề phải" đứng trước bước "chỗ tách nhánh"). Đã sửa ở v2. Con số 94.5 **đánh giá quá cao** độ chuyển giao vì
các giới hạn 1–3; không dùng thay GTS thật.
