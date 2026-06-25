# CLOUD COMPUTING ARCHITECTURE - INFRASTRUCTURE

## 1. Cloud Computing Architecture - Kiến trúc điện toán đám mây:

`<img src="../images/image.png" />`

- __Cloud Computing Architecture__ là tập hợp:
  - Các thành phần (components)
  - Dịch vụ (services)
  - Nguyên lý thiết kế (design principles)
  - Mô hình triển khai (deployment models)

&rarr; Cung cấp tài nguyên CNTT thông qua Internet theo mô hình dịch vụ

- Mục tiêu:
  - Cung cấp tài nguyên theo nhu cầu (On-demand)
  - Co giãn linh hoạt (Elasticity)
  - Tính sẵn sàng cao (High Availability)
  - Khả năng mở rộng cao (Scalability)
  - Thanh toán theo mức sử dụng (PAYG - Pay as you go)
  - Quản lý tập trung

```
┌──────────────────────┐
│      Frontend        │
│ Web, Mobile, CLI     │
└──────────┬───────────┘
           │ Internet/API
           ▼
┌──────────────────────┐
│      Cloud Layer     │
│                      │
│ Application Services │
│ Compute Services     │
│ Storage Services     │
│ Database Services    │
│ Network Services     │
│ Security Services    │
│ Monitoring Services  │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│ Physical Resources   │
│ Servers              │
│ Storage              │
│ Networking           │
│ Data Centers         │
└──────────────────────┘
```

### 1.1. Frontend Component:

- Là giao diện UI, thành phần giúp người dùng tương tác trực tiếp
  - __Client Infrastructure__: Bao gồm phần cứng và phần mềm phía người dùng như laptop, mobile, tablet, web browser, v.v.
  - Chức năng chính: Cung cấp Graphical User Interface để truy cập các dịch vụ cloud
- Vai trò: FE gửi request qua internet đến BE và nhận về response
- Ví dụ: Khách hàng truy cập cloud qua Management Console, CLI, SDK hoặc ứng dụng mobile/web kết nối qua API Gateway

### 1.2. Backend Component (Cloud Provider Side):

- Là `Cloud` thực sự, do các nhà cung cấp quản lý
- Chứa tất cả tài nguyên cốt lõi, xử lý logic, lưu trữ, bảo mật và scaling
- Các thành phần:

| Component                | Mô tả                                                                                     | AWS Mapping                                                                                          |
| ------------------------ | ------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| Application (Ứng dụng) | Phần mềm hoặc nền tảng mà client truy cập,<br />xử lý yêu cầu người dùng      | Ứng dụng web/API chạy trên EC2, ECS, EKS,<br />Lambda hoặc Elastic Beanstalk                    |
| Service (Dịch vụ)      | Quản lý các loại dịch vụ cloud cung cấp (IaaS, PaaS, SaaS, v.v.)                     | EC2 (IaaS), Lambda (FaaS), RDS (PaaS),<br />S3 (Storage as a Service)                                |
| Runtime Cloud            | Môi trường thực thi cho ứng dụng (virtual machines, containers)                       | EC2 instances, ECS Fargate, EKS, Lambda runtime                                                      |
| Storage                  | Lưu trữ linh hoạt, scalable cho dữ liệu (object, block, file)                          | S3 (Object), EBS (Block), EFS/FSx (File), Glacier (Archive)                                          |
| Infrastructure           | Phần cứng nền tảng + Virtualization (server, network),<br />được quản lý bằng IaC | AWS Global Infrastructure (Region, AZs), EC2 hosts,<br />IaC với CDK/Terraform                      |
| Management               | Control plane: cấp phát tài nguyên, giám sát, quản lý toàn bộ BE                  | AWS Systems Manager, Auto Scaling,<br />CloudWatch, AWS Organizations                                |
| Security                 | Bảo vệ tài nguyên, mạng, dữ liệu (IAM, encryption, v.v.)                             | IAM (Identity), KMS (Key), WAF (Firewall), GuardDuty,<br />Security Hub, VPC Security Groups         |
| Database                 | Quản lý dữ liệu có cấu trúc/ không cấu trúc                                       | RDS/Aurora (SQL), DynamoDB (NoSQL),<br />DocumentDB, Redshift                                        |
| Networking               | Điều hướng traffic, load balancing, DNS, connection                                     | VPC (Virtual Private Cloud), ALB/NLB (Load Balancer),<br />Route 53, Transit Gateway, Direct Connect |
| Analytics                | Xử lý dữ liệu lớn, BI, Machine Learning                                                | Glue, Athena, QuickSight, EMR, SageMaker, Kinesis                                                    |

### 1.3. Flow hoạt động:

* Người dùng tương tác qua **Frontend** (browser/app) → gửi request.
* Request đi qua **Internet** → đến **Networking** layer (Load Balancer, API Gateway).
* **Management** layer phân bổ tài nguyên từ **Runtime Cloud** +  **Infrastructure** .
* **Application** + **Service** xử lý logic, truy vấn **Database** /  **Storage** .
* **Security** layer kiểm tra mọi lúc.
* Response trả về Frontend.
* **Analytics** layer theo dõi và tối ưu liên tục.

