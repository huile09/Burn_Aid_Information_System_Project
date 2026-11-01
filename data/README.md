# Dữ Liệu Mẫu Kiểm Thử (Sample Data) & Liên Kết Bộ Dữ Liệu Đầy Đủ

Thư mục này chỉ lưu trữ các file ảnh mẫu có dung lượng nhỏ phục vụ việc kiểm thử nhanh các tính năng của hệ thống BurnAid AI, tuân thủ đúng quy chuẩn nộp mã nguồn GitHub.

---

## 🔗 Liên Kết Bộ Dữ Liệu Đầy Đủ Trên Kaggle

Bộ dữ liệu đầy đủ bao gồm 4.686 ảnh lâm sàng phục vụ huấn luyện và đánh giá mô hình học sâu được công khai trên Kaggle:

👉 **[Kaggle Dataset: Skin Burn Detection Benchmark](https://www.kaggle.com/datasets/fareselmenshawii/skin-burn-dataset)** *(Abbas, 2020)*

### Phân Bố Tập Dữ Liệu Chuẩn:
- **Tập Huấn luyện (Train):** 3.908 ảnh (83.40%)
- **Tập Kiểm tra (Validation):** 462 ảnh (9.86%)
- **Tập Thử nghiệm (Test):** 316 ảnh (6.74%)
- **Tổng cộng:** 4.686 ảnh (Độ 1: 1.259 ảnh, Độ 2: 1.201 ảnh, Độ 3: 1.055 ảnh, Da lành: 1.171 ảnh).

---

## 🖼️ Danh Sách Ảnh Mẫu Nhỏ Trong Thư Mục Này

Bạn có thể sử dụng các file ảnh mẫu sau để kiểm tra ngay trên giao diện web hoặc REST API:

1. **`test_burn_degree2.jpg` (57 KB):**
   - **Tổn thương:** Bỏng độ II (phỏng nước trung bì, phồng rộp, bề mặt ướt đỏ).
   - **Mục đích kiểm thử:** Kiểm tra khả năng phân loại độ 2 và phân đoạn diện tích phỏng nước.

2. **`test_burn_degree3.jpg` (101 KB):**
   - **Tổn thương:** Bỏng độ III (hoại tử sâu, đóng vảy da hoại tử trắng đục hoặc cháy đen).
   - **Mục đích kiểm thử:** Kiểm tra tính năng cảnh báo an toàn và kích hoạt hộp thoại gọi **Cấp cứu 115** khẩn cấp.

3. **`test_normal_skin.jpg` (36 KB):**
   - **Tổn thương:** Da lành bình thường, không có tổn thương nhiệt.
   - **Mục đích kiểm thử:** Kiểm tra khả năng kiềm chế ranh giới của mô hình, đảm bảo hệ thống không vẽ mặt nạ ảo (phantom mask) lên vùng da bình thường.

4. **`test_low_confidence_burn.jpg` (104 KB):**
   - **Tổn thương:** Vùng bỏng có ranh giới phức tạp, ánh sáng mờ.
   - **Mục đích kiểm thử:** Kiểm tra độ ổn định của thuật toán xử lý ảnh trong điều kiện ánh sáng khó.
