# REGISTER & SETUP AWS ACCOUNT

## 1. Requirements:

- Trước khi bắt đầu, ta cần chuẩn bị sẵn:
  - __Email__:
    - Nếu lập tài khoản cá nhân
    - Không nên sử dụng email công ty
    - Nếu lập cho doanh nghiệp, nên dùng email alias dạng nhóm vì người tạo ban đầu có thể đổi vai trò
  - __Số điện thoại__ nhận được SMS/cuộc gọi để xác thực
  - __Thẻ tín dụng/ghi nợ__
  - __Địa chỉ liên hệ__

## 2. Các bước đăng ký tài khoản:

- __Bước 1__: Truy cập aws.amazon.com, và nhấn `Create an AWS Account`

![image.png](https://images.viblo.asia/c68f5a4e-ef97-45ba-ac0e-a705ff5bc783.png)

- __Bước 2__: Điền thông tin email và account name

![Email&AccountName](https://images.viblo.asia/f664086c-090a-4d65-80a0-8032234ef7ee.png)

- __Bước 3__: Xác thực địa chỉ email

![EmailVerification](https://images.viblo.asia/d3895586-def9-4d76-bbf8-5dcb8334a1d6.png)

- __Bước 4__: Nhập mật khẩu tài khoản root

![RootPassword](https://images.viblo.asia/a21a5a46-684b-4d42-b407-c8e4255ecfbd.png)

- __Bước 5__: Chọn plan cho 1 tài khoản AWS: Trong phần này ta sẽ chọn Free Plan

![Choosing-Plan](https://images.viblo.asia/bc8cafaa-9fc2-41d6-babf-a51c3642ff4b.png)

- __Bước 6__: Nhập thông tin liên hệ:
  - Ta sẽ chọn __Personal Account__ (Đối với __Business Account__ - ta cần dùng email tương ứng với tổ chức tại bước 2)

![Contact-Information](https://images.viblo.asia/a25b8eaf-5798-444e-9bba-e40041e4fcda.png)

- __Bước 7__: Nhập thông tin thanh toán:

![Billing-Information](https://images.viblo.asia/b18880f7-29d8-4eaf-9a70-b51292361d0b.png)

- __Bước 8__: Nhập số điện thoại xác thực:
  - **Chúng ta cần cung cấp số điện thoại như step 6 tại đây.** **- Có 2 phương thức có thể chọn để xác thực là SMS và thông qua Phone Call.** **-**
  - **Thường thì nếu SMS có vấn đề chúng ta mới chọn Phone Call (Voice Call)**

![Phone-Verification](https://images.viblo.asia/3a5e9031-fb52-49da-b32a-06587873ae4b.png)

- __Bước 9__: Hoàn thành đăng ký tài khoản:

![Phone-confirmed](https://images.viblo.asia/07404894-147f-401e-8910-d57866921312.png)

- __Bước 10__: Check inbox email

![Confirmed-Email](https://images.viblo.asia/165ad746-9486-4106-8d03-0b60045cf0b9.png)


## 3. Một số sự cố thường gặp và cách khắc phục:

### 3.1. Sự cố thẻ bị từ chối:  Sử dụng thẻ ghi nợ/tín dụng có bật giao dịch trực tuyến

### 3.2. Sự cố xác minh qua điện thoại không thành công: Sử dụng gọi thoại thay cho SMS

### 3.3. Sự cố tài khoản đang chờ xử lý: Chờ từ 30 - 60p, kiểm tra thư mục thư rác tìm email xác nhận

### 3.4. Sự cố Amazon phát hiện thông tin thông tin chúng ta sử dụng đã được dùng để tạo tài khoản trước đây: Phải sử dụng email và thẻ khác

![Warning-popup](https://images.viblo.asia/c21eed04-9d7d-4376-bfa6-4138dfd66d54.png)


## 4. Chú ý:

- Sau 6 tháng (hoặc khi hết 200$ credits), tài khoản Free Plan sẽ không bị khoá ngay, nhưng có quy trình rõ ràng:
  - Sử dụng được __Always Free__ services với hơn 30 dịch vụ
  - Nếu không upgrade lên __Paid Plan__, tài khoản sẽ bị đóng tự động và dữ liệu bị xoá sau 90 ngày

| Thời gian / Sự kiện                     | Điều gì xảy ra?                                                                       | Bạn còn dùng được gì?           |
| ------------------------------------------ | ----------------------------------------------------------------------------------------- | -------------------------------------- |
| **Trong 6 tháng**                   | Dùng credits $200 + Always Free. Không bị charge tiền.                                | Hầu hết dịch vụ (giới hạn)       |
| **Hết credits hoặc đủ 6 tháng** | Free Plan **kết thúc** . AWS gửi thông báo (email + console).                 | Always Free vẫn dùng được         |
| **Sau khi Free Plan hết**           | Bạn**phải upgrade lên Paid Plan**trong **90 ngày** .                      | Always Free + trả phí bình thường |
| **Sau 90 ngày không upgrade**      | AWS**đóng vĩnh viễn tài khoản**và **xóa toàn bộ resource + data** . | Mất hết tài khoản                  |
