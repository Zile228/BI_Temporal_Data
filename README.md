# Data Mining for Temporal Data

## Tổng quan
Đây là mã nguồn phục vụ báo cáo giữa kỳ môn **Hệ hỗ trợ quản trị thông minh** với đề tài **Data Mining for Temporal Data** (UEH, 03/2026).

Nhóm thực hiện:
- Thái Hoài An
- Nguyễn Thị Thùy Dương
- Nguyễn Duy Tân
- Lê Vy

Tài liệu báo cáo: [Báo cáo.pdf](./Báo%20cáo.pdf)

## Mục tiêu dự án
Dựa trên dữ liệu thời gian trong bối cảnh quản trị, dự án tập trung:
- Phân tích **thời gian đến khi xảy ra sự kiện** (Survival Analysis) cho bài toán rời bỏ khách hàng.
- Khai phá **đồng xuất hiện** (Association Analysis) để nhận diện cấu hình rủi ro.
- Khai thác **trình tự hành vi** (Sequential Pattern Mining) và **episode theo cửa sổ thời gian** (Episode Mining).
- Minh họa thêm hướng tiếp cận **chuỗi Markov** cho dữ liệu trạng thái theo thời gian.

## Kết quả nổi bật (theo báo cáo)
- Telco Churn có tỷ lệ rời bỏ tổng thể khoảng **26.6%**.
- Hàm sống sót Kaplan-Meier cho thấy sau 72 tháng xác suất duy trì còn khoảng **0.6**.
- Nhóm hợp đồng **Month-to-month** có rủi ro cao nhất; hợp đồng dài hạn (đặc biệt 2 năm) là yếu tố bảo vệ mạnh.
- Trong cohort churn, các cấu hình như `TS=No` và `PM=E-check` thường đồng xuất hiện cùng `CT=Month`.
- Với Retail Rocket:
  - Số session dùng trong thực nghiệm: **3776**.
  - Số sự kiện sau lọc top item: **32,534**.
  - Episode mining dùng **3249** cửa sổ trượt (window=50, step=10).

## Cấu trúc thư mục
```text
.
├── Báo cáo.pdf
└── BI_Temporal_Data
    ├── Data
    │   ├── WA_Fn-UseC_-Telco-Customer-Churn.csv
    │   └── seoul 2022-01-01 to 2024-01-01.csv
    ├── Notebooks
    │   ├── BI_Hình_Ảnh_Minh_Họa.ipynb
    │   ├── BI_Survival_Analysis.ipynb
    │   ├── markov-chain-analysis.ipynb
    │   └── Assosiation_Rule,_Sequence_Analysis.ipynb
    └── README.md
```

## Dữ liệu sử dụng
- **Telco Customer Churn** (Kaggle): dùng cho EDA, Kaplan-Meier, Cox, Association.
- **Seoul Historical Weather Data**: dùng cho Markov chain analysis.
- **Retail Rocket E-commerce Dataset** (Kaggle): dùng cho Sequential/Episode mining.

## Yêu cầu môi trường
- Python 3.10+ (khuyến nghị 3.11/3.12)
- Jupyter Notebook/Lab

Cài nhanh:
```bash
python -m venv .venv
source .venv/bin/activate
pip install -U pip
pip install numpy pandas matplotlib seaborn plotly lifelines networkx kagglehub jupyter
```

## Cách chạy notebook
1. Mở notebook:
```bash
cd BI_Temporal_Data/Notebooks
jupyter lab
```
2. Chạy lần lượt các notebook theo nhu cầu:
- `BI_Hình_Ảnh_Minh_Họa.ipynb`: tạo hình minh họa lý thuyết.
- `BI_Survival_Analysis.ipynb`: EDA + Kaplan-Meier + Cox trên Telco.
- `markov-chain-analysis.ipynb`: ma trận chuyển, tính chất chuỗi Markov trên dữ liệu thời tiết.
- `Assosiation_Rule,_Sequence_Analysis.ipynb`: association rules (Telco) + sequential/episode mining (Retail Rocket).

## Lưu ý khi chạy local
- Một số cell đang dùng đường dẫn Kaggle (`/kaggle/input/...`). Khi chạy local, đổi sang file trong `BI_Temporal_Data/Data/`.
- Notebook có phần `kagglehub.dataset_download(...)` cần internet để tải dữ liệu công khai từ Kaggle.
- Notebook Survival có cell `!pip install -q lifelines`; có thể bỏ qua nếu đã cài trước trong môi trường local.
