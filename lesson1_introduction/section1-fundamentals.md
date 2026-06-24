# CLOUD COMPUTING FUNDAMENTALS

## 1. Giới thiệu - Cloud Computing là gì?

- __Cloud Computing__ là một mô hình cung cấp tài nguyên CNTT (như máy chủ server, lưu trữ storage, mạng, cơ sở dữ liệu, phần mềm, v.v.) thông qua internet theo nhu cầu (__on-demand__)
- Cho phép người dùng:
  - __Tự phục vụ__ (Self-service)
  - __Thanh toán theo mức độ sử dụng__ (PAYG - Pay as you go)
  - Khả năng mở rộng linh hoạt (Elastic)
- __Cloud__ có 5 đặc tính thiết yếu theo __NIST (National Institute of Standard and Technology):__
  - __On-demand self-services__: Khách hàng tự cấp phát tài nguyên mà không cần tương tác với nhà cung cấp
  - __Broad network access__: Truy cập qua mạng internet bằng nhiều thiết bị khác nhau (tablet, laptop, mobile, v.v.)
  - __Resource pooling__: Tài nguyên được chia sẻ đa người dùng (__Multi-tenant__), đặt tại các data-center lớn
  - __Rapid elasticity__: Điều chỉnh tăng/giảm tài nguyên nhanh chóng, gần như tức thì
  - __Measured service__: Hệ thống đo lường, theo dõi và tính phí chính xác
- So sánh với mô hình truyền thống (__On-premise__):
  - On-premise: Phải mua server, tủ rack, điện dự phòng, đội ngũ vận hành &rarr; Chi phí CapEx (Capital Expenditure - Chí phí vốn) cao, lãng phí tài nguyên
  - Cloud: Chuyển OpEx (Operating Expenditure - Chi phí vận hành), chỉ trả tiền cho những gì sử dụng

## 2. Lợi ích của Cloud Computing:

- __Tiết kiệm chi phí__: Chuyển từ __CapEx__ sang __OpEx__, không lãng phí tài nguyên idle
- __Tốc độ & Agility (Sự nhanh nhạy)__: Triển khai môi trường chỉ trong vài phút thay vì vài tuần/tháng
- __Scalability & Elasticity__: Tự động scale lên/xuống dựa theo tải
- __High Availability & Reliability__: Sử dụng Multi-AZ (Availability Zones), Multi-Region
- __Global Reach__: Triển khai ứng dụng gần người dùng cuối để giảm latency
- __Innovation Speed__: Dễ dàng thử nghiệm công nghệ mới (AI/ML, Serverless, Containers)
- __Security__: Nhà cung cấp cloud thường có đội ngũ bảo mật mạnh hơn doanh nghiệp vừa và nhỏ
- __Sustainability__: AWS, Azure, GCP đang chuyển sang năng lượng tái tạo

Nhược điểm:

- Vendor lock-in (Khó chuyển đổi nhà cung cấp)
- Chi phí có thể tăng cao nền không kiểm soát (__Cost explosion__)
- Vấn đề tuân thủ pháp lý và data sovereignty (chủ quyền dữ liệu): Dữ liệu nằm ở quốc gia nào thì phải tuân thủ luật pháp của quốc gia đó, nghĩa là không phụ thuộc vào vị trí của tổ chức của dữ liệu đó, khi dữ liệu được lưu trữ trên server tại một quốc gia khác, nó sẽ chịu sự chi phối của luật pháp quốc gia đó
- Phụ thuộc vào kết nối internet

## 3. Mô hình dịch vụ Cloud (Service Models):

