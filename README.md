# BÀi 13 : (Bài tập tổng hợp) Dựng README.md cho Dự Án CLB SmartCampus


# PHẦN 1 – HOÀN THIỆN SRS BẰNG HEADING STYLES VÀ AUTO TOC

### 1 & 2. Khung tiêu đề 3 cấp và gán Heading Styles

* **1. Giới thiệu dự án** `[Heading 1]`
  * **1.1. Mục tiêu** `[Heading 2]`
  * **1.2. Đối tượng sử dụng** `[Heading 2]`
* **2. Chức năng hệ thống** `[Heading 1]`
  * **2.1. Quản lý mượn sách** `[Heading 2]`
    * **2.1.1. Luồng mượn sách qua thẻ sinh viên** `[Heading 3]`
  * **2.2. Quản lý trả sách** `[Heading 2]`
* **3. Yêu cầu bảo mật** `[Heading 1]`

### 3. Nội dung mô tả yêu cầu

* **Dưới mục 2. Chức năng hệ thống (Yêu cầu chức năng - Functional Requirements):**
  > Hệ thống cho phép thủ thư thực hiện tra cứu danh mục, tạo phiếu mượn/trả sách tự động và gửi thông báo nhắc hạn tới sinh viên. Sinh viên có thể chủ động xem tình trạng còn/hết của đầu sách và kiểm tra lịch sử mượn thông qua tài khoản cá nhân.

* **Dưới mục 3. Yêu cầu bảo mật (Yêu cầu phi chức năng - Non-functional Requirements):**
  > Toàn bộ thông tin mật khẩu tài khoản người dùng phải được mã hóa một chiều an toàn trước khi lưu vào cơ sở dữ liệu để chống lộ lọt thông tin. Hệ thống phải đảm bảo thời gian phản hồi cho các thao tác tra cứu dữ liệu dưới 2 giây và hoạt động liên tục 24/7 với độ ổn định cao.

### 4. Thao tác chèn và cập nhật Mục lục tự động (Auto TOC)
* **Thao tác tạo TOC:** Đặt con trỏ soạn thảo ở trang đầu tiên $\rightarrow$ Thẻ **References** $\rightarrow$ Chọn **Table of Contents** $\rightarrow$ Chọn mẫu **Automatic Table 1**.
* **Thao tác cập nhật sau khi đẩy mục 3 sang trang sau:** 
  1. Nhấp chuột phải vào bảng Mục lục vừa tạo.
  2. Chọn **Update Field** $\rightarrow$ Tích chọn **Update entire table** $\rightarrow$ Nhấn **OK**.
* **Kết quả số trang thay đổi:**
  * *Trước khi cập nhật:* Mục `3. Yêu cầu bảo mật` hiển thị ở **Trang 1**.
  * *Sau khi cập nhật:* Mục `3. Yêu cầu bảo mật` tự động nhảy sang hiển thị ở **Trang 2**.

---

# PHẦN 2 – CHUẨN HÓA DỮ LIỆU VÀ AUTOFILTER

### 1. Ba lỗi vi phạm 5 Quy tắc Vàng trong bảng dữ liệu gốc

| Lỗi | Vị trí (hàng) | Quy tắc bị vi phạm | Hậu quả kỹ thuật |
| :---: | :---: | :--- | :--- |
| **1** | Hàng 1 (A1:E1) | Không merge (trộn) ô trong vùng dữ liệu | Gây hỏng cấu trúc cột, khiến tính năng AutoFilter và sắp xếp (Sort) bị lỗi hoặc bị vô hiệu hóa. |
| **2** | Hàng 5 | Không để hàng/dòng trống xen giữa | Làm gián đoạn tập dữ liệu (Data Range), Excel sẽ tưởng bảng kết thúc tại hàng 4. |
| **3** | Hàng 6 | Không để dòng tổng cộng xen giữa dữ liệu | Lẫn lộn giữa dữ liệu chi tiết (Record) và dữ liệu tính toán tổng hợp, làm sai lệch kết quả lọc và thống kê. |

