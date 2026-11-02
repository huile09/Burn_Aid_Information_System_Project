# BurnAid AI: Hệ Thống Hỗ Trợ Đánh Giá Bỏng & Sơ Cứu Tiền Viện Bằng Học Sâu

[![Python 3.10+](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![PyTorch 2.0+](https://img.shields.io/badge/PyTorch-2.0%2B-red.svg)](https://pytorch.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Hugging Face Spaces](https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Spaces-orange)](https://huggingface.co/spaces/YOUR_USERNAME/BurnAid-AI)
[![Kaggle Dataset](https://img.shields.io/badge/Kaggle-Dataset-20BEFF.svg)](https://www.kaggle.com/datasets/fareselmenshawii/skin-burn-dataset)

---

## 📌 Liên Kết Quan Trọng (Important Links)

* 🌐 **Live Demo (Hugging Face Spaces):** [https://huggingface.co/spaces/YOUR_USERNAME/BurnAid-AI](https://huggingface.co/spaces/YOUR_USERNAME/BurnAid-AI)
* 📊 **Full Dataset (Kaggle):** [Kaggle Skin Burn Detection Benchmark (4,686 images)](https://www.kaggle.com/datasets/fareselmenshawii/skin-burn-dataset)
* 🧠 **Pretrained Model Weights (Google Drive):** [Download ConvNeXtV2 & U-Net++ Models](https://drive.google.com/drive/folders/16Eioi25kgdv-j4CtXtLZ77SiB1kiOxuI?usp=sharing)
* 📄 **Báo Cáo Đồ Án (PDF):** [`report/IS.report.pdf`](report/IS.REPORT.pdf)
* 📝 **Bài Báo Khoa Học (LaTeX):** [`report/paper/main.tex`](report/paper/GROUP_3_PAPER.pdf)
* 🖥️ **Slide Báo Cáo (PDF):** [`slides/Bai_Thuyet_Trinh_BurnAid.pdf`](slides/IS.SLIDES.pdf)

---

## 📖 Giới Thiệu Dự Án (Project Overview)

**BurnAid AI** là hệ thống hỗ trợ chẩn đoán và hướng dẫn sơ cứu bỏng ứng dụng thị giác máy tính và trí tuệ nhân tạo tạo sinh (GenAI/RAG), nhằm hỗ trợ người dân và nhân viên y tế tuyến cơ sở đánh giá nhanh mức độ bỏng, ước lượng diện tích bỏng (%TBSA), và đưa ra khuyến nghị sơ cứu khẩn cấp theo Quyết định 635/QĐ-BYT.

### ✨ Các Tính Năng Cốt Lõi
1. **Quy trình thị giác 2 giai đoạn (2-Stage Computer Vision):**
   * **Stage 1 - Phân loại độ sâu:** Kiến trúc ConvNeXtV2-Nano (14.99M tham số) phân loại 4 lớp (Độ 1 - Ban đỏ, Độ 2 - Phỏng nước, Độ 3 - Hoại tử, Da lành - No Burn) đạt Macro-F1 = 0.8559 và Accuracy = 0.8576 trên 316 ảnh test.
   * **Stage 2 - Phân đoạn tổn thương:** Kiến trúc Curriculum U-Net++ (ResNet-34) khoanh vùng chính xác ranh giới mô tổn thương, đạt Mean Dice = 0.7215 trên tập test và kiềm chế mask ảo trên da lành xuống 6.09% (so với 99.13% ở mô hình thông thường).
2. **Quy tắc tính diện tích %TBSA lâm sàng Việt Nam:** Tích hợp quy tắc các con số 1-3-6-9-18 của GS. Lê Thế Trung và bản đồ 22 vùng giải phẫu cơ thể. Bỏng độ 1 được tính 0% TBSA theo tiêu chuẩn y khoa quốc tế ABA.
3. **Phác đồ hồi sức dịch & Đánh giá nguy cơ tử vong:** Tự động tính toán lượng dịch truyền theo công thức Baxter / Parkland trong 24 giờ đầu và chỉ số tiên lượng tử vong ABSI (Abbreviated Burn Severity Index).
4. **Cơ chế an toàn tiền viện (Safety Override 115):** Khi phát hiện bỏng độ 3, diện tích bỏng lớn hoặc bỏng nghi ngờ đường thở, hệ thống tự động kích hoạt hộp thoại gọi khẩn cấp Cấp cứu 115.
5. **Trợ lý y khoa RAG thông minh:** Kết nối kho tri thức 2.274 đoạn văn bản y khoa bỏng với Groq LLM (hỗ trợ chế độ offline Rule-based fallback khi mất mạng).
6. **Giao diện Web bản địa hợp nhất:** Ứng dụng Single Page Application (HTML5, TailwindCSS, JavaScript) hỗ trợ mở camera trực tiếp trên điện thoại và máy tính để bàn.

---

## 📁 Cấu Trúc Thư Mục Dự Án (Repository Structure)

Cấu trúc thư mục:

```text
BurnAid_AI/
├── README.md                # Giới thiệu project, link Kaggle, link Demo, hướng dẫn
├── requirements.txt         # Danh sách thư viện Python cần cài đặt
├── .gitignore               # Loại trừ các file không tải lên (.env, __pycache__, cache...)
│
├── code/                    # Toàn bộ mã nguồn của hệ thống
│   ├── app/                 # Ứng dụng web, REST API server, RAG và cơ sở dữ liệu
│   │   ├── api_server.py    # FastAPI / Starlette REST API server
│   │   ├── burn_aid_prototype.html # Giao diện Web Frontend Single Page Application
│   │   ├── clinical_rules.py# Bộ quy tắc lâm sàng %TBSA Lê Thế Trung, Parkland, ABSI
│   │   ├── burn_rag.py      # Module RAG tư vấn y khoa kết nối Groq LLM
│   │   ├── database.py      # Module quản trị cơ sở dữ liệu SQLite
│   │   ├── knowledge_base_burns.txt # Kho dữ liệu 2.274 đoạn tri thức y học bỏng
│   │   └── burnaid.db       # Cơ sở dữ liệu SQLite khởi tạo mẫu
│   ├── models/              # Trọng số mô hình học sâu và tài liệu hướng dẫn
│   │   ├── convnextv2_burn_4class_best.pth  # Trọng số phân loại ConvNeXtV2 (57.2 MB)
│   │   ├── best_random_curriculum_seed2026.pt # Trọng số phân đoạn U-Net++ (99.7 MB)
│   │   └── README.md        # Link tải Google Drive và thông số kiến trúc
│   ├── notebooks/           # Jupyter Notebook huấn luyện và đánh giá mô hình
│   │   └── Burn_AID_Notebook.ipynb
│   ├── experiments/         # Nhật ký huấn luyện và số liệu đánh giá thực nghiệm
│   │   └── Burn_Training_History.xlsx
│   ├── assets/              # Tài nguyên hình ảnh (Sơ đồ giải phẫu GS. Lê Thế Trung)
│   │   └── body_proportions_le_the_trung.png
│   └── Chay_He_Thong.bat    # Script khởi chạy 1-click trên hệ điều hành Windows
│
├── data/                    # Chứa các file ảnh mẫu nhỏ để kiểm thử nhanh
│   ├── README.md            # Mô tả ảnh mẫu và link tới bộ dữ liệu đầy đủ trên Kaggle
│   ├── test_burn_degree2.jpg# Ảnh mẫu bỏng độ 2 (phỏng nước trung bì)
│   ├── test_burn_degree3.jpg# Ảnh mẫu bỏng độ 3 (hoại tử sâu)
│   ├── test_low_confidence_burn.jpg # Ảnh mẫu ca bỏng ranh giới phức tạp
│   └── test_normal_skin.jpg # Ảnh mẫu da lành bình thường (kiểm tra kiềm chế mask ảo)
│
├── report/                  # Báo cáo và bài báo khoa học
│   ├── IS.REPORT.pdf           # Báo cáo đồ án (dạng PDF)
│   └── paper/               # Bài báo khoa học viết bằng LaTeX
│       ├── main.tex         # Mã nguồn bài báo chuẩn định dạng IEEE LaTeX
│       ├── GROUP_03_PAPER  # Bản PDF paper
│       └── traininglog/  # Các csv có trong paper
│
└── slides/                  # Slide báo cáo thuyết trình
    ├── IS.SLIDES.pdf  # Slide thuyết trình đồ án (dạng PDF)
```

---

## 🚀 Hướng Dẫn Cài Đặt & Chạy Hệ Thống (Quick Start)

### 1. Yêu cầu hệ thống
* Python 3.10 trở lên.
* Khuyến nghị GPU NVIDIA (tối thiểu 4GB VRAM) hoặc CPU 4 nhân trở lên (hệ thống hỗ trợ chạy thuần CPU).

### 2. Cài đặt môi trường
Mở Terminal / Command Prompt tại thư mục gốc của dự án:

```bash
# Tạo môi trường ảo (khuyến nghị)
python -m venv venv

# Kích hoạt môi trường ảo:
# Trên Windows:
venv\Scripts\activate
# Trên Linux/macOS:
source venv/bin/activate

# Cài đặt toàn bộ thư viện cần thiết:
pip install -r requirements.txt
```

### 3. Tải trọng số mô hình (Pretrained Weights)
Do kích thước trọng số mô hình lớn, các file trọng số được lưu trữ an toàn trên Google Drive:
* 👉 **[Link tải trọng số mô hình từ Google Drive](https://drive.google.com/drive/folders/16Eioi25kgdv-j4CtXtLZ77SiB1kiOxuI?usp=sharing)**
* Tải 2 file `convnextv2_burn_4class_best.pth` và `best_random_curriculum_seed2026.pt` đặt vào thư mục `code/models/`.

### 4. Khởi chạy ứng dụng

#### Cách 1: Khởi chạy 1-Click trên Windows
Nhấp đúp chuột vào file:
```
code/Chay_He_Thong.bat
```
Script sẽ tự động kiểm tra Python, thư viện, giải phóng cổng mạng và mở giao diện ứng dụng.

#### Cách 2: Khởi chạy bằng dòng lệnh
```bash
cd code/app
python api_server.py
```

Mở trình duyệt web và truy cập địa chỉ:
👉 **[http://127.0.0.1:8000](http://127.0.0.1:8000)**

---

## 🧪 Dữ Liệu Huấn Luyện & Thử Nghiệm

* **Bộ dữ liệu phân loại:** 4.686 ảnh (Train: 3.908 ảnh - 83.40%, Validation: 462 ảnh - 9.86%, Test: 316 ảnh - 6.74%).
* **Bộ dữ liệu phân đoạn:** 2.198 records (300 manual polygon, 921 pseudo-masks qua Auto-QC, 977 ảnh nền da lành None).
* **Kiểm tra trên ảnh mẫu nhỏ:** Bạn có thể sử dụng trực tiếp các file ảnh trong thư mục `data/` (`test_burn_degree2.jpg`, `test_burn_degree3.jpg`, `test_normal_skin.jpg`) để tải lên thử nghiệm hệ thống.

---

## 👥 Nhóm Tác Giả & Đơn Vị Thực Hiện
* **Sinh viên thực hiện:**
  * Lê Huỳnh Đức Huy
  * Hà Phương Thảo
  * Mai Hồ Quốc Túy
  * Nguyễn Ngọc Khánh Uyên
  * Nguyễn Khắc Lưu Vũ
* **Đơn vị:** Viện Công nghệ Thông minh và Tương tác, Đại học Kinh tế Thành phố Hồ Chí Minh (UEH).

---

## ⚖️ Giấy Phép & Tuyên Bố Miễn Trừ Trách Nhiệm Y Khoa
* **Giấy phép:** [MIT License](LICENSE).
* **Tuyên bố y tế (Medical Disclaimer):** BurnAid AI là hệ thống hỗ trợ ra quyết định mang tính chất tham khảo học thuật và sơ cứu ban đầu, không thay thế chẩn đoán chuyên khoa của bác sĩ. Trong các trường hợp bỏng nặng, cần liên hệ ngay cơ sở y tế gần nhất hoặc gọi cấp cứu 115.