| **Tiêu chí**               | **IaaS**                                                                       | **PaaS**                                                                                         | **CaaS (Mới)**                                                                                                                | **FaaS**                                                                 | **SaaS**                                                            | **XaaS (Mới)**                                                                               |
| ---------------------------------- | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| **Tên tiếng Việt**        | **Dịch vụ Hạ tầng**                                                        | **Dịch vụ Nền tảng**                                                                         | **Dịch vụ Container**                                                                                                        | **Dịch vụ Hàm**                                                       | **Dịch vụ Phần mềm**                                            | **Mọi thứ dưới dạng dịch vụ**                                                          |
| **Định nghĩa**            | **Cung cấp tài nguyên tính toán cơ bản (máy chủ, mạng, lưu trữ).** | **Cung cấp môi trường nền tảng để lập trình viên phát triển và chạy ứng dụng.** | **Cung cấp môi trường để triển khai, quản lý và mở rộng các ứng dụng đóng gói dạng container.**             | **Cho phép chạy các đoạn mã nhỏ lẻ, phản hồi theo sự kiện.** | **Cung cấp các ứng dụng phần mềm hoàn chỉnh qua internet.** | **Thuật ngữ bao trùm chỉ TẤT CẢ mọi dịch vụ CNTT được cung cấp qua internet.**   |
| **Nhà cung cấp quản lý** | **Mạng, Máy chủ, Lưu trữ, Ảo hóa.**                                     | Hệ điều hành, Middleware, Runtime.                                                                 | Hệ điều hành, Container Engine, Bộ điều phối Container (Kubernetes/Docker Swarm).**                                          | Môi trường thực thi mã nguồn.                                            | Dữ liệu, Ứng dụng.                                                    | **Tùy thuộc vào mô hình "aaS" cụ thể bên trong nó.**                                 |
| **Người dùng quản lý**  | **Hệ điều hành, Middleware, Runtime, Dữ liệu, Ứng dụng.**              | **Dữ liệu, Ứng dụng.**                                                                       | **Container Images (Docker image), Ứng dụng bên trong container, Dữ liệu.**                                               | **Mã nguồn (Code) và Dữ liệu.**                                     | **Chỉ các cài đặt cá nhân nhỏ.**                            | **Tùy thuộc vào mô hình "aaS" cụ thể.**                                                |
| **Đối tượng sử dụng**  | **SysAdmin, Kiến trúc sư IT.**                                              | **Lập trình viên (Developers).**                                                              | **DevOps Engineers, Lập trình viên, SysAdmin.**                                                                             | **Lập trình viên (Developers).**                                      | **Người dùng cuối (End-users).**                                | **Tất cả (CIO, IT Manager, Dev, End-user).**                                                |
| **Mức độ kiểm soát**    | **Cao nhất.**                                                                 | **Trung bình.**                                                                                 | **Trung bình - Cao**(Kiểm soát được môi trường chạy trong container, nhưng không can thiệp được vào host OS). | **Cao (Tập trung vào logic hàm).**                                    | **Thấp nhất.**                                                    | **Đa dạng**(Từ thấp đến cao).                                                           |
| **Độ linh hoạt**          | **Rất cao.**                                                                  | **Cao.**                                                                                         | **Rất cao**(Mang ứng dụng đi khắp nơi dễ dàng nhờ container).                                                         | **Rất cao.**                                                            | **Thấp.**                                                          | **Tối đa** **.**                                                                      |
| **Chi phí**                 | **Trả theo CPU, RAM, GB lưu trữ.**                                          | **Trả theo tài nguyên và dịch vụ nền tảng.**                                             | **Trả theo số lượng node (cluster), CPU/RAM tiêu thụ, hoặc phí quản lý cluster.**                                    | **Trả theo số lần thực thi và thời gian chạy.**                   | **Trả theo gói đăng ký hoặc số lượng user.**               | **Đa dạng**(Đăng ký, trả theo mức dùng, v.v.).                                        |
| **Ví dụ điển hình**     | **AWS EC2, Azure VMs, Google Compute Engine.**                                 | **Heroku, Google App Engine, AWS Elastic Beanstalk.**                                            | **AWS ECS/EKS, Google Kubernetes Engine (GKE), Azure Kubernetes Service (AKS).**                                               | **AWS Lambda, Azure Functions, Google Cloud Functions.**                 | **Gmail, Salesforce, Microsoft 365, Zoom.**                         | **DBaaS**(Database),**STaaS**(Storage),**BCaaS**(Backup), và cả IaaS/PaaS/SaaS. |

## 4. Mô hình triển khai Cloud (Deployment Models):