### 2. Bảng dữ liệu sau khi sửa chuẩn hóa

| MSSV | Họ Tên | Mã Sách | Ngày Mượn | Tình Trạng |
| :--- | :--- | :--- | :---: | :--- |
| SV001 | Nguyễn Văn An | S001 | 01/10/2026 | Đang mượn |
| SV002 | Trần Thị Bình | S002 | 03/10/2026 | Quá hạn |
| SV003 | Lê Văn Cường | S003 | 10/10/2026 | Đã trả |
| SV004 | Phạm Thu Hà | S099 | 12/10/2026 | Đang mượn |

*(Ghi chú: Tiêu đề lớn được đưa hẳn lên trên tách rời bảng, dòng "Tổng cộng: 4 phiếu" được chuyển xuống dòng riêng biệt nằm ngoài vùng dữ liệu).*

### 3. Phân biệt Record và Field
* **1 Record (Bản ghi / Dòng):** Là một hàng ngang chứa toàn bộ thông tin đầy đủ của một thực thể phiếu mượn.  
  *Ví dụ:* Hàng chứa dữ liệu `[SV001 | Nguyễn Văn An | S001 | 01/10/2026 | Đang mượn]`.
* **1 Field (Trường dữ liệu / Cột):** Là một cột dọc đại diện cho một thuộc tính duy nhất của dữ liệu.  
  *Ví dụ:* Cột `MSSV` hoặc cột `Tình Trạng`.

### 4. Thao tác bật AutoFilter và lọc sinh viên "Quá hạn"
* **Bước 1:** Đặt con trỏ chuột vào một ô bất kỳ trong bảng dữ liệu (ví dụ ô `A1`).
* **Bước 2:** Nhấn tổ hợp phím tắt `Ctrl + Shift + L` để bật AutoFilter (mũi tên trỏ xuống sẽ xuất hiện ở từng ô tiêu đề).
* **Bước 3:** Bấm vào nút mũi tên tại tiêu đề cột **Tình Trạng**.
* **Bước 4:** Bỏ chọn ô `(Select All)`, tích chọn duy nhất ô `Quá hạn` rồi bấm **OK**. Kết quả sẽ chỉ hiển thị duy nhất bản ghi của sinh viên `SV002 - Trần Thị Bình`.

---

# PHẦN 3 – NỐI DỮ LIỆU BẰNG VLOOKUP

### 1. Công thức VLOOKUP lấy Tên Sách
Giả sử chèn thêm cột **Tên Sách** tại cột D (kế bên cột Mã Sách ở ô `C2`):
```excel
=VLOOKUP(C2, DanhMucSach!$A$2:$C$4, 2, FALSE)
```

### PHẦN 4 - SLIDE BÁO CÁO TIẾN ĐỘ

  1. Thiết kế nội dung cho 1 Slide báo cáo (1 Slide – 1 Thông điệp)
  - Assertion Title (Tiêu đề khẳng định kết luận):

    - 25% phiếu mượn đang bị quá hạn và xuất hiện mã sách lỗi cần rà soát lại dữ liệu

  - Content Area (Vùng nội dung trọng tâm):

    - Con số nổi bật: 1 / 4 phiếu mượn (25%) đã quá hạn trả sách; 50% đang mượn; 25% đã hoàn thành trả sách.

    - Cảnh báo dữ liệu: Phát hiện mã S099 của sinh viên Phạm Thu Hà không nằm trong danh mục sách nhà trường.

  - Lựa chọn loại biểu đồ & Lý do:

  - Chọn loại biểu đồ: Biểu đồ tròn khuyết (Donut Chart).

  - Lý do chọn: Phù hợp nhất để thể hiện tỷ lệ cơ cấu phần trăm của từng nhóm trạng thái (Đang mượn, Quá hạn, Đã trả) so với tổng thể 100% dữ liệu mượn sách tháng 10.
