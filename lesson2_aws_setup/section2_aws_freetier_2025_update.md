#  AWS FREE TIER 15/07/2025

- __AWS__ công bố thay đổi chương trình Free Tier từ 15/07/2025, chuyển từ mô hình giới hạn giờ sử dụng sang cấp credit trực tiếp
- Người dùng mới nhận được:
  - __100$__ credit ngay lập tức
  - Kiếm thêm __100$__ thông qua 5 nhiệm vụ thực hành
- Chương trình mới linh hoạt hơn nhưng có thời hạn ngắn hơn 6 tháng

## 1. Có gì mới?

- Trước đây, ta được miễn phí

  - __750 giờ__ sử dụng __EC2 t2.micro__
  - __1M__ request Lambda function
- Thì nay, mô hình mới tập trung vào việc cấp AWS credits:

  - __Nhận ngay 100$ credit ngay sau khi đăng ký tài khoản thành công__
  - __Kiếm thêm 100$ credit__ bằng cách hoàn thành 5 nhiệm vụ thực hành cơ bản trên AWS

  ![comapre.png](https://images.viblo.asia/02c707a8-6376-4b23-9bb6-85e16f7046a3.png)
- Bảng so sánh:

| Tiêu chí                        | Free Tier cũ                                                                                  | Free Tier mới                                                                                         |
| --------------------------------- | ---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| **Thời hạn**              | 12 tháng miễn phí                                                                           | 6 tháng (hoặc đến khi hết credit)                                                                 |
| **Cơ chế miễn phí**     | Miễn phí theo hạn mức mỗi tháng (ví dụ: 750 giờ EC2 t2.micro, 1 triệu req Lambda...) | Được cấp 100$ credit + tối đa 100$ nữa nếu hoàn thành 5 nhiệm vụ                         |
| **Cách dùng**             | Dùng trong hạn mức, vượt thì bị tính phí                                              | Tự do sử dụng các dịch vụ nằm trong danh sách hỗ trợ, trong phạm vi số credit được cấp |
| **Kết thúc gói**         | Tài khoản vẫn hoạt động, chỉ bị tính phí nếu vượt mức                            | Tài khoản sẽ bị đóng nếu không nâng cấp sau 6 tháng hoặc khi hết credit                   |
| **Phân loại tài khoản** | Không có, chỉ một loại duy nhất                                                          | Có 2 loại: Free Plan và Paid Plan                                                                   |
| **Truy cập dịch vụ**     | Toàn quyền truy cập                                                                         | Free Plan bị giới hạn một số dịch vụ dễ làm cạn credit hoặc yêu cầu phần cứng           |
| **Always Free**             | Có                                                                                            | Có (vẫn giữ nguyên hơn 30 dịch vụ Always Free)                                                  |

- Khi đăng ký, ta có 2 lựa chọn:
  - __Gói Free Account Plan__:
    - Đảm bảo bạn sẽ không bị tính phí cho đến khi chủ động nâng cấp
    - Hết hạn sau 6 tháng hoặc hết credit
    - Một số dịch vụ doanh nghiệp bị giới hạn
  - __Gói Paid Account Plan__:
    - Hệ thống tự động trừ vào số credit ta có
    - Khi dùng hết credit, chi phí phát sinh sẽ được tính theo giá on-demand
  - Khi nâng cấp lên gói Paid, số credit còn lại vẫn có hiệu lực trong vòng 12 tháng tính từ ngày đăng ký

## 2. Nhận thêm 100$ credit:

- Để nhận thêm 100$, ta cần hoàn thành 5 bài lab đơn giản, được thiết kế để giúp người mới làm quen với các building block quan trọng của AWS
- Với mỗi bài hoàn thành, ta nhận được 20$ credit
- Ta có thể theo dõi tiến trình nhận credit này ngay trên widget __Explore AWS__ trong AWS Management Console:

![Explore AWS](https://images.viblo.asia/c134ac4e-5f76-44c4-9fa6-6776b88d1874.png)

- 5 bài lab bao gồm:

### 2.1. AWS Budgets:

- Bài lab này giúp ta học cách thiết lập ngân sách và cảnh báo để quản lý tài khoản hiệu quả
- Giúp tránh phát sinh chi phí không mong muốn sau này
- __Bước 1__: Trong widget __Explore AWS__, tìm và chọn __Set up a cost budget using AWS Budgets__

![Cost 1.png](https://images.viblo.asia/78aae265-81d8-4a25-ba75-246c05f7d764.png)

&rarr; Ta sẽ được chuyển đến trang AWS Billing and Cost Management

- __Bước 2__: Chọn __Use a template (simplified)__ cho đơn giản hoá
- __Bước 3__: Chọn __Monthly cost budget__, sau đó nhập số tiền dự kiến chi tiêu hàng tháng (ví dụ 10$)

&rarr; Hệ thống sẽ gửi email cảnh báo nếu chi phí thực tế hoặc dự báo vượt quá con số này:

![Cost 2.png](https://images.viblo.asia/df589cae-323d-4d8e-8336-437fd2be5872.png)

- __Bước 4__: Điền các thông tin cần thiết và hoàn tất

![Cost 6.png](https://images.viblo.asia/95a6cc53-ec7e-4b08-856e-5aed6ea30b3c.png)

- Sau khi tạo budget thành công, ta vào mục __Credits__ trong menu bên trái của trang __Billing sẽ thấy 20$ được cộng vào tài khoản:__

![Cost 7.png](https://images.viblo.asia/e5e7e2fb-a27d-4c08-b58f-383bcf461f3f.png)

### 2.2. AWS EC2:

- Bài lab này hướng dẫn cách khởi chạy và tắt một máy chủ ảo EC2 (Elastic Compute Cloud)
- __Bước 1__: Từ widget __Explore AWS__, chọn nhiệm vụ __Launch an instance using EC2__ để bắt đầu

![Ec2-1.png](https://images.viblo.asia/d33d287f-10e6-4c15-b30b-8652a71b3e75.png)

- __Bước 2__: Làm theo các bước của tutorial, giữ nguyên hầu hết các cài đặt mặc định như AMI (Amazon Machine Image), Instance Type, Network, Storage

![EC2-3.png](https://images.viblo.asia/caaeeeb0-1df5-4aad-bd07-1d27f8e05d66.png)

- __Bước 3__: Trong phần __Key pair__, nhấn __Create new key pair__, đặt tên và __lưu lại file__ `.pem` được tải về

![](https://images.viblo.asia/full/6d49a8d4-c1fb-46ef-b2ed-97b27811c7e1.png)

- __Bước 4__: Nhấn __Launch Instance__, đi đến trang quản lý EC2, chọn máy chủ vừa tạo, và __Terminate instance__ để hoàn thành nhiệm vụ

![EC2-12.png](https://images.viblo.asia/c8155ade-799d-4797-82ae-adc199cd8d49.png)

### 2.3. AWS Bedrock:

- Nhiệm vụ này yêu cầu sử dụng một mô hình AI (foundation model) trong môi trường Bedrock playground để tạo ra một response
- __Bước 1__: Từ widget __Explore AWS__, chọn nhiệm vụ __Use a foundation model in the Amazon Bedrock playground__

![Bedrock1.png](https://images.viblo.asia/2ebd92b2-8011-4360-b772-4c1275b790b8.png)

- __Bước 2__: Yêu cầu truy cập model:
  - Nếu là lần đầu truy cập Bedrock, ta sẽ cần yêu cầu cấp quyền truy cập model
  - Trên trang `Model Access` (https://us-east-1.console.aws.amazon.com/bedrock/home/modelaccess), hãy chọn các model của Amazon (Nova Lite, Titan Text G1 - Lite)
  - Sau đó cuộn xuống dưới cùng nhấn __Save Changes__

![Bedrock4.png](https://images.viblo.asia/c380ba68-b7ee-487e-a73a-c1af882a37d4.png)

![](https://images.viblo.asia/full/dfbf6cad-f6f8-45cc-a899-0fbc0e0ef9e6.png)

- __Bước 3__: Quay lại trang __Playground__, nhấn __Select model__, chọn 1 model của Amazon ta vừa cấp quyền và __Apply__

![Bedrock2.png](https://images.viblo.asia/86f77aa8-c6d9-4926-99a0-f76af8b8df70.png)

![Bedrock6.png](https://images.viblo.asia/3478cf8e-2cb2-4570-9d6e-d6b54aebda53.png)

- __Bước 4__: Trong input chat, nhập 1 câu hỏi bất kỳ và __Run__
- Khi model trả về response, ta đã hoàn thành nhiệm vụ

### 2.4. AWS Lambda:

- Nhiệm vụ yêu cầu tạo một web app đơn giản bằng Lambda mà không cần viết code
- __Bước 1__: Trong widget __Explore AWS__, chọn nhiệm vụ __Create a web app using AWS Lambda__

![Lambda-1.png](https://images.viblo.asia/b12038e7-4757-4138-940d-bcc7f1a7f20e.png)

- __Bước 2__: Trên trang __Create function__, chọn __Use a blueprint__
  - Trong danh sách __Blueprint name__, tìm và chọn __Getting started with Lambda HTTP__

![Lambda-2.png](https://images.viblo.asia/430d878e-c009-4d7e-bec9-9a1591d5a48f.png)

![Lambda-3.png](https://images.viblo.asia/7e5f1f6b-7ca9-4da1-9e67-b7ffe11f6d68.png)

- __Bước 3__: Đặt tên cho function, kéo xuống cuối trang, tick vào __Acknowledge__ rồi nhần __Create function__

![Lambda-4.png](https://images.viblo.asia/43edbfc2-c1d8-4368-81b6-71026ad1a6dc.png)

![Lambda-6.png](https://images.viblo.asia/a838dddf-48ad-407a-818b-ba7c5afb40c0.png)

- __Bước 4__: Sau khi function được tạo, trang chi tiết sẽ hiện ra
  - Tìm mục __Function URL__ và nhấp vào đường link đó
- Bước 5: Response trả về:

![Lambda-9.png](https://images.viblo.asia/6e36014c-270f-44a8-a4a1-22cc5744ee44.png)

&rarr; Hoàn thành nhiệm vụ

### 2.5. AWS RDS - Relational Database System

- Nhiệm vụ yêu cầu ta tạo một cơ sở dữ liệu quan hệ trên RDS bằng phương pháp đơn giản nhất
- __Bước 1__: Trong widget **Explore AWS** , chọn nhiệm vụ **"Create an Amazon RDS Database"** để bắt đầu.

![RDS-1.png](https://images.viblo.asia/f53e0454-88ea-46b5-a4f5-509b7be247cb.png)

- __Bước 2__: Trên trang __Create database__, chọn phương thức __Easy create__, và trong `Engine Type`, chọn __Aurora (PostgreSQL Compatible) hoặc PostgreSQL__

![RDS-2.png](https://images.viblo.asia/ccf4788d-9764-4c9c-afd0-7ed0b5bc2e74.png)

![RDS-3.png](https://images.viblo.asia/dbc0290b-36e4-4a8f-b95f-38b87624a89b.png)

- __Bước 3__: Giữ nguyên các thiết lập mặc định khác, cuộn xuống cuối trang và nhấn __Create database__

![RDS-5.png](https://images.viblo.asia/51c55acc-878b-41e3-bcaf-3c29a9d8d47c.png)

- __Bước 4__: Chờ vài phút cho database được tạo xong chuyển trạng thái __Available__

![RDS-6.png](https://images.viblo.asia/51094ff6-d89e-423e-9779-23421fd83157.png)

- __Bước 5__: Xoá và dọn dẹp Database:
  - Chọn database vừa tạo
  - Vào menu __Actions__ và chọn __Delete__
