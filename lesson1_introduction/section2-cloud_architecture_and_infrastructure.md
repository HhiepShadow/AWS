# CLOUD COMPUTING ARCHITECTURE - INFRASTRUCTURE

## 1. Cloud Computing Architecture - Kiến trúc điện toán đám mây:

- __Cloud Computing Architecture__ là tập hợp:
  - Các thành phần (components)
  - Dịch vụ (services)
  - Nguyên lý thiết kế (design principles)
  - Mô hình triển khai (Deployment models)

&rarr;Cung cấp tài nguyên CNTT thông qua Internet theo mô hình dịch vụ

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
  - Chức năng chính: Cung cấp Graphical User Interface
