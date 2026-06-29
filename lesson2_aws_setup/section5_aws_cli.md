# AWS COMMAND LINE INTERFACE

- __AWS CLI__ là một công cụ thống nhất để quản lý các dịch vụ AWS - cho phép ta quản lý và tương tác với các dịch vụ của AWS trực tiếp trên terminal
- Là công cụ nền tảng cho mọi automation CI/CD pipeline, là lớp giao tiếp trực tiếp với AWS API mà không cần viết code SDK

## 1. AWS CLI v2:

- __AWS CLI v1__ (`awscli`) sẽ được đưa vào maintainance mode từ 15/07/2026 và chính thức end-of-support từ 15/07/2027
- Nếu hệ thống của bạn vẫn đang dùng v1 thì ta cần lên kế hoạch migrate sang v2
- So sánh AWS CLI v1 và v2:

| Tiêu chí                 | v1                                           | v2                                                   | Nhận xét về v2                                 |
| -------------------------- | -------------------------------------------- | ---------------------------------------------------- | ------------------------------------------------- |
| Ra mắt                    | 2013                                         | 2020                                                 | Hiện đại hơn, vẫn được phát triển mạnh |
| Ngôn ngữ lập trình     | Python 2.7/3.x                               | Python 3.8+                                          | Tương thích tốt hơn                          |
| Cài đặt                 | `pip install awscli`                       | Official Installer (`.msi, .pkg, .zip`)            | Dễ cài, không phụ thuộc vào pip             |
| Tự động cập nhật      | Không có                                   | `aws --version` và `aws --update`               | Dễ maintain                                      |
| Hỗ trợ IAM Roles/SSO     | Hỗ trợ hạn chế                           | Hỗ trợ đầy đủ (IAM Identity Center,<br />SSO)  | Tốt cho enterprise                               |
| Assume Role                | Phải cấu hình thủ công                  | Hỗ trợ native, dễ dàng                           | Tiện lợi                                        |
| S3 Performance             | Chậm với big size file                     | High-performance transfer (multipart,<br />parallel) | Nhanh gấp nhiều lần                            |
| Built-in Commands          | Ít                                          | Gần như đầy đủ các commands                   | Giàu tính năng                                 |
| Output Format mặc định  | json                                         | json (có thể custom dễ dàng)                     |                                                   |
| Auto-prompt & Help         | Cơ bản                                     | Tốt hơn (suggestion, --help chi tiết)             | Dễ dàng                                         |
| Security Features          | Cơ bản                                     | Tốt hơn (credential process, SSO, MFA support)     | An toàn                                          |
| Docker/Container Support   | Hạn chế                                    | AWS CLI v2 Docker image                              | Phù hợp với DevOps                             |
| Kích thước cài đặt   | Nhẹ                                         | Nặng hơn                                           | Vẫn ở mức chấp nhận                          |
| Tích hợp CI/CD           | Tốt                                         | Rất tốt (Github OIDC, GitLab, Jenkins)             |                                                   |
| Hỗ trợ các service mới | Chậm cập nhật                             | Realtime                                             |                                                   |
| Backward Compatibility     | -                                            | Tương thích tới 99% với v1                      | Dễ migration                                     |
| Trạng thái               | Maintainance từ 7/2026,<br />EOS từ 7/2027 | Official version, liên tục update                  |                                                   |

## 2. Cài đặt:

- Có 3 cách phổ biến:
  - Sử dụng official url download:

    ```
    curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
    unzip awscliv2.zip && sudo ./aws/install
    ```
  - Sử dụng Homebrew (MacOS):

    ```
    brew install awscli
    aws --version 
    # aws-cli/2.33.29 Python/3.13.12 Darwin/24.3.0 source/x86_64
    ```
  - Pull Docker image: AWS cung cấp Docker image `amazon/aws-cli`
- IPv6: CLI v2 hỗ trợ download qua kết nối IPv6-only - quan trọng cho EC2 chạy trong VPC chỉ có IPv6

## 3. AWS CLI v2 Commands theo Domain:

### 3.1.  Configure:

```bash
aws configure			# Cấu hình cơ bản
# AWS Access Key ID: ...
# AWS Secret Access Key: ...
# Default region name: ap-southeast-1
# Default output format: json

aws configure --profile dev	# Cấu hình Multi-account (dev, prod, staging)
```

&rarr; Lưu vào 2 file:

- `~/.aws/credentials` - Chứa access key/secret key theo từng profile
- `~/.aws/config` - Chứa region, output format, role config theo từng profile

```bash
aws --version								# Kiểm tra phiên bản
aws configure list							# Xem cấu hình hiện tại
aws configure list-profiles						# Liệt kê các profile
aws configure --profile dev remove					# Xoá profile
aws help								# Help tổng quát
aws <service> help							# Help theo service
aws sts get-caller-identity						# Kiểm tra đang login bằng identity nào
aws sts assume-role --role-arn arn:... --role-session-name temp 	# Switch role/account
```

- Authentication (SSO):

```bash
aws configure sso	# Cấu hình SSO
aws sso login		# Đăng nhập SSO
```

### 3.2. IAM - STS (Kiểm tra & cấp quyền):

```bash
aws iam list-users
```
