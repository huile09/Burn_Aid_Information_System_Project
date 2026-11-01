# Mã Nguồn Hệ Thống (System Codebase)

Thư mục `code/` chứa toàn bộ mã nguồn thực thi, kiến trúc mô hình học sâu, notebook thực nghiệm và giao diện của hệ thống **BurnAid AI**:

---

## 📁 Cấu Trúc Module:

```text
code/
├── app/                 # Ứng dụng web, REST API server, RAG và cơ sở dữ liệu
│   ├── api_server.py    # FastAPI / Starlette REST API backend
│   ├── burn_aid_prototype.html # Giao diện Web Frontend Single Page Application
│   ├── clinical_rules.py# Bộ quy tắc lâm sàng %TBSA Lê Thế Trung, Parkland, ABSI
│   ├── burn_rag.py      # Module RAG tư vấn y khoa kết nối Groq LLM
│   ├── database.py      # Module quản trị cơ sở dữ liệu SQLite
│   ├── knowledge_base_burns.txt # Kho dữ liệu 2.274 đoạn tri thức y học bỏng
│   ├── knowledge_base_burns_full.json # Dữ liệu RAG dạng JSON có metadata
│   ├── burnaid.db       # Cơ sở dữ liệu SQLite khởi tạo mẫu
│   ├── BurnAid_Database_v9.1_Full_Production.sql # Script SQL khởi tạo schema
│   └── requirements.txt # Thư viện cần cho backend
│
├── models/              # Trọng số mô hình và tài liệu cấu trúc mạng
│   ├── convnextv2_burn_4class_best.pth  # Trọng số ConvNeXtV2-Nano (57.2 MB)
│   ├── best_random_curriculum_seed2026.pt # Trọng số Curriculum U-Net++ ResNet-34 (99.7 MB)
│   └── README.md        # Hướng dẫn tải trọng số từ Google Drive
│
├── notebooks/           # Jupyter Notebooks huấn luyện và đánh giá mô hình
│   ├── Burn_AID_Notebook.ipynb # Notebook thực nghiệm toàn diện
│   └── README.md
│
├── experiments/         # Lịch sử và bảng thống kê thực nghiệm
│   ├── Burn_Training_History.xlsx # File Excel ghi nhận quá trình train qua các epoch
│   └── README.md
│
├── assets/              # Tài nguyên đồ họa
│   └── body_proportions_le_the_trung.png # Bảng tỷ lệ diện tích cơ thể GS. Lê Thế Trung
│
└── Chay_He_Thong.bat    # Script khởi chạy nhanh hệ thống trên Windows
```

---

## ⚡ Hướng Dẫn Khởi Chạy Nhanh:

1. **Chạy 1-Click trên Windows:** Nhấp đúp vào `Chay_He_Thong.bat`.
2. **Chạy qua Terminal:**
   ```bash
   cd code/app
   python api_server.py
   ```
   Sau đó mở trình duyệt tại: `http://127.0.0.1:8000`.
