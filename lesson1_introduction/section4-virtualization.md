# VIRTUALIZATION - ẢO HOÁ

## 1. Virtualization là gì?

- __Virtualization (Ảo hoá)__ là công nghệ cho phép tạo ra phiên bản ảo (virtual) của một tài nguyên vật lý (physical resources) như CPU, RAM, Storage, Network, GPU, v.v.
- Giúp một máy chủ vật lý có thể chạy nhiều máy chủ ảo độc lập cùng lúc
- Lợi ích của Virtualization:
  - __Tăng utilization__: CPU/RAM từ 10-20% lên 70-80%, giúp tối đa hoá việc sử dụng tài nguyên vật lý
  - __Isolation mạnh__: Độc lập sử dụng các máy ảo, một VM crash không gây ảnh hưởng đến VM khác
  - __Snapshot & Migration__: Có thể 'đóng băng' trạng thái VM, di chuyển VM sống (live migration, vMotion) giữa các server vật lý mà không gây downtime
  - __Tiết kiệm chi phí__: Giảm số lượng server vật lý cần mua, giảm điện, làm mát, không gian data center
  - __Cấp phát nhanh chóng và linh hoạt__: tạo VM mới trong vài phút (thay vì mua/lắp server vật lý mất hàng tuần)
  - __Disaster Recovery dễ dàng hơn__: Backup/Restore cả VM như 1 file config
  - __Testing & Development an toàn__

## 2. Các loại Virtualization:

- __Virtualization__ không chỉ giới hạn ở server
- Có 6 loại chính của __Virtualization__:

### 2.1. Server/Compute Virtualization:

- Giống với định nghĩa, __Server/Compute Virtualization__ sử dụng 1 máy chủ vật lý và phần mềm ảo hoá để tách nhỏ thành nhiều VMs
- Sử dụng công nghệ __Hypervisor__ với 3 loại:
  - __Hypervisor (VMM - Virtual Machine Monitor)__: Lớp phần mềm trung gian giữa hardware và VMs
  - __Type 1 (Bare-metal)__: Chạy trực tiếp trên hardware (không thông qua host OS) với hiệu suất cao, an toàn
  - __Type 2 (Hosted)__: Chạy trên host OS, dễ sử dụng trong development/testing
- Có 3 kỹ thuật:
  - __Full Virtualization__:
    - Mô phỏng toàn bộ phần cứng
    - Sử dụng Hypervisor đóng vai trò trung gian
    - Guest OS (HĐH ảo) không biết nó đang chạy trên môi trường ảo và mọi lệnh gọi phần cứng đều được Hypervisor dịch lại hoàn toàn
  - __Para-Virtualization__:
    - Cung cấp API được tối ưu hoá để Guest OS giao tiếp trực tiếp với Hypervisor thay vì phải giả lập phần cứng
    - Guest OS cần phải được sửa đổi mã nguồn để nhận biết nó đang chạy trên máy ảo
  - __Hardware-assisted__:
    - Tận dụng công nghệ tích hợp trực tiếp trên vi xử lý vật lý (Intel VT-x hoặc AMD-V) để phân tách và quản lý tài nguyên ảo
    - Phần cứng vật lý tự động nhận biết và hỗ trợ các phân vùng ảo
    - Cho phép Guest OS ảo hoá toàn phần giao tiếp với CPU thông qua các lệnh cứng phần gốc
    - Giảm thiểu việc dịch thuật phức tạp của Hypervisor
- Công cụ sử dụng:
  - __KVM__ (Kernel-based Virtual Machine): Tích hợp Linux kernel, open-source, sử dụng bởi AWS Nitro (ảo hoá) kết hợp với QEMU
  - __VMWare ESXi/vSphere__: Enterprise mạnh (vMotion, DRS - Distributed Resource Scheduler, HA)
  - __Microsoft HyperV__: Tích hợp Windows
  - __Xen__: Para-Virtualization, sử dụng trong AWS
  - __Proxmox VE__: KVM + LXC (Linux Container), dễ sử dụng với Web UI
  - __Harvester__: HCI (Hyperconverged) dựa trên Kubernetes + KVM
  - __MicroVM__: Firecracker (AWS), Cloud Hypervisor