| Tiêu chí                                  | Public Cloud                                                                       | Private Cloud                                                     | Hybrid Cloud                                                               | Community Cloud                                                        | Multi-Cloud                                                        |
| ------------------------------------------- | ---------------------------------------------------------------------------------- | ----------------------------------------------------------------- | -------------------------------------------------------------------------- | ---------------------------------------------------------------------- | ------------------------------------------------------------------ |
| __Định nghĩa__                     | __Toàn bộ hạ tầng thuộc nhà cung cấp cloud công cộng__              | __Hạ tầng cloud dành riêng cho một tổ chức__         | __Kết hợp giữa Public + Private Cloud/On-premise__                | __Chia sẻ hạ tầng giữa nhiều tổ chức có chung nhu cầu__ | Sử dụng nhiều nhà cung cấp public cloud khác nhau            |
| **Quyền sở hữu**                   | **Nhà cung cấp dịch vụ (AWS, Azure...).**                                | **Tổ chức/Doanh nghiệp tự sở hữu.**                   | **Kết hợp giữa Nhà cung cấp & Doanh nghiệp.**                  | **Một tổ chức đại diện hoặc nhóm các tổ chức.**       | **Các nhà cung cấp dịch vụ khác nhau.**                |
| **Đối tượng sử dụng**           | **Bất kỳ cá nhân, DN nào đăng ký.**                                  | **Chỉ nội bộ 1 tổ chức duy nhất.**                    | **Nội bộ tổ chức + Khách hàng đối tác.**                    | **Nhóm tổ chức có chung mục đích/tuân thủ.**            | **Nội bộ tổ chức (sử dụng nhiều vendor).**            |
| **Vị trí hạ tầng**                | **Tại Data Center của nhà cung cấp.**                                    | **Tại chỗ (On-premise) hoặc thuê ngoài.**              | **Kết hợp cả Tại chỗ và Nhà cung cấp.**                      | **Tại chỗ hoặc thuê ngoài (riêng biệt).**                 | **Tại các Data Center của nhiều nhà cung cấp.**        |
| **Mức độ bảo mật & Kiểm soát** | **Thấp hơn (phải tin tưởng nhà cung cấp).**                           | **Cao nhất**(Toàn quyền kiểm soát).                    | **Cao (Tách biệt dữ liệu nhạy cảm và dữ liệu thường).**   | **Cao (Tuân thủ các chuẩn ngành chung).**                   | **Trung bình - Cao (Phụ thuộc vào từng vendor).**       |
| **Chi phí**                          | **Thấp nhất**(Không tốn vốn đầu tư ban đầu, trả theo mức dùng). | **Cao nhất**(Tốn kém phần cứng, nhân sự vận hành). | **Trung bình (Tối ưu hóa chi phí giữa 2 môi trường).**      | **Trung bình (Chi phí được chia sẻ cho nhóm).**           | **Cao (Phức tạp trong quản lý chi phí nhiều vendor).** |
| **Khả năng mở rộng**              | **Gần như vô hạn**tức thì.                                             | **Hạn chế (bị giới hạn bởi phần cứng tự mua).**    | **Rất cao (Mượn sức mạnh từ Public khi cần).**                | **Hạn chế (Bị giới hạn bởi hạ tầng cộng đồng).**      | **Rất cao (Mượn sức mạnh từ nhiều Public).**          |
| **Độ phức tạp khi quản lý**     | **Rất thấp (Nhà cung cấp lo hết).**                                     | **Rất cao (Doanh nghiệp tự lo 100%).**                   | **Cao (Cần kiến trúc sư giỏi để kết nối 2 môi trường).** | **Trung bình.**                                                 | **Rất cao**(Cần công cụ quản lý đa nền tảng).       |
| **Ví dụ điển hình**              | **AWS EC2, Microsoft 365, Google Drive.**                                    | **VMware vSphere, OpenStack nội bộ, IBM Cloud Private.**  | **Kết nối AWS với Data Center tại chỗ qua VPN/Direct Connect.** | **Đám mây dùng chung cho ngành Y tế, Chính phủ.**        | **Dùng AWS (Compute) + GCP (AI) + Snowflake (Data).**       |

## 5. Shared Responsibility Model (Mô hình Trách nhiệm chung):

- __Shared Responsibility Model__ là một trong những khái niệm quan trọng nhất khi làm việc với AWS
- Đây là nền tảng để hiểu rõ ai chịu trách nhiệm về phần nào trong môi trường cloud
- Là mô hình phân chia trách nhiệm giữa __AWS__ và __Khách hàng (Người dùng)__ về bảo mật và tuân thủ khi sử dụng AWS
  - __AWS__ chịu trách nhiệm bảo mật __phần hạ tầng bên dưới__ (__Security of the Cloud__)
  - Khách hàng chịu trách nhiệm bảo mật những gì họ triển khai trên cloud (__Security in the Cloud__)

