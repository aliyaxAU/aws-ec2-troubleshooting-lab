# Issue 1 Broken Security Group

## SECURITY NOTE: All sensitive AWS identities (account IDs, instance IDs, IP addresses, ARNs etc) are blurred throughout this documentation.

## Issue summary

One common real-world scenario that makes an EC2 instance unreachable is when its security group blocks required inbound traffic (SSH/HTTP) or is simply misconfigured (e.g., wrong IP address).

### Symptoms

- SSH connection times out when try to ssh

![alt text](<img/ssh ec2 error.png>)

- HTTP requests fail (if a web server is running)

To replicate the issue I misconfigured inbound SSH/HTTP traffic in security group of an instance (added a wrong IP address) and when I SSH to my instance, I'm getting:

```console
ssh: connect to host <EC2-PUBLIC-IP> port 22: Connection timed out

```

##  Diagnosis Steps

#### 1.The first thing to check is the instance state:

- EC2 → Instance → Status checks: 2/2 passed
![alt text](<img/ec2 instance health check passed.png>)

I can see status checked passed.

#### 2. Tested connectivity SSH

- SSH (ssh ec2-user@<public-ip>) → seeing connection timed out.
![alt text](<img/ssh ec2 error.png>)

When I see connection timeout I firstly check to the security groups:

- When I opened a security group in the EC2 console, I could see in the inbound rules the source of the IP address (blurred for security) is different to where it was supposed to be set:

![alt text](<img/wrong ip address.png>)

After modifying the inbound rule and setting the correct IP address, I try to connect again, and this time SSH to my instance is successful:

![alt text](<img/ssh success private ip.png>)

## Root cause 

The EC2 instance became unreachable because its security group was incorrectly configured, which blocked essential inbound traffic such as SSH or HTTP. Even though the instance itself was running normally. Since security groups act as stateful firewalls, any misconfiguration immediately makes the instance appear offline despite being fully operational.

