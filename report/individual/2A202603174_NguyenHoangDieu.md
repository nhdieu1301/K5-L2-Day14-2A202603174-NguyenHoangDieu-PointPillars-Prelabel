# Báo cáo Lab Day 14 — Pre-label 3D bằng PointPillars pre-trained (VF LiDAR)

- **Họ và tên:** Nguyễn Hoàng Diệu
- **MSSV:** 2A202603174
- **Seed tag:** `seed_tag=393590736f`

---

## 1. Dự đoán trước sweep (Bước 5b)

- **Kết quả đo cấu hình gốc trên Tập A (`s01f01`, `s03f41`, `s05f28`):** GT 43 hộp, dự đoán 93 hộp (khớp 36) $\rightarrow$ **Xóa 57, Thêm 7, Sửa 2 $\rightarrow$ Tổng chi phí: `25.1`**.
- **Dự đoán tham số & lý do:** Với cấu hình gốc (`score_thr=0.1`, `min_points=0`), mô hình sinh ra tới 93 hộp trên tổng số 43 vật thể thật, dẫn đến **57 hộp thừa phải xóa** (chiếm `17.1 / 25.1` tổng chi phí, đặc biệt ở `s03f41` dư 33 hộp và `s05f28` dư 17 hộp) do các dự đoán nhiễu có điểm tin cậy thấp và ít điểm LiDAR. Do đó, dự đoán việc **tăng `score_thr` (lên khoảng `0.3` – `0.4`) kết hợp tăng `min_points` (`5` – `10`)** sẽ giảm công sửa nhiều nhất nhờ lọc bỏ lượng lớn hộp giả này, đồng thời vẫn giữ lại được phần lớn các phương tiện thật gần xe.