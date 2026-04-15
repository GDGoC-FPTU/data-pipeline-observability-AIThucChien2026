# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600133
**Name:** Nguyen Ba Hao
**Date:** Wednesday, April 15, 2026

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 10 | Dữ liệu chính xác và hợp lệ giúp Agent đưa ra câu trả lời hợp lý. |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 2 | Dữ liệu chứa các giá trị ngoại lai (outliers) cực đoan làm Agent đưa ra kết quả vô lý. |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Agent trả lời sai khi dùng Garbage Data vì bộ dữ liệu này chứa nhiều vấn đề về chất lượng dữ liệu. Cụ thể:
1. **Outliers (Giá trị ngoại lai):** Sự xuất hiện của "Nuclear Reactor" với mức giá 999,999 đô la là một ví dụ điển hình về dữ liệu không thực tế. Do logic của Agent là tìm kiếm sản phẩm có giá cao nhất trong danh mục, nó đã chọn ngay bản ghi này mà không có cơ chế kiểm tra tính hợp lý.
2. **Duplicate IDs (Trùng lặp ID):** Việc có nhiều bản ghi chung ID nhưng nội dung khác nhau làm nhiễu hệ thống, khiến việc truy xuất thông tin không nhất quán.
3. **Wrong Data Types (Sai kiểu dữ liệu):** Bản ghi "Broken Chair" có giá là chuỗi "ten dollars" thay vì số, có thể gây lỗi tính toán nếu Agent cần thực hiện phép toán.
4. **Null Values (Giá trị rỗng):** Các bản ghi thiếu thông tin sản phẩm hoặc danh mục làm cho Agent không thể hiểu được bối cảnh của dữ liệu, dẫn đến phản hồi mơ hồ hoặc sai lệch hoàn toàn.

Chính vì những lỗi này, Agent dù có "thông minh" đến đâu cũng sẽ đưa ra kết quả sai lệch nếu đầu vào bị "nhiễm độc".

---

## 3. Ket luan

**Quality Data > Quality Prompt?**

Tôi hoàn toàn đồng ý. Một prompt tốt có thể giúp Agent hiểu câu hỏi, nhưng nếu dữ liệu nền tảng (Knowledge Base) không chính xác, Agent sẽ bị dẫn dắt bởi thông tin sai lệch ("Garbage In, Garbage Out"). Do đó, việc xây dựng một ETL Pipeline mạnh mẽ để làm sạch và quan sát dữ liệu là bước quan trọng nhất trong việc xây dựng các hệ thống AI tin cậy.
