# Kế hoạch thực hiện bài Lab 10: Data Pipeline & Data Observability

## 1. Mục tiêu
Hoàn thành hệ thống ETL tự động, thực hiện quan sát dữ liệu và báo cáo tác động của chất lượng dữ liệu đối với AI Agent.

## 2. Các bước thực hiện

### Bước 1: Chuẩn bị môi trường
- [x] Cài đặt thư viện cần thiết: `pip install pandas pytest`.
- [x] Kiểm tra cấu trúc thư mục hiện tại.

### Bước 2: Triển khai ETL Pipeline (`solution.py`)
- [x] **Extract**: Đọc dữ liệu từ `raw_data.json` sử dụng `json.load`. Xử lý lỗi nếu file không tồn tại.
- [x] **Validate**: Lọc bỏ các bản ghi có `price <= 0` hoặc `category` rỗng. In ra số lượng bản ghi hợp lệ và bị loại để đảm bảo tính quan sát (Observability).
- [x] **Transform**: 
    - [x] Tạo DataFrame từ dữ liệu hợp lệ.
    - [x] Thêm cột `discounted_price` (giảm 10% so với `price`).
    - [x] Chuẩn hóa `category` thành Title Case.
    - [x] Thêm cột `processed_at` với timestamp hiện tại.
- [x] **Load**: Lưu DataFrame kết quả vào `processed_data.csv`.

### Bước 3: Thử nghiệm Stress Test & Quan sát AI Agent
- [x] Chạy `solution.py` để tạo dữ liệu sạch (`processed_data.csv`).
- [x] Chạy `generate_garbage.py` để tạo dữ liệu rác (`garbage_data.csv`).
- [x] Chạy `agent_simulation.py` để ghi lại phản hồi của Agent trong hai trường hợp:
    - [x] Với dữ liệu sạch.
    - [x] Với dữ liệu rác.

### Bước 4: Hoàn thiện báo cáo và tài liệu
- [x] **Cập nhật `experiment_report.md`**:
    - [x] Điền bảng kết quả thử nghiệm.
    - [x] Viết phần phân tích (ít nhất 50 từ) về lý do Agent thất bại khi gặp dữ liệu rác.
    - [x] Viết kết luận về tầm quan trọng của chất lượng dữ liệu.
- [x] **Cập nhật `README.md`**:
    - [x] Điền thông tin cá nhân.
    - [x] Mô tả ngắn gọn về bài làm.
    - [x] Hướng dẫn cách chạy code và tóm tắt kết quả.

### Bước 5: Kiểm tra và Nộp bài
- [x] Chạy test nội bộ bằng lệnh: `pytest tests/test_autograder.py`.
- [x] Đảm bảo tất cả các test case đều đạt điểm tối đa (100/100).
- [ ] Thực hiện `git add`, `git commit`, và `git push` để nộp bài lên GitHub Classroom.

## 3. Tiêu chí đánh giá (Rubric) - Đã đạt 100/100
- ETL chạy không lỗi: 20đ (Pass)
- Validation đúng quy tắc: 10đ (Pass)
- Transformation đúng logic: 10đ (Pass)
- Logging (Observability): 10đ (Pass)
- Timestamp (Observability): 10đ (Pass)
- Báo cáo Stress Test đầy đủ: 10đ (Pass)
- Phân tích chuyên sâu (>= 50 từ): 10đ (Pass)
- Cấu trúc thư mục đúng yêu cầu: 10đ (Pass)
- README đầy đủ thông tin: 10đ (Pass)
