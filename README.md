# aws-ec2-troubleshooting-lab

# Overview

The project shows real AWS issues and how I debugged, fixed, and suggested how to prevent each one. The goal is to demonstrate useful cloud troubleshooting, monitoring, and operational skills.

## Skills Demonstrated

- EC2 troubleshooting

- CloudWatch metrics, logs, and alarms

- IAM roles and instance profiles

- VPC networking (route tables, subnets, gateways)

- Linux debugging (disk usage, CPU load, processes)

- Monitoring and alerting (SNS notifications)

## How to Navigate This Repository

### Issue 1 Broken Security Group:

[/issue-1-disk-full/](https://github.com/aliyaxAU/aws-ec2-troubleshooting-lab/blob/main/issues/Issue%201%20Security%20Group/issue1-security-group.md)

When a security group blocks the necessary incoming traffic (SSH/HTTP), the EC2 instance can't be reached.

__________________________

### Issue 2: Route Table Misconfiguration:

[/issue-2-route-table/](https://github.com/aliyaxAU/aws-ec2-troubleshooting-lab/blob/main/issues/Issue%202%20Route%20Table/issue2-route-table.md)

EC2 has a public IP and appears healthy but cannot reach the internet because its subnet is associated with a route table missing the Internet Gateway route.

___________________________

### Issue 3: High CPU Spike

[/issue-3-high-cpu-load/](https://github.com/aliyaxAU/aws-ec2-troubleshooting-lab/blob/main/issues/Issue%203%20High%20CPU%20Load/issue3-high-cpu-load.md)

EC2 instance experiences high CPU usage, and the steps below show how to implement monitoring and alerts to prevent future incidents.

___________________________

### Issue 4: Disk Full on EC2 instance

[/issue-4-full-disk/](https://github.com/aliyaxAU/aws-ec2-troubleshooting-lab/blob/main/issues/Issue%204%20Full%20Disk/issue4-full-disk.md)

An EC2 instance can experience a disk full issue. The goal is to detect the issue early to prevent recurrence.
