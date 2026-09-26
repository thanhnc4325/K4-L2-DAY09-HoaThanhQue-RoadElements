# Peer feedback + owner response

Phần 1 do **nhóm peer** trả lời (gửi kèm file export). Phần 2 do **nhóm owner** điền. Thay mọi placeholder mới
là xong (gate G5).

- **Nhóm peer:** ⚠️ MÔ PHỎNG NỘI BỘ — không phải nhóm peer. Nhóm chưa nhận được bài của nhóm peer trước hạn nộp. Chi tiết và giới hạn: `internal_simulation/README_MO_PHONG_NOI_BO.md`.
- **Người label blind:** Zeen (thành viên nhóm) — dùng lại lần gắn nhãn thử 28 ảnh theo guideline v1; trích 5 ảnh blind.

## 1. Peer trả lời

Không có. Đây là mô phỏng dùng lại export có sẵn; người vẽ không làm phiếu 5 câu và không có blind window, nên nhóm
**không** điền câu trả lời thay người vẽ. Phần này sẽ điền khi có bài của nhóm peer thật.

Quan sát của owner từ export (không phải lời của peer):

- Rule rõ nhất: quy tắc 3 dấu hiệu — 0 box vẽ nhầm biển trông giống; GTS14 gắn đúng `no_speed_sign`.
- Rule dễ hiểu sai: thứ tự bước trong cây `applies_to_ego` (GTS25) — người vẽ dừng ở "lề phải" trước khi xét "chỗ tách nhánh".
- `needs_review` không được tích ở bất kỳ box nào (0/6 box trên ảnh blind) — checkbox mặc định `false` dễ bị bỏ qua.

## 2. Owner phân loại

Owner không tranh luận để bảo vệ guideline. Mỗi feedback và mỗi decision peer làm sai được xếp vào một hướng xử lý.

| Feedback / decision sai | Nguyên nhân (guideline gap / data ambiguity / execution error) | Xử lý (accept + revise / reject with evidence / add escalation rule) | Bằng chứng |
|---|---|---|---|
| GTS25 d2: gán `yes`, gold `unknown` + `needs_review=true` | guideline gap (v1: bước "lề phải" đứng trước bước "góc giao lộ / tách nhánh") | accept + revise — đã đổi thứ tự bước ở v2, thêm ví dụ GTS05 | `internal_simulation/transfer_score_internal.csv`; `08_revision_log.md` dòng v2 |
| `needs_review` không được tích trên box nào | guideline gap + CVAT default `false` dễ bị bỏ qua | accept + revise — checklist v2 bắt buộc tích khi `unknown`/`unreadable` | `zeen_blind5_annotations.xml` |

