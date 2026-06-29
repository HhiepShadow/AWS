# CLOUD DEPLOYMENT MODELS

- __Deployment Models__ xác định cách thức hạ tầng cloud được cung cấp và sở hữu
- Có 5 mô hình chính:
  - __Public Cloud__
  - __Private Cloud__
  - __Hybrid Cloud__
  - __Community Cloud__
  - __Multi-Cloud (Multi Public Cloud)__

## 1. Public Cloud:

- Định nghĩa: Toàn bộ hạ tầng được sở hữu và vận hành bởi nhà cung cấp cloud công cộng, công khai như AWS, Azure, GCP, Alibaba
- Tài nguyên được chia sẻ cho nhiều khách hàng (multi-tenant)
- Đặc điểm:
  - On-demand (PAYG - Pay as you go)
  - Scale lớn, global infrastructure
  - Regions + AZs trên toàn cầu
- Ưu điểm:
  - Chi phí thấp ban đầu (không cần đầu tư hardware)
  - Scale gần như tức thì, elastic
  - Innovation cao (Dịch vụ mới được cập nhật liên tục)
  - High availability & Global reach
  - Không cần quản lý data center
- Nhược điểm:
  - Bảo mật và compliance kém linh hoạt hơn (phụ thuộc vào nhà cung cấp)
  - Vendor lock-in (Sự phụ thuộc vào nhà cung cấp)
  - Rủi ro chia sẻ hạ tầng (Multi-tenant)
  - Chi phí có thể tăng cao nếu không kiểm soát
- Khi nào sử dụng:
  - Startup, doanh nghiệp vừa/nhỏ
  - Ứng dụng web/mobile, SaaS, development/test development
  - Workload không không nhạy cảm dữ liệu

## 2. Private Cloud:

- Định nghĩa: Hạ tầng cloud dành riêng cho 1 __tổ chức duy nhất__
- Có thể tự xây (On-premise) hoặc thuê từ provider (hosted private cloud)
- Công nghệ phổ biến: VMWare Cloud, OpenStack, AWS Outposts, Azure Stack, Oracle Private Cloud
- Ưu điểm:
  - Bảo mật cao, kiểm soát hoàn toàn
  - Tuân thủ quy định nghiêm ngặt (ngân hàng, y tế, chính phủ)
  - Tuỳ chỉnh sâu
  - Data sovereignty (Khuôn khổ quản lý dữ liệu được lưu trữ trong nước)
- Nhược điểm:
  - Chi phí cao (gần giống on-premise)
  - Scale chậm hơn public cloud
  - Cần đội ngũ vận hành lớn
  - Ít innovation so với public
- Khi nào sử dụng:
  - Doanh nghiệp lớn có dữ liệu nhạy cảm
  - Yêu cầu compliance cao (HIPAA, PCI-DSS, GDPR nghiêm ngặt)
  - Legacy system không dễ di chuyển

## 3. Hybrid Cloud:

- Định nghĩa: Kết hợp __Public Cloud__ + __Private Cloud__ (hoặc On-premise)
- Dữ liệu và ứng dụng có thể di chuyển linh hoạt giữa 2 môi trường
- Công nghệ sử dụng: AWS Direct Connect, VPN, AWS Outposts, VMWare Cloud on AWS, Azure Arc
- Ưu điểm:
  - Độ linh hoạt cao: Dùng private cho dữ liệu nhạy cảm, public cho workload biến động
  - Cost optimization
  - Dễ di chuyển dần dần (modernization)
  - Tận dụng được 2 thế mạnh
- Nhược điểm:
  - Quản lý phức tạp (networking, security, data consistency)
  - Chi phí kết nối cao
  - Cần kỹ năng hybrid architecture
- Khi nào sử dụng:
  - Doanh nghiệp đang chuyển đổi số (digital transformation)
  - Workload seasonal (Black Friday, Holiday)
  - Kết hợp legacy system với cloud-native

## 4. Community Cloud:

- Định nghĩa: Hạ tầng được chia sẻ giữa nhiều tổ chức có chung mục tiêu, quy định hoặc ngành nghề
- Ví dụ: Cloud cho các ngân hàng, AWS GovCloud
- Ưu điểm:
  - Chi phí thấp hơn private cloud
  - Chia sẻ best practices và compliance
  - Bảo mật và quy định chung
- Nhược điểm:
  - Ít linh hoạt
  - Phụ thuộc vào thành viên cộng đồng
  - Ít phổ biến hơn
- Khi nào sử dụng: Các tổ chức trong cùng ngành có yêu cầu tương đồng như y tế, giáo dục, chính phủ

## 5. Multi-Cloud (Cross-Cloud):

- Định nghĩa: Sử dụng nhiều dịch vụ Public Cloud khác nhau cùng lúc (AWS + Azure + GCP)
- Lý do: Tránh vendor lock-in, best-of-breed, negotiation giá, disaster recovery
- Ưu điểm: Linh hoạt, resilience cao
- Nhược điểm: Quản lý rất phức tạp (Cost, security, networking)
- Khi nào sử dụng: Doanh nghiệp lớn, chiến lược tránh phụ thuộc vào một nhà cung cấp
