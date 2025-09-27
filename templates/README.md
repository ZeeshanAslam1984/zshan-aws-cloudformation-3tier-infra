# AWS CloudFormation 3-Tier Architecture for .NET App

This project defines a secure, scalable, and event-driven 3-tier architecture for deploying a .NET application on AWS using modular CloudFormation templates.

## 🧱 Architecture Overview

- **Network Layer**: VPC, public/private subnets, IGW, NAT, route tables, NACLs, security groups
- **Compute Layer**: EC2, ECS Cluster, ECS Service (Fargate), ECR
- **Database Layer**: Amazon RDS with private subnet isolation
- **Application Layer**: CloudFront, WAF, Route 53, EventBridge
- **Config & Secrets**: Parameter Store and Secrets Manager
- **Monitoring**: CloudWatch Logs, Alarms
- **Event-Driven Pipeline**: S3 → SNS → SQS → Lambda → Step Functions
- **IAM Roles**: Scoped access for ECS, Lambda, Step Functions

## 📁 Folder Structure

```plaintext
aws-cloudformation-3tier-architecture/
├── templates/
│   ├── network/
│   ├── compute/
│   ├── database/
│   ├── application/
│   ├── config-management/
│   ├── monitoring/
│   ├── event-driven/
│   ├── iam/
│   └── main.yaml
├── assets/
│   └── lambda/
├── parameters/
├── scripts/
└── docs/

## 📁 Deplyment Instruction for main-stack

aws cloudformation create-stack \
  --stack-name myapp-main-stack \
  --template-body file://templates/main.yaml \
  --parameters ParameterKey=KeyName,ParameterValue=my-key \
               ParameterKey=DBUsername,ParameterValue=admin \
               ParameterKey=DBPassword,ParameterValue=SuperSecure123 \
  --capabilities CAPABILITY_NAMED_IAM
