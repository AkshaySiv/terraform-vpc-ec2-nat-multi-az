# Terraform AWS VPC with EC2, NAT Gateway, and Load Balancer (Multi-AZ)

This Terraform configuration sets up a simple AWS architecture

- VPC with public and private subnets across multiple Availability Zones in `ap-south-1` (Mumbai)
- A NAT Gateway for internet access from private subnet
- An EC2 instance (t2.micro) in the private subnet with a web server (Apache)
- An Application Load Balancer (ALB) in front of the EC2 instance
- User data to display a welcome page from EC2
- Security groups to control access
- Outputs ALB DNS name to access the app

---

## ✅ Components

| Resource          | Description                                                   |
|-------------------|---------------------------------------------------------------|
| VPC               | Custom VPC with CIDR `10.0.0.0/16`                             |
| Subnets           | 2 public (`10.0.1.0/24`, `10.0.2.0/24`), 1 private (`10.0.3.0/24`) |
| NAT Gateway       | In Public Subnet A, provides internet to private EC2          |
| Internet Gateway  | Enables internet access for public subnets                    |
| EC2 Instance      | `t2.micro`, Amazon Linux 2, runs Apache web server            |
| Load Balancer     | ALB distributes HTTP traffic to the EC2 instance              |
| Security Groups   | ALB (open to internet), EC2 (only from ALB)                   |

---

## 📦 Prerequisites

- Terraform installed
- AWS CLI configured with credentials
- SSH key pair in AWS (for EC2 access)
