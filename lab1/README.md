# Cloud Lab 1 — Amazon EC2

**Student Name:** THOUNG SOKET  
**Student ID:** e20220586  
**Region:** US East (N. Virginia) — us-east-1

## 1. Introduction

In this lab, I learned how to create and use an Amazon EC2 instance. I created a security group, generated a key pair, and launched a Linux virtual server. I also tested a simple web page using its public IP address and connected to the server using SSH from Windows PowerShell.

## 2. Part 1.1 — Amazon EC2 Walkthrough

### Task 1 — Create a Security Group

I created a security group named `aws-bootstrap-security-group`. I configured two inbound rules:

- SSH (Port 22) for remote access.
- HTTP (Port 80) for accessing the website.

![Security Group](images/01-security-group.png)

### Task 2 — Create a Key Pair

I created an RSA key pair named `aws-bootstrap-key-pair` and downloaded the `.pem` file. I used this key to connect securely to my EC2 instance.

![Key Pair](images/02-key-pair.png)

### Task 3 — Launch an EC2 Instance

I launched an EC2 instance with the following configuration:

- Instance name: `aws-bootstrap-instance`
- Operating system: Amazon Linux 2023
- Instance type: `t2.micro`
- Storage: 8 GiB
- Security group: `aws-bootstrap-security-group`
- Key pair: `aws-bootstrap-key-pair`

I used a user data script to install and start the Apache web server automatically.

![EC2 Instance](images/03-instance-details.png)

### Task 4 — Test the Web Server

I opened the public IP address of my EC2 instance in a browser using HTTP.

The web page displayed the message:

`Hello World from Educative(ip-172-31-81-100.ec2.internal)`

This confirmed that the Apache web server was working.

![Browser Test](images/04-browser-test.png)

### Task 5 — Connect to EC2 Using SSH

I used Windows PowerShell to connect to my EC2 instance with the private key.

I ran the following commands to check my connection:

```bash
whoami
hostname
```

The results were:

```text
ec2-user
ip-172-31-81-100.ec2.internal
```

This confirmed that I successfully connected to my Linux server.

![SSH Connection](images/05-ssh-connection.png)

## 3. Part 1.2 — EC2 Web Solution Challenge

Not completed yet.

## 4. Conclusion

In Part 1.1, I learned how to launch an Amazon EC2 instance, configure security rules, use an SSH key pair, and host a simple website. I also practiced connecting to a Linux server using PowerShell. These steps helped me understand the basic use of Amazon EC2.

