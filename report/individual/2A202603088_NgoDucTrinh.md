# Báo cáo cá nhân — NgoDucTrinh-2A202603088


Đoạn video: MOT17-09, 150 frame (frame 1–150), nguồn MOTChallenge, giấy phép CC BY-NC-SA 3.0.

## 0. Thông tin học viên

- Họ tên: Ngọ Đức Trinh
- MSSV: 2A202603088
- Mã đề (A/B/C): B
- Email:26ai@vinuni.edu.vn
- Link repository: (https://github.com/ductrinh318-hue/K5-L2-Day05-NgoDucTrinh-2A202603088-MOTTracking)
- Giờ bắt đầu: 18:30
- Giờ kết thúc: 20:40

## 1. Xem trước đoạn video (CP0)

Ghi **trước khi vẽ**, mỗi người một dòng.

| Mã | Frame xuất hiện | Frame cuối thấy được | Rẽ / dừng / đổi tốc độ ở frame | Bị che ở frame | Ghi chú |
|---|---|---|---|---|---|
| P1 | 0 | 149 | Đi chậm trong cửa hàng Vodafone, đổi góc nghiêng quanh frame 50–73 | 27–38 (bị che một phần), 39–48 (khuất hoàn toàn), 49–55 (thoát che) | Người mặc đồ tối bên trong shop Vodafone |
| P2 | 0 | 149 | Đi thẳng tiến về phía camera | Không bị che | Người đi bộ tuyến chính, kích thước tăng dần khi lại gần |
| P3 | 0 | 149 | Đi thẳng tiến về phía camera | Không bị che | Người đi bộ tuyến chính, di chuyển ổn định |
| P4 | 0 | 146 | Đi chậm bên sảnh Woolworths, đổi hướng nhẹ quanh frame 106–109 và 136–146 | 106–109 (bị che một phần), 110–135 (khuất hoàn toàn), 136–146 (lộ diện lại) | Em bé mặc áo trắng váy hoa đi cùng người lớn |
| P5 | 0 | 104 | Đi ngang từ trái qua phải trước cửa Vodafone | 94–104 (bị che một phần khi tiến sát rìa khung hình) | Người mặc áo khoác đen quần kaki đi ngang qua mặt P1 |

*(Lưu ý: Thứ tự Track ID 1–5 trong file xuất tương ứng với P1, P4, P2, P3, P5 theo trình tự bạn đã gán trên CVAT).*

## 2. Keyframe và thời gian (CP1, CP4)

Số keyframe lấy từ kết quả `src/check_submission.py`.

| Mã | Số keyframe | Keyframe ở frame | Số frame có mặt | Keyframe / 100 frame | Thời gian (phút) | Chỗ khó |
|---|---|---|---|---|---|---|
| P1 (Track 1 / ID 0) | 31 | 0, 10, 20, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 49, 50, 51, 52, 55, 60, 70, 73, 80, 90, 100, 110, 120, 130, 140, 149 | 140 | 22.1 | 20 | Bị P5 đi ngang qua che khuất hoàn toàn 10 frame (39–48), dễ bị mất dấu hoặc đổi ID khi lộ diện lại |
| P4 (Track 2 / ID 1) | 24 | 0, 10, 20, 30, 40, 50, 60, 70, 80, 100, 106, 107, 108, 109, 136, 137, 138, 139, 140, 142, 143, 144, 145, 146 | 121 | 19.8 | 18 | Kích thước nhỏ ở xa, bị người áo xanh che khuất 26 frame (110–135) rồi xuất hiện lại ở mép phải |
| P2 (Track 3 / ID 2) | 16 | 0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100, 110, 120, 130, 140, 149 | 150 | 10.7 | 10 | Tiến lại gần camera nên phải mở rộng kích thước hộp bao đều đặn |
| P3 (Track 4 / ID 3) | 16 | 0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100, 110, 120, 130, 140, 149 | 150 | 10.7 | 10 | Thay đổi tỷ lệ chiều cao và chiều rộng hộp theo phối cảnh gần camera |
| P5 (Track 5 / ID 4) | 18 | 0, 10, 20, 30, 40, 50, 70, 94, 95, 96, 97, 98, 99, 100, 101, 102, 103, 104 | 105 | 17.1 | 12 | Di chuyển ngang tốc độ nhanh qua khung hình và bị cắt/che ở mép phải giai đoạn 94–104 |
| **Tổng** | **105** | - | **666** | **15.8** | **70** | - |

Keyframe / 100 frame của cả bài = tổng keyframe ÷ tổng số frame có mặt × 100 = $105 \div 666 \times 100 = 15.8$ (nằm trong khoảng chuẩn 8–18 keyframe / 100 frame).

Bạn đặt keyframe nhiều nhất ở người nào? Vì sao (người đó rẽ, dừng, lại gần camera hay bị che)?

Đặt keyframe nhiều nhất ở **P1** (31 keyframe, mật độ 22.1 KF/100 frame). Nguyên nhân chính là do P1 di chuyển bên trong cửa hàng Vodafone và bị người đi bộ P5 cắt ngang che khuất hoàn toàn từ frame 39 đến frame 48. Trước khi bị che hẳn (frame 27–38) và ngay sau khi lộ diện trở lại (frame 49–55), diện tích phần cơ thể nhìn thấy thay đổi liên tục nên cần chốt keyframe dày để bật/tắt đúng cờ `occluded` (`Q`), bật/tắt cờ `outside` (`O`) và giữ hộp bao khớp sát người sau khi thoát che khuất.

## 3. Đoạn bị che (CP2)

Người bị che: `P1`

| Mốc | Frame |
|---|---:|
| Bắt đầu bị che một phần (bật `occluded`) | 27 |
| Mất hẳn (bật `outside`) | 39 |
| Hiện lại (tắt `outside`) | 49 |
| Thấy rõ trở lại (tắt `occluded`) | 56 |

- Thời gian khuất hẳn: 10 frame (từ frame 39 đến 48) = 0.33 giây (với video 30 fps).
- Quyết định: **giữ cùng ID**.
- Lý do (trả lời 3 câu: khuất bao lâu so với 60 frame, ngoại hình có khớp, chỗ hiện lại có đúng hướng và tốc độ):
  1. **Thời gian khuất:** Đối tượng chỉ bị che khuất hoàn toàn trong 10 frame ($\approx 0.33$ giây), ngắn hơn rất nhiều so với ngưỡng tối đa 60 frame (2 giây) của bài thực hành.
  2. **Ngoại hình:** Ngay tại frame 49 khi lộ diện lại, trang phục (áo tối màu, quần dài) và vóc dáng khớp hoàn toàn với đối tượng P1 trước khi bị che.
  3. **Quỹ đạo và tốc độ:** Vị trí xuất hiện lại ở frame 49 nằm đúng trên đường nội suy di chuyển chậm bên trong cửa hàng Vodafone, giữ nguyên hướng bước và tốc độ như trước frame 39.

Ảnh chụp màn hình:

![Trước khi che](images/che_1_truoc.png)
![Giữa đoạn che, thấy cờ trên panel object](images/che_2_giua.png)
![Sau khi hiện lại, cùng ID](images/che_3_sau.png)

## 4. Tự review ID (CP3)

Lượt 1 theo người (đi ngược từ frame 149 về 0 trên CVAT), lượt 2 theo cảnh (nhảy 10 frame). Ít nhất 3 dòng; không có lỗi thì ghi một dòng "đã kiểm hai lượt, không lỗi".

Loại lỗi dùng đúng một trong 7 mã: `id_switch`, `fragmentation`, `lost`, `merge`, `false_track`, `drift`, `flag`.

| Frame | Mã người | Loại lỗi | Mô tả một câu | Phát hiện ở lượt | Đã sửa? |
|---:|---|---|---|---|---|
| 39 | P1 | `flag` | Đối tượng đã bị người áo đen che khuất 100% nhưng chưa bật cờ `outside` làm hộp bao vẫn hiển thị đè lên người che. | Lượt 1 | Đã sửa (bật `O` từ frame 39 đến 48) |
| 110 | P4 | `drift` | Khi em bé bị người áo xanh che kín từ frame 110–135, hộp nội suy bị trôi lệch khỏi quỹ đạo thực tế lúc lộ diện lại ở frame 136. | Lượt 1 | Đã sửa (bật `outside` 110–135 và chỉnh lại keyframe tại 136) |
| 40 | P5 | `false_track` | Ban đầu gán nhầm Track cho người phụ nữ mặc áo vest xám đi cạnh P4 thay vì người mặc áo khoác đen đi ngang qua trước cửa Vodafone. | Lượt 2 | Đã sửa (xóa Track thừa và vẽ lại đúng P5) |

Tổng hợp số lỗi theo loại:

| `id_switch` | `fragmentation` | `lost` | `merge` | `false_track` | `drift` | `flag` |
|---:|---:|---:|---:|---:|---:|---:|
| 0 | 0 | 0 | 0 | 1 | 1 | 1 |

Lỗi nào chỉ lượt 2 (theo cảnh) mới thấy, lượt 1 (theo người) không thấy? Vì sao?

Lỗi **`false_track`** (gán nhầm đối tượng mục tiêu ngoài danh sách của đề bài) hoặc lỗi một đối tượng bị gán trùng 2 hộp bao khác ID chỉ dễ phát hiện ở **lượt 2 (kiểm tra theo toàn cảnh)**. Vì ở lượt 1 ta chỉ tập trung nhìn vào một hộp bao duy nhất đi ngược thời gian nên dễ bỏ qua bối cảnh tổng thể của cả khung hình; sang lượt 2 khi quan sát toàn bộ 5 hộp cùng lúc trên cảnh, ta mới đối chiếu được chính xác từng người với danh sách P1–P5 và phát hiện ngay nếu có người bị gán sai hoặc thiếu.

## 5. File xuất và kết quả tự kiểm (CP4)

| Kiểm tra | Kết quả |
|---|---|
| Tên file MOT 1.1 | `NgoDucTrinh_mot.zip` |
| Tên file CVAT for video 1.1 | `NgoDucTrinh_cvat_video.zip` |
| Số track ID khác nhau trong `gt/gt.txt` (phải là 5) | 5 |
| Frame `outside` không có dòng trong `gt/gt.txt` (đúng / sai) | Đúng |
| Job đã completed trên CVAT máy cá nhân | Đã chuyển trạng thái Completed |

Dán phần tóm tắt in ra từ `src/check_submission.py`:

```text
Số frame in theo CVAT (bắt đầu từ 0). Trong gt.txt, frame_id = frame CVAT + 1.

=== File MOT 1.1: NgoDucTrinh_mot.zip ===
  Số track ID: 5   |   Tổng số box: 666
  [OK]        Đúng 5 track ID.

  Track | Frame có mặt | Số frame | Đoạn vắng (outside)
      1 |   0–149      |      140 | 39–48
      2 |   0–146      |      121 | 110–135
      3 |   0–149      |      150 | -
      4 |   0–149      |      150 | -
      5 |   0–104      |      105 | -


=== File CVAT for video 1.1: NgoDucTrinh_cvat_video.zip ===

  Track | Nhãn   | Frame thấy | Keyframe | KF/100 frame | Frame occluded | Lần bật outside
      0 | person |        140 |       31 |         22.1 |             18 |               1
              Track 0: keyframe ở frame [0, 10, 20, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 49, 50, 51, 52, 55, 60, 70, 73, 80, 90, 100, 110, 120, 130, 140, 149]
      1 | person |        121 |       24 |         19.8 |             13 |               2
              Track 1: keyframe ở frame [0, 10, 20, 30, 40, 50, 60, 70, 80, 100, 106, 107, 108, 109, 136, 137, 138, 139, 140, 142, 143, 144, 145, 146]
      2 | person |        150 |       16 |         10.7 |              0 |               0
              Track 2: keyframe ở frame [0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100, 110, 120, 130, 140, 149]
      3 | person |        150 |       16 |         10.7 |              0 |               0
              Track 3: keyframe ở frame [0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100, 110, 120, 130, 140, 149]
      4 | person |        105 |       18 |         17.1 |             11 |               1
              Track 4: keyframe ở frame [0, 10, 20, 30, 40, 50, 70, 94, 95, 96, 97, 98, 99, 100, 101, 102, 103, 104]

  Tổng: 105 keyframe / 666 frame có mặt = 15.8 keyframe / 100 frame
  [OK]        Đọc được 5 track từ annotations.xml.

=== Tóm tắt ===
  Lỗi: 0   |   Cảnh báo: 0
  Đạt. Dán phần tóm tắt này vào báo cáo mục 5.
```

## 6. Ba câu kết

1. Nếu được gán lại, bạn sẽ đặt keyframe khác ở đâu? Vì sao?

   Nếu được gán lại, tôi sẽ đặt thưa bớt các keyframe ở giai đoạn thoát che khuất của P1 (frame 27–38 và 49–55) và đoạn cuối của P5 (frame 94–104), chỉ đặt tại các mốc đổi trạng thái cờ (`occluded`/`outside`) và điểm đổi hướng thay vì đặt liên tiếp từng frame một. Cách này giúp giảm mật độ keyframe của P1 từ 22.1 xuống khoảng 14–16 KF/100 frame mà độ chính xác nội suy của hộp bao vẫn giữ nguyên.

2. Có chỗ nào bạn không chắc "cùng ID hay ID mới"? Bạn đã quyết định và ghi chú thế nào?

   Có phân vân ở trường hợp của **P4** (em bé áo trắng đi gần sảnh Woolworths) khi bị người mặc áo xanh che khuất từ frame 110 đến 135 (26 frame). Tuy nhiên, vì thời gian khuất dưới 60 frame ($\approx 0.87$ giây), ngay khi lộ diện ở frame 136 vẫn nhận diện rõ đôi giày đỏ, váy hoa và vị trí nằm đúng hướng di chuyển ban đầu nên tôi quyết định **giữ cùng ID** và ghi chú rõ mốc `outside` 110–135.

3. Một lỗi ID trong job của bạn (nếu không còn sót, chọn lỗi đã sửa) có thể làm xe tự lái dự đoán sai chuyển động của người đó như thế nào? Lỗi đó ảnh hưởng MOTA hay IDF1 nhiều hơn?

   Nếu lỗi quên bật `outside` tại frame 39–48 của **P1** không được sửa, bộ theo vết trên xe tự lái sẽ nhận nhầm tọa độ của người đi ngang (P5) gán cho P1, dẫn đến thuật toán ước lượng vận tốc bị tính sai đột biến (tưởng người trong cửa hàng bất ngờ lao ngang ra ngoài với tốc độ cao) và kích hoạt phanh gấp giả. Lỗi gắn nhầm/đổi danh tính xuyên suốt chuỗi thời gian như vậy sẽ làm giảm chỉ số **IDF1** nhiều hơn đáng kể so với MOTA, vì IDF1 đo lường khả năng duy trì đúng một danh tính duy nhất từ đầu đến cuối quỹ đạo.

## 7. Tài liệu tham khảo và công cụ AI đã dùng

- Tài liệu hướng dẫn thực hành Lab 05 — Gán nhãn dữ liệu theo vết đa đối tượng (MOT) với CVAT.
- Bộ dữ liệu MOTChallenge (`MOT17-09`), giấy phép CC BY-NC-SA 3.0.
- Công cụ hỗ trợ: CVAT (local Docker), script kiểm tra `src/check_submission.py`, và trợ lý AI hỗ trợ giải đáp quy tắc gắn cờ `occluded`/`outside`, tối ưu mật độ keyframe và kiểm tra lỗi định dạng tệp xuất.