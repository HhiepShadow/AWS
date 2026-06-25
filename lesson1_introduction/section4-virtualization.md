# VIRTUALIZATION - ẢO HOÁ


## 1. Virtualization là gì?

- __Virtualization (Ảo hoá)__ là công nghệ cho phép tạo ra phiên bản ảo (virtual) của một tài nguyên vật lý (physical resources) như CPU, RAM, Storage, Network, GPU, v.v.
- Giúp một máy chủ vật lý có thể chạy nhiều máy chủ ảo độc lập cùng lúc
- Lợi ích của Virtualization:
  - __Tăng utilization__: CPU/RAM từ 10-20% lên 70-80%, giúp tối đa hoá việc sử dụng tài nguyên vật lý
  - __Isolation mạnh__: Độc lập sử dụng các máy ảo, một VM crash không gây ảnh hưởng đến VM khác
  - __Snapshot & Migration__: Có thể 'đóng băng' trạng thái VM, di chuyển VM sống (live migration, vMotion) giữa các server vật lý mà không gây downtime
  - __Tiết kiệm chi phí__: Giảm số lượng server vật lý cần mua, giảm điện, làm mát, không gian data center
  - __Cấp phát nhanh chóng__: tạo VM mới trong vài phút (thay vì mua/lắp server vật lý mất hàng tuần)
  - __Disaster Recovery dễ hơn:"__
