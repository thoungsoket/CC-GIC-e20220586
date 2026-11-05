
# Cloud Lab 1 Submission — Amazon EC2

- **Student name:** THOUNG SOKET
- **Student ID:** e20220586
- **Learner Lab user name:** voclabs/user5623376=THOUNG_SOKET
- **Region:** US East (N. Virginia) — us-east-1
- **Date completed:** In progress

---

## Part 1.1 — An Amazon EC2 Walkthrough

### Security group

I created a security group named `aws-bootstrap-security-group`.

I configured two inbound rules:
- SSH (Port 22) for remote access.
- HTTP (Port 80) for accessing the website.

![Security group inbound rules](images/01-security-group.png)

### Key pair

I created an RSA key pair named `aws-bootstrap-key-pair` and downloaded the private key as a `.pem` file.

I used this key to connect to my EC2 instance.

![Key pair](images/02-key-pair.png)

### Instance details

I launched an EC2 instance with these settings:

- Instance name: `aws-bootstrap-instance`
- Operating system: Amazon Linux 2023
- Instance type: `t2.micro`
- Storage: 8 GiB
- Security group: `aws-bootstrap-security-group`
- Key pair: `aws-bootstrap-key-pair`

I used a user data script to install and start the Apache web server automatically.

![Instance details](images/03-instance-details.png)

### Browser test

I opened the public IP address of my instance in a browser using HTTP.

The web page displayed:

`Hello World from Educative(ip-172-31-81-100.ec2.internal)`

This confirmed that the Apache web server was working.

![Browser test](images/04-browser-test.png)

### SSH connection

I connected using my own SSH client through Windows PowerShell, not EC2 Instance Connect.

I used the private key `aws-bootstrap-key-pair.pem` to connect to my instance.

After connecting, I ran:

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

![SSH connection](images/05-ssh-connection.png)

---

## Part 1.2 — EC2 Web Solution (Challenge)

Not completed yet.

### Launch configuration

Screenshot pending: `06-challenge-launch.png`

### Security group

Screenshot pending: `07-challenge-security-group.png`

### Running instance

Screenshot pending: `08-challenge-instance.png`

### Commands on the instance

Screenshot pending: `09-challenge-terminal.png`

The commands used to install the web server and create `index.html` will be added after completing the challenge.

### Browser test

Screenshot pending: `10-challenge-browser.png`

---

## Questions

### 1. Your security group has an SSH rule and an HTTP rule. What does each one let you do? What would stop working if you deleted the HTTP rule?

The SSH rule (Port 22) allows me to connect to the EC2 instance remotely.

The HTTP rule (Port 80) allows users to open the web page using a browser.

If I delete the HTTP rule, the website will no longer be accessible through HTTP from the internet. However, SSH can still work if Port 22 is allowed.

### 2. In Part 1.1 you never logged in to install the web server. What installed it, and when did it run?

The user data script installed the Apache web server automatically.

The script ran when the EC2 instance was launched for the first time. It installed Apache, started the service, and created the web page.

### 3. Why does the web page open with `http://` but not with `https://`?

The web server was configured to use HTTP on Port 80.

HTTPS uses Port 443 and requires TLS configuration and a certificate. We did not configure HTTPS in this lab.

### 4. Part 1.2 asked for a 10 GiB root volume. Where in the launch settings did you set it, and how can you check the size on the running instance?

Not completed yet. I will answer this question after configuring the 10 GiB root volume in Part 1.2.

---

## Problems and How I Solved Them

In Part 1.1, I needed to configure the permissions of my private SSH key on Windows.

I moved the `.pem` file to the `.ssh` folder and used PowerShell commands to remove inherited permissions and grant access to my Windows user.

After that, I successfully connected to the EC2 instance using SSH.

---

## AI Note

I used ChatGPT to help me understand the SSH commands and configure my private key permissions.

I checked the result by running `icacls` in PowerShell and successfully connecting to my EC2 instance.

---

## Clean Up

- [ ] Part 1.1: Instance terminated, key pair and security group deleted.
- [ ] Part 1.2: Instance terminated, security group and any challenge key pair deleted.