__Event-Driven (EDA)__: Sử dụng __SQS (Simple Queue Servive), SNS (Simple Notification Service)__

### 1.4. Key Benefits:

- __Cost Efficiency__: Chuyển từ CapEx &rarr; OpEx, chỉ trả tiền cho tài nguyên sử dụng
- __Scalability__: Tự động scale ngang (Auto Scaling Groups, Lambda concurrency)
- __Reliability & Disaster Recovery__: Multi-AZ, Multi-Region, Snapshots, Aurora Global Database
- __Security__: Centralized, enterprise-grade
- __Simplified Management__: IaC, managed services, automation

### 1.5. Best Practices:

- __Design for Failure__: Luôn giả định component sẽ lỗi &rarr; Multi-AZ, Chaos Engineering (FIS)
- __Infrastructure as Code (IaC)__: Sử dụng AWS SDK hoặc Terraform cho Infrastructure layer
- __Serverless-first__ khi phù hợp (giảm quản lý runtime cloud)
- __Observability__: Triển khai 3 trụ cột (Metrics - Logs - Traces) ngay từ đầu
- __Security by Design__: Áp dụng Zero Trust + Least Privilege
- __Cost Optimization__: Tagging strategy + Compute Optimizer + Savings Plans
- __Well-Architected Review__: Đánh giá định kỳ theo 6 Pillars


## 2. Cloud Computing Infrastructure - Hạ tầng điện toán đám mây:

![](https://media.geeksforgeeks.org/wp-content/uploads/20210318220041/infra2.png)

- __Cloud Infrastructure__ là phần backend của __Cloud Computing Architecture__
- Bao gồm toàn bộ phần cứng (hardware) và phần mềm (software) cần thiết để cung cấp các dịch vụ đám mây một cách đáng tin cậy, scalable và an toàn
- Gồm:

  - __Server__
  - __Networking__
  - __Virtualization Software (Hypervisor)__
  - __Management Software__
  - __Deployment Software__
  - __Storage__
- Vai trò:

  - Cung cấp tài nguyên theo nhu cầu (On-demand)
  - Hỗ trợ Public, Private và Hybrid Cloud
  - Giúp chuyển đổi từ CapEx sang OpEx

### 2.1. __Hypervisor__ (Virtual Machine Monitor - VMM):

- Định nghĩa: Firmware/Phần mềm thấp cấp cho phép ảo hoá - tạo nhiều máy ảo (VM) trên một server vật lý
- Chức năng:
  - Phân bổ CPU/RAM/Storage cho các VM
  - Cô lập các VM (Security & Multi-tenancy)
  - Quản lý tài nguyên động
- Có 2 loại phổ biến:
  - __Bare Metal__: VMWare ESXi, Xen, Hyper-V, KVM
  - __Hosted__: VirtualBox, VMWare Workstation
- AWS Mapping: AWS sử dụng custom hypervisor (Nitro System) trên EC2 instances để đạt performance cao, security tốt hơn

### 2.2. Management Software:

- Chức năng: Giám sát, cấu hình và tối ưu hoá toàn bộ hạ tầng
- Bao gồm: Resource allocation, monitoring, automation, billing, policy enforcement
- AWS Tools:
  - AWS Systems Manager (SSM)
  - AWS Organizations + Control Tower
  - AWS Config + CloudWatch
  - AWS Auto Scaling + Compute Optimizer

### 2.3. Deployment Software:

- Chức năng: Triển khai và tích ứng dụng lên cloud, xây dựng môi trường ảo
- Hỗ trợ tự động provisioning, configuration management
- __AWS Tools__: AWS CloudFormation, AWS CDK, AWS Elastic Beanstalk, AWS OpsWorks, Terraform

### 2.4. Network:

- Chức năng: Kết nối tất cả các thành phần, truyền dữ liệu nội bộ và ngoại bộ qua internet
- Bao gồm: Routers, Switches, Load Balancers, Firewalls, DNS, VPN, Direct Connect
- __AWS Mapping__:
  - AWS VPC (Virtual Private Cloud)
  - ALB/NLB/GLB
  - Route 53
  - Transit Gateway, Direct Connect, Global Accelerator

### 2.5. Server (Computing):

- Chức năng: Xử lý tính toán, chạy ứng dụng và dịch vụ
- Bao gồm cả physical servers + virtual servers
- AWS Mapping:
  - EC2
  - Lambda
  - Outposts (Server on-premise)

### 2.6. Storage:

- Chức năng: Lưu trữ và quản lý dữ liệu với khả năng replicate, backup và high availability
- Các loại lưu trữ:
  - Block
  - File
  - Object
  - Archival
- AWS Mapping:
  - Object: AWS S3 (11 9's durability)
  - Block: AWS EBS (Elastic Block Store)
  - File: AWS EFS, FSx
  - Archival: S3 Glacier, Deep Archive
  - Lifecycle Policies, Replication, Versioning
-
