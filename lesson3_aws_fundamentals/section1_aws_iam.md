# AWS IAM - Identity and Access Management

- __AWS IAM__ là service của AWS (miễn phí, toàn cục - không thuộc region nào), giúp kiểm soát danh tính và quyền truy cập của toàn bộ AWS
- __AWS IAM__ giúp ta trả lời 2 câu hỏi cho mọi request gửi tới AWS:
  - __Authentication (Xác thực)__: Ai đang gửi request này?
  - __Authorization (Uỷ quyền)__: Người đó có được phép thực hiện hành động này trên tài nguyên này không?
- Khi ta tạo 1 tài khoản AWS, ta có identity duy nhất gọi là __root user__ - có toàn quyền trên mọi thứ của tài khoản đó. 

&rarr;__AWS__ khuyên không nên sử dụng tài khoản __root__ cho việc hàng ngày, chỉ dùng cho một số tác vụ đặc biệt (như đổi support plan, đóng tài khoản, một số thiết lập thanh toán, v.v.)

&rarr; Nên tạo các identity khác trong IAM để phân quyền


## 1. Các thành phần chính:

### 1.1. IAM Users:

- Là 1 identity đại diện cho một người hoặc một ứng dụng
- Có credential riêng (mật khẩu, console, access key cho CLI/API)
- Mỗi user có thể được gắn policy trực tiếp hoặc theo group

### 1.2. IAM Groups:

- Là tập hợp các users có cùng nhu cầu về quyền
- Ta gắn policy vào group một lần, tất cả member tự động được áp dụng
- Group __không thể__ chứa group khác
- Group __không thể__ được assume như 1 role, mà chỉ là cách gom các user để gán quyền tiện hơn

### 1.3. IAM Roles:

- __Role__ là 1 identity có quyền, nhưng không gắn cố định với ai
- Được các thực thể đáng tin cậy __assume (đảm nhận)__ tạm thời để lấy credential tạm thời (qua __AWS STS__), thay vì dùng access key dài hạn
- Role có 2 loại policy:
  - __Trust policy__: quy định ai được assume role này (1 service như EC2/Lambda, 1 AWS account khác, v.v.)
  - __Permission policy__: quy định role đó được làm gì sau khi assume
- Role dùng cho:
  - EC2 instance profile
  - Lambda execution role
  - Cross-account access
  - Federation (SAML/OIDC)
  - IAM Roles Anywhere (workload chạy ngoài AWS như on-premise server)

### 1.4. Policies:

- Là 1 văn bản JSON định nghĩa quyền
- Câu hỏi cốt lõi: `A có quyền làm hành động B trên C không, trong điều kiện D?`
- Có nhiều loại Policy:

| Loại policy                 | Gắn vào                                | Mục đích                                                                 |
| ---------------------------- | ---------------------------------------- | --------------------------------------------------------------------------- |
| Identity-based               | User, Group, Role                        | Quyền của chính identity đó                                            |
| Resource-based               | Tài nguyên (S3 bucket, SQS queue, KMS) | Cho phép truy cập chéo account, có `Principal`                        |
| Permissions boundary         | User, Role                               | Giới hạn quyền tối đa, dù identity-based policy cho phép nhiều hơn |
| Service Control Policy (SCP) | AWS Organizations (account/OU)           | Giới hạn quyền tối đa toàn bộ account trong tố chức                |
| Session policy               | Truyền khi gọi AssumeRole              | Giới hạn quyền thêm cho session đó                                    |

- Cấu trúc 1 JSON policy:
  - Effect:  `Allow` hoặc `Deny`
  - Action: Hành động cụ thể (`[service:Operation`])
  - Resource: ARN (mã định danh duy nhất) của tài nguyên bị tác động
  - Principle: chỉ xuất hiện trong resource-based/trust policy - ai được phép
  - Condition: điều kiện thêm (IP, MFA, tag, thời gian, region, v.v.)

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowReadS3Bucket",
      "Effect": "Allow",
      "Action": ["s3:GetObject", "s3:ListBucket"],
      "Resource": [
        "arn:aws:s3:::my-bucket",
        "arn:aws:s3:::my-bucket/*"
      ],
      "Condition": {
        "IpAddress": { "aws:SourceIp": "203.0.113.0/24" }
      }
    }
  ]
}
```

## 2. Workflow của IAM

- __IAM__ hoạt động theo mô hình __"Who can do what on which resource?"__
- Quy trình:
  - Authentication (Xác thực danh tính)
  - Authorization (Kiểm tra quyền)
  - Action (Thực thi hành động)
  - Logging & Auditing (CloudTrail)
- __Bước 1: Authentication__ (Xác thực):
  - Khi ta có gắng truy cập AWS (Console, CLI, SDK):
    - Root User: Sử dụng email + password + MFA
    - IAM User:
      - Console: Username + password + MFA
      - CLI/SDK: Access Key ID + Secret Access Key
  - IAM Role: Assume Role (Tạm thời nhận quyền)
  - Federated User: SSO qua IAM Identity Center, Google, Okta, SAML, OIDC
  - Nếu xác thực thành công &rarr; AWS cấp Security Token
- __Bước 2: Authorization (Uỷ quyền)__:
  - AWS sẽ đánh giá tất cả __Policy__ áp dụng cho request theo thứ tự:
    - __Deny Policies (explicit deny)__ &rarr; Từ chối lập tức
    - __SCP (Service Control Policies)__ &rarr; Nếu dùng AWS Organizations
    - __Resource-based Policies__ (S3 Bucket Policy, KMS Key Policy, v.v.)
    - __IAM Identity-based Policies__ (gán vào User/Role/Group)
  - Allow &rarr; Cho phép thực hiện action
  - Deny hoặc không có policy nào Allow &rarr; Từ chối
- __Bước 3: Action Execution (Thực thi):__
  - Nếu được Allow, request sẽ được thực thi trên resource (EC2, S3, Lambda, v.v.)
- __Bước 4: Logging & Auditing__:
  - __CloudTrail__ ghi lại mọi API call
  - __CloudWatch + IAM Access Analyzer__ giám sát
  - __Config__ theo dõi thay đổi cấu hình IAM