```
                  Khách hàng chịu trách nhiệm
    ┌──────────────────────────────────────────────────────┐
    │  Dữ liệu          Ứng dụng          OS / Runtime     │
    │  Access Control   IAM Policies      Encryption       │
    │  Network Config   Patch Management  Backup           │
    └──────────────────────────────────────────────────────┘

		  AWS chịu trách nhiệm   
    ┌──────────────────────────────────────────────────────┐
    │  Physical Security   Hypervisor   Host OS            │
    │  Data Center         Power        Cooling            │
    │  Global Network      Facilities   Hardware           │
    └──────────────────────────────────────────────────────┘
```

- Trách nhiệm của AWS: __AWS__ chịu trách nhiệm bảo vệ toàn bộ hạ tầng vật lý và nền tảng cốt lõi:
  - __Physical security của data center__ (Camera giám sát, bảo vệ, sinh trắc học)
  - __Hardware infrastructure__ (Server, disk, network devices)
  - __Hypervisor__ (Ảo hoá)
  - __Global networking infrastructure__ (fiber, routers, edge locations)
  - __Power, cooling, fire suppresion__ trong dât center
  - __Region & Availability Zone isolation__
  - __Compliance certifications của hạ tầng: ISO 27001, SOC 1/2/3, PCI-DSS, GDPR, HIPAA, v.v. (AWS cung cấp qua AWS Artifact)__
- Trách nhiệm của Khách hàng: Ta cần chịu trách nhiệm cho mọi thứ ta cấu hình và triển khai:
  - __Dữ liệu (Data)__: Encryption, classification, backup
  - __Identity & Access__: IAM users, roles, policies, MFA, least privilege
  - __Network configuration__: Security Groups, NACLs, Route Tables, VPC settings
  - __Operating System (Trên EC2)__: Patch OS, firewall, antivirus
  - __Application Security__: Code, dependencies, OWASP top 10
  - __Encryption__: KMS keys, TLS/SSL, data at rest & in transit
  - __Backup & Disaster Recovery__
  - __Logging & Monitoring__: CloudTrail, CloudWatch, Config
  - __Compliance__ cho workload của ứng dụng
- Mô hình sẽ thay đổi theo loại dịch vụ:
  - Mức độ trách nhiệm của bạn giảm dần khi dịch vụ càng cao cấp:

| Dịch vụ  | Trách nhiệm của AWS         | Trách nhiệm của khách hàng            | Mức độ khách hàng quản lý |
| ---------- | ------------------------------ | ------------------------------------------ | -------------------------------- |
| EC2        | Hypervisor, Host hardware      | OS, Patch, IAM, Security Group             | Cao nhất                        |
| RDS/Aurora | OS, Database engine, Backup    | Data, Encryption, IAM, Network, Parameters | Trung bình                      |
| Lambda     | Toàn bộ runtime, scaling, OS | Code, Dependencies, IAM Role, Data         | Thấp                            |
| S3         | Infrastructure                 | Bucket policy, Encryption, Public Access   | Thấp                            |
| DynamoDB   | Toàn bộ hạ tầng            | Table design, IAM, Encryption, Access      | Rất thấp                       |

__Ví dụ__:

- __S3 Bucket__:
  - AWS: Đảm bảo dữ liệu được replicate 11 9's (99.999999999%) durability, bảo mật data center
  - Khách hàng: Phải cấu hình __Bucket Policy__, bật __Versioning__, __Server-Side Encryption__, __Block Public Access__
    - Nếu bucket public &rarr; Ta phải chịu trách nhiệm hoàn toàn

__Best Practices khi áp dụng Shared Responsibility Model__:

- __Least Privilege__ &rarr;Chỉ cấp quyền cần thiết
- __Enable MFA__ cho tất cả user và root account
- __Bật AWS Config + Security Hub + GuardDuty__ để giảm sát
- __Sử dụng AWS Organizations + SCP__ để enforce policy ở mức tổ chức
- __Automation__: IaC + Security as Code
- __Regular Well-Architected Review__ (Security Pillar)
- __Encryption everywhere__ (KMS + TLS 1.2+)
- __Backup + DR Strategy__ (RTO/RPO)
- __Training & Awareness__
