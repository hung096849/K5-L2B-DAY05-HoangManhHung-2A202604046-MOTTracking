# Báo cáo cá nhân — HoangManhHung-2A202604046

Đổi tên file theo quy tắc `MSSV_HoTen.md`. Ví dụ: `20241234_NguyenVanAn.md`.

Đoạn video: MOT17-09, 150 frame (frame 1–150), nguồn MOTChallenge, giấy phép CC BY-NC-SA 3.0.

## 0. Thông tin học viên

- Họ tên:Hoàng Mạnh Hùng
- MSSV:2A202604046
- Mã đề (A/B/C):A
- Email:26ai.hunghm@vinuni.edu.vn
- Link repository:https://github.com/hung096849/K5-L2B-DAY05-HoangManhHung-2A202604046-MOTTracking.git
- Giờ bắt đầu: 4h30
- Giờ kết thúc: 7h30

## 1. Xem trước đoạn video (CP0)

Ghi **trước khi vẽ**, mỗi người một dòng.

| Mã | Frame xuất hiện | Frame cuối thấy được | Rẽ / dừng / đổi tốc độ ở frame | Bị che ở frame | Ghi chú |
|---|---|---|---|---|---|

| P1 | 0 | 149 | | không | Lại gần camera, box lớn dần |
| P2 | 0 | 149 | | 108–149 | |
| P3 | 0 | 149 | | 39–59 | |
| P4 | 24 | 149 | | không | Bước vào từ mép phải |
| P5 | 79 | 149 | | không | Xuất hiện muộn |

## 2. Keyframe và thời gian (CP1, CP4)

Số keyframe lấy từ kết quả `src/check_submission.py`.

| Mã | Số keyframe | Keyframe ở frame | Số frame có mặt | Keyframe / 100 frame | Thời gian (phút) | Chỗ khó |
|---|---|---|---|---|---|---|
| P1 | 87 | 0, 1, 17, 24, 25, 29, ... 145, 149 (đoạn dày: 95–123) | 150 | 58,0 | | |
| P2 | 10 | 0, 12, 34, 46, 82, 108, 120, 132, 144, 149 | 150 | 6,7 | | |
| P3 | 15 | 0, 12, 24, 36, 39, 48, 60, 72, 84, 96, 108, 120, 132, 144, 149 | 150 | 10,0 | | |
| P4 | 12 | 24, 36, 48, 60, 72, 84, 96, 108, 120, 132, 144, 149 | 126 | 9,5 | | |
| P5 | 8 | 79, 91, 103, 115, 127, 138, 139, 149 | 71 | 11,3 | | |
| **Tổng** | 132 | | 647 | 20,4 | | |

Keyframe / 100 frame của cả bài = tổng keyframe ÷ tổng số frame có mặt × 100 = ...

Bạn đặt keyframe nhiều nhất ở người nào? Vì sao (người đó rẽ, dừng, lại gần camera hay bị che)?

Đó là Track 1. Người đầu tiên được gán đi từ xa lại gần camera nên kích thước tăng.

## 3. Đoạn bị che (CP2)

Người bị che: `P2`

| Mốc | Frame |
|---|---:|
| Bắt đầu bị che một phần (bật `occluded`) | 39 |
| Mất hẳn (bật `outside`) | Không có |
| Hiện lại (tắt `outside`) | Không có |
| Thấy rõ trở lại (tắt `occluded`) | 60 |

- Thời gian khuất hẳn: 21 frame = 0.7 giây.
- Quyết định: giữ cùng ID / tạo track mới.
- Lý do (trả lời 3 câu: khuất bao lâu so với 60 frame, ngoại hình có khớp, chỗ hiện lại có đúng hướng và tốc độ):

Khuất khoảng 3 giây, ngoại hình khớp, có hiện đúng hướng và tốc độ

Ảnh chụp màn hình:

![Trước khi che](images/che_1_truoc.png)
![Giữa đoạn che, thấy cờ trên panel object](images/che_2_giua.png)
![Sau khi hiện lại, cùng ID](images/che_3_sau.png)

## 4. Tự review ID (CP3)

Lượt 1 theo người (đi ngược từ frame 149 về 0 trên CVAT), lượt 2 theo cảnh (nhảy 10 frame). Ít nhất 3 dòng; không có lỗi thì ghi một dòng "đã kiểm hai lượt, không lỗi".

Loại lỗi dùng đúng một trong 7 mã: `id_switch`, `fragmentation`, `lost`, `merge`, `false_track`, `drift`, `flag`.

Đã kiểm hai lượt, không lỗi

## 5. File xuất và kết quả tự kiểm (CP4)

| Kiểm tra | Kết quả |
|---|---|
| Tên file MOT 1.1 | HoangManhHung_mot.zip |
| Tên file CVAT for video 1.1 | HoangManhHung_cvat_video.zip |
| Số track ID khác nhau trong `gt/gt.txt` (phải là 5) | 5 |
| Frame `outside` không có dòng trong `gt.txt` (đúng / sai) | Đúng |
| Job đã completed trên CVAT máy cá nhân | Completed |

Dán phần tóm tắt in ra từ `src/check_submission.py`:

```
=== Tóm tắt ===
  Lỗi: 0   |   Cảnh báo: 1
  Không có lỗi định dạng. Mở CVAT xem lại từng [CẢNH BÁO]; cảnh báo đúng ý bạn thì ghi lý do vào báo cáo.
...
```

## 6. Ba câu kết

1. Nếu được gán lại, bạn sẽ đặt keyframe khác ở đâu? Vì sao?

Tôi sẽ gán lại keyframe ở track1, vì keyframe ở đoạn người đi đều, chỉ dày ở chỗ kích thước đổi nhanh

2. Có chỗ nào bạn không chắc "cùng ID hay ID mới"? Bạn đã quyết định và ghi chú thế nào?

   Không có chỗ nào

3. Một lỗi ID trong job của bạn (nếu không còn sót, chọn lỗi đã sửa) có thể làm xe tự lái dự đoán sai chuyển động của người đó như thế nào? Lỗi đó ảnh hưởng MOTA hay IDF1 nhiều hơn?

   Không có lỗi nào

## Bonus (nếu làm)

### B1 — Hai người đi sát

...

### B2 — So cách đặt keyframe

| Cách đặt | Số keyframe | Frame trôi nhất | Ghi chú |
|---|---:|---:|---|
| Đều mỗi 30 frame | | | |
| Theo chỗ đổi hướng | | | |

...

### B3 — So với tracker có sẵn

| Frame | Mã người | Tracker làm gì | Nhãn của bạn | Giải thích (đoán rồi sửa / ghép IoU / box score thấp / ngoại hình) |
|---:|---|---|---|---|
| | | | | |
| | | | | |

## 7. Tài liệu tham khảo và công cụ AI đã dùng
Không dùng tài liệu và công cụ AI
