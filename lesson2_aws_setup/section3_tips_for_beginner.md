# ALERT FOR BEGINNERS

## 1. Danh sách các service cần tránh vì giá đắt

- Có một số services có thể khiến hết sạch credit trong vài giờ
- __Compute & Storage__:
  - __EC2 instances lớn__: t3.large, m5.xlarge, c5.4xlarge trở lên
  - __GPU instances__: p3, g4 series (3 - 20$/h)
  - __EC2 Dedicated Hosts__
  - __EBS volumes lớn__: gp3 > 1TB, io1/io2 với IOPS cao
- __Database__:
  - __RDS Multi-AZ__: Gấp đôi chi phí so với single-AZ
  - __Aurora Serverless v2__
  - __DynamoDB On-Demand__: tốn 10x so với Provisioned
- __Networking__:
  - __NAT Gateway__: 0.045$/h
  - __VPC Endpoints__: 0.01$/h/endpoint
  - __Direct Connect__: Chi phí port cao
- __AI/ML__:
  - __SageMaker Training jobs__
  - __Bedrock với model lớn: Claude 4 series__
  - __Rekognition__: với volume lớn hình ảnh/video

## 2. Danh sách các service an toàn, phù hợp với Free Tier:

- __Always Free__:
  - __Lambda: 1M reqs/month__
  - __DynamoDB: 25GB storage + 25 RCU/WCU__
  - __S3__: 5GB standard storage
  - __CloudWatch__: 10 custom metrics + 1M API reqs
  - __SNS: 1M Publishes__
  - __SQS__: 1M requests
- __Study credits:__
  - __EC2 t2.micro/t3.micro__: 8.47$/month
  - __RDS t3.micro__: Single-AZ, 15$/month
  - __ElastiCache t3.micro__: Redis/Memcached nhỏ
  - __API Gateway__: 1M calls đầu tiên với 1$

## 3. Tiết kiệm credits:

- Luôn terminate EC2 instances sau khi thực hành
- Sử dụng Spot Instances khi có thể
- Sử dụng region rẻ như us-east-1
- Xoá resources không sử dụng EBS volumes, Elastic IPs, Load Balancers
- Set up billing alert ở ngưỡng 50 - 100$