- Cấu hình:

```
sudo apt install qemu-kvm libvirt-clients libvirt-daemon-system virt-manager

virt-install --name ubuntu0vm --vcpus=4 --ram=8192 \
	--disk path=/var/lib/libvirt/images/vm.img,size=50 \
	--os-variant=ubuntu24.04 --network bridge=virbr0 --graphics none
```

- Ưu điểm:
  - Isolation mạnh
  - multi-OS
  - live migration
- Nhược điểm:
  - Overhead cao hơn container (chi phí tài nguyên vật lý cao)

### 2.2. OS-level Virtualization (Containerization):

- Khái niệm: Ảo hoá ở mức OS, chia sẻ kernel host, tạo isolated user-space instances (containers)
- Cách hoạt động: Sử dụng:
  - Linux namespaces (PID, network, mount, v.v.)
  - cgroups (resource control)
  - seccomp/AppArmor/SELinux
- Công cụ:
  - Docker/containerd/CRI-O
  - Podman (daemonles, rootless)
  - Kata Containers
  - LXC/LXD
  - gVisor
  - Kubernetes (EKS/AKS/GKE)
- Cách sử dụng:

```
docker run -d --name nginx -p 80:80 --memory=512m nginx
# Podman rootless
podman run -d -p 8080:80 nginx
```

### 2.3. Storage Virtualization:

- Khái niệm: Pool nhiều physical storage thành logical storage pool, abstract khỏi hardware
- Cách hoạt động: Tạo nhiều virtual disks/volumes, hỗ trợ thin provisioning, snapshots, replication, tiering
- Công cụ:
  - __Ceph__ (object/block/file, kết hợp với Rook trong K8s)
  - __Longhorn__ (Kubernetes-native)
  - __Nutanix AOS, OpenStack Cinder__
  - __AWS EBS/EFS, Azure Managed Disks, GCP Persistent Disk__
  - Cách dùng: Tạo StorageClass trong K8s, provision volume động

### 2.4. Network Virtualization:

- Tách network logic khỏi hardware
- __SDN (Software Defined Networking)__:
  - __Cilium__ (eBPF-based, mạnh nhất hiện nay trong K8s)
  - Calico, Flannel, Weave
  - Open vSwitch (OVS)
- __VMWare NSX, OpenStack Neutron__
- __Cloud__: AWS VPC, Azure VNet, GCP VPC
- __NFV__ (Network Functions Virtualization): Chạy firewall, load balancer như VM/container

### 2.5. Desktop Virtualization - VDI:

- Sử dụng khi công ty cần cấp desktop chuẩn hoá cho nhiều nhân viên, quản lý tập trung, cho phép truy cập từ xa an toàn
- Các nền tảng phổ biến:
  - __Azure Virtual Desktop/ Windows 365__
  - __Citrix Virtual Apps and Desktops__
  - __VMWare Horizon__

#### 2.6. Application Virtualization:

- Chạy application mà không install vào OS, tránh xung đột phần mềm
- Giúp dễ gỡ bỏ, dễ cập nhật tập trung
- Các ứng dụng phổ biến:
  - __Docker__
  - __VMWare ThinApp, Microsoft App-V__
  - __Citrix Virtual App__

## 3. Cloud Computing Virtualization:

- __Virtualization__ là nền tảng cốt lõi của __Cloud Computing__, nếu không có Virtualization, mô hình cloud gần như không thể tồn tại trên quy mô lớn
- Kiến trúc Cloud được xây trên Virtualization:
  - __Physical Infrastructure__: hàng nghìn server vật lý trong các datacenter của provider
  - __Virtualization Layer__: Hypervisor chạy trên từng server vật lý, 'băm' tài nguyên thành các đơn vị nhỏ gộp vào 1 `resource pool` khổng lồ
  - __IaaS__: Khách hàng thuê các đơn vị ảo đó dưới dạng VM (EC2 instances, Azure VM, GCE instances), virtual storage (EBS, Azure Disk), virtual network (VPC)
  - __PaaS/SaaS__: Xây tiếp ở tầng trên, tận dụng cùng lớp virtualization bên dưới

