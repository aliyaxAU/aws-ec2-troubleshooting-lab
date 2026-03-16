# aws-ec2-troubleshooting-lab
The repository simulates real-world EC2 issues in a AWS environment to demonstrate troubleshooting skills

To showcase hands-on ability to diagnose, resolve, and document common EC2 and VPC-level failures, including network misconfigurations, performance bottlenecks, and system-level faults using AWS-native tools and Linux command-line techniques.

🧱 What’s Included
- A custom-built VPC with public and private subnets
- Bastion host for secure access to private EC2 instances
- 5 intentionally broken EC2 scenarios:
- Misconfigured security group (no SSH/HTTP access)
- Missing route to Internet Gateway (no outbound connectivity)
- High CPU usage (performance degradation)
- Full disk (storage failure)
- Failed systemd service (application outage)
- Step-by-step documentation for each issue:
- Symptoms
- Diagnostic process
- Root cause analysis
- Resolution steps
- Prevention strategies
- Optional automation scripts to simulate failures
- Architecture diagram and runbooks

🎯 Skills Demonstrated
- EC2 and VPC networking
- Linux troubleshooting (SSH, CPU, disk, services)
- CloudWatch monitoring and metrics
- IAM roles and secure access patterns
- Realistic incident response thinking
- Clear technical documentation and root cause analysis


