# Issue 2 Route Table Misconfiguration

## SECURITY NOTE: All sensitive AWS identities (account IDs, instance IDs, IP addresses, ARNs etc) are blurred throughout this documentation.

## Issue summary

Another scenario is where an EC2 instance has a public IP and appears healthy but cannot reach the internet because its subnet is associated with a route table missing the Internet Gateway route.

## Symptoms and Diagnosis Steps

- EC2 console shows 2/2 status checks passed.

![alt text](<img/ec2 instance health check passed-1.png>)

- Confirmed Security Group allowed SSH

![alt text](<img/security group inbound traffic-1.png>)

- Confirm if route table has correct subnet association: VPC -> Route Tables -> Select you route table the EC2 associated with -> Subnet Association

However:

- SSH into the instance doesn't work even though security groups are configured correctly and the route table has a correct subnet association.

- Select Routes tab in Route Table and found missing 0.0.0.0/0 and igw-xxxx route

![alt text](<img/missing route internet gateaway.png>)

To fix the issue we need to add a route:

`Destination: 0.0.0.0/0
Target: Internet Gateway (igw-xxxxxxx)`

![alt text](<img/edit route table and add a route-2.png>)

Save changes and retest connectivity:

![alt text](<img/ping test connection.png>)

![alt text](<img/retest connection.png>)

## Root Cause

The subnet containing the EC2 instance was associated with a route table that did NOT include the required route (0.0.0.0/0 → Internet Gateway), which meant the instance had no path to the internet.
Because of this missing route, the EC2 instance could not send return traffic, so SSH and all outbound connectivity failed even though the instance had a public IP and the security group allowed SSH.
