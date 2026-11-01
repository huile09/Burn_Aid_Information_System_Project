# Báo Cáo Đồ Án & Bài Báo Khoa Học (Reports & Paper)

Thư mục này quản lý toàn bộ các văn bản khoa học chính thức của đề tài **BurnAid AI**:

---

## 📁 Cấu Trúc Thư Mục:

```text
report/
├── report.pdf       # Báo cáo khóa luận / đồ án tốt nghiệp chính thức (dạng PDF)
└── paper/           # Bài báo khoa học viết bằng LaTeX và các bản Word đối chiếu
    ├── main.tex     # Mã nguồn bài báo khoa học định dạng chuẩn IEEE / Conference LaTeX
    ├── references.bib # File danh mục trích dẫn y văn quốc tế chuẩn BibTeX (22 tài liệu)
    ├── BurnAid_AI_Research_Paper.docx    # Toàn văn bài báo khoa học đã rà soát liêm chính học thuật
    └── BurnAid_Paper_Detailed_Summary.docx # Bản tóm tắt chi tiết và hướng dẫn phản biện hội đồng
```

---

## 📄 Chi Tiết Các Tài Liệu:

1. **`report.pdf`:**
   - Toàn văn báo cáo đồ án tốt nghiệp hệ thống thông tin, đối chiếu chi tiết từ Chương 1 đến Chương 9.
   - Trọng tâm thực nghiệm tại Chương 7 (trang 79–93): Thiết kế thực nghiệm, lựa chọn mô hình qua 3 random seeds, phân tích trade-off giữa độ phức tạp mô hình và hiệu năng phân loại, đối đầu trực tiếp giữa Curriculum U-Net++ và UPerNet, và khảo sát kiềm chế mặt nạ ảo trên tập ảnh da lành.

2. **`paper/main.tex`:**
   - Tên bài báo: *Burn-Depth Classification and Burn-Lesion Segmentation Using Deep Learning: An Empirical Evaluation of Model Selection Trade-offs*.
   - Chuẩn định dạng IEEE 2 cột, sẵn sàng để biên dịch bằng `pdflatex` hoặc tải lên Overleaf.

3. **`paper/references.bib`:**
   - Đầy đủ 22 trích dẫn y văn quốc tế chuẩn xác (Cirillo et al., Tran et al., Abubakar et al., Liu et al., Boissin et al., Şevik & Mutlu, ConvNeXtV2, UNet++, v.v.).
