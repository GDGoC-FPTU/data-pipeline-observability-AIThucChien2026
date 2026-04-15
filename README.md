[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23574214&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student ID:** 2A202600133
**Name:** Nguyen Ba Hao

---

## Mo ta

Bài Lab này thực hiện việc xây dựng một hệ thống ETL (Extract, Transform, Load) tự động và áp dụng các kỹ thuật quan sát dữ liệu (Data Observability). Em đã hoàn thành các nhiệm vụ:
1. Xây dựng ETL Pipeline làm sạch dữ liệu từ file JSON và lưu vào CSV.
2. Thiết lập cơ chế kiểm soát chất lượng dữ liệu (Validation) để loại bỏ các bản ghi không hợp lệ.
3. Thực hiện Stress Test để chứng minh ảnh hưởng của chất lượng dữ liệu đối với hiệu suất của AI Agent.
4. Ghi nhận nhật ký (logging) và dấu thời gian (timestamp) để tăng tính minh bạch cho quy trình.

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas pytest
```

### Chay ETL Pipeline
```bash
python solution.py
```
Sau khi chạy, file `processed_data.csv` sẽ được tạo ra trong thư mục gốc.

### Chay Agent Simulation (Stress Test)
1. Tạo dữ liệu rác: `python generate_garbage.py`
2. Chạy mô phỏng: `python agent_simulation.py`

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── raw_data.json            # Dữ liệu nguồn (Input)
├── processed_data.csv       # Dữ liệu sau khi xử lý (Output)
├── garbage_data.csv         # Dữ liệu phục vụ stress test
├── experiment_report.md     # Báo cáo phân tích thí nghiệm
├── agent_simulation.py      # Script mô phỏng AI Agent
└── README.md                # Tài liệu hướng dẫn này
```

---

## Ket qua

- **Trích xuất:** Hoàn tất việc đọc dữ liệu từ `raw_data.json`.
- **Làm sạch:** Hệ thống đã giữ lại 3 bản ghi hợp lệ và loại bỏ 2 bản ghi bị lỗi (thiếu danh mục hoặc giá sai).
- **Chuyển đổi:** Đã tính toán giá chiết khấu, chuẩn hóa tên danh mục và thêm dấu thời gian xử lý.
- **Thử nghiệm:** Chứng minh được Agent phản hồi sai lệch hoàn toàn khi gặp dữ liệu chứa giá trị ngoại lai (outliers) cực đoan.