```
┌─────────────────────────────────────────┐
│  SaaS – Software as a Service           │  Gmail, Salesforce, Office 365
├─────────────────────────────────────────┤
│  PaaS – Platform as a Service           │  Runtime, middleware, công cụ dev
├─────────────────────────────────────────┤
│  IaaS – Infrastructure as a Service     │  VM, storage ảo, network ảo
├─────────────────────────────────────────┤
│  Virtualization Layer                   |  Hypervisor, resource pooling
├─────────────────────────────────────────┤
│  Physical Infrastructure                │  Server, storage, network vật lý
└─────────────────────────────────────────┘
```

- __Multi-tenancy__ - Đặc tính sống còn của Cloud:
  - Virtualization cho phép nhiều khách hàng (tenant) khác nhau sử dụng chung 1 server vật lý mà không biết và không can thiệp được vào nhau:
    - Mỗi VM được cách ly (isolated) hoàn toàn ở mức hypervisor (CPU scheduling, memory isolation, virtual network riêng)
    - Cloud Provider có thể đóng gói nhiều VM nhỏ của nhiều tenant vào 1 server lớn
- __Elasticity & On-demand self-service__:
  - Vì tài nguyên đã được ảo hoá thành các đơn vị nhỏ tách rời khỏi phần cứng vật lý, nên Cloud Provider có thể:
    - Cấp 1 VM mới cho khách hàng chỉ trong vài giây đến vài chục giây
    - Tự động __Scale up/down__ (tăng/giảm vCPU/RAM) hoặc __Scale out/in__ (thêm/giảm số VM) &rarr; Điểm khác biệt giữa Cloud Computing và VPS
    - Tính phí theo giờ/giây sử dụng thực tế (PAYG - Pay as you go), cấp/thu linh hoạt
- Các công nghệ Virtualization trong Cloud Provider:
  * **AWS** : dùng **Nitro System** — kết hợp hypervisor dựa trên KVM (rất nhẹ) với chip chuyên dụng (Nitro Card) đảm nhận networking, storage, để hypervisor gần như không chiếm tài nguyên CPU/RAM của khách hàng — gọi là "bare-metal performance"
  * **Microsoft Azure** : dùng **Hyper-V** (chính hypervisor Type 1 của Microsoft) làm nền cho mọi Azure VM
  * **Google Cloud** : dùng hypervisor dựa trên **KVM** (open-source, tích hợp sẵn trong Linux kernel)

&rarr; Cả 3 đều sử dụng __Type 1 Hypervisor__ vì cần hiệu năng tối đa và quản lý quy mô khổng lồ

- __Virtual Network & Virtual Storage trong cloud__:

  - __Virtual network__: Khi ta tạo 1 VPC trên AWS hay Azure VNet, đây chính là network virtualization.
    &rarr;Ta có 1 không gian địa chỉ IP, subnet, route table, firewall riêng dù chạy trên hạ tầng switch/route vật lý chung với hàng ngàn khách hàng khách
  - __Virtual Storage__: AWS EBS, Azure Disk, GCP Persistent Disk là các ổ đĩa ảo (virtual disk) từ storage pool vật lý lớn, có thể gắn/tháo khỏi VM linh hoạt, snapshot, replicate dễ dàng
- __Containers & Virtualization hiện nay:__

  - Container chạy trên VM, tạo ra 2 lớp ảo hoá:
    - Lớp ngoài: VM cách lý mạnh giữa các khách hàng khác nhau
    - Lớp trong: Container (Docker, chạy trong K8s) đóng gói ứng dụng nhẹ, khởi động nhanh, do chính 1 khách hàng tự quản lý nhiều container trong VM
  - Ví dụ: Khi ta tạo 1 cluster K8s trên AWS EKS, Azure AKS hay GCP GKE, mỗi node trong cluster thực chất là 1 VM, và bên trong mỗi VM chạy nhiều container/pod
