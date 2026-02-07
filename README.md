# SWE 645 – Static Website Deployment on AWS

**Name:** Aakash Patil
**Course:** SWE 645
**Assignment:** Static Website Deployment on AWS (S3 and EC2)

---

## Overview

This project demonstrates the deployment of a static portfolio website using Amazon Web Services (AWS). The website is hosted using two different AWS services:

* **Amazon S3** for static website hosting
* **Amazon EC2** with Apache HTTP Server for web hosting

Both deployments were configured, tested, and verified for public accessibility.

---

## Deployment of Static Website on Amazon S3

Amazon S3 was used to host the static website using the built-in static website hosting feature.

### Steps Followed

1. Created an S3 bucket with a unique name.
2. Disabled **Block all public access** to allow public access.
3. Uploaded website files (HTML, CSS, JavaScript) to the bucket.
4. Added a bucket policy to allow public `GetObject` access.
5. Enabled **Static Website Hosting** from the bucket properties.
6. Set `index.html` as the index document.
7. Uploaded three main files: `index.html`, `error.html`, `dragon-skull.jpg`, and `survey.html`.
8. Obtained the website endpoint from the bucket settings.

### S3 Website URL

[http://hw1-aakashpatil.s3-website-us-east-1.amazonaws.com](http://hw1-aakashpatil.s3-website-us-east-1.amazonaws.com)

---

## Deployment of Static Website on Amazon EC2

Amazon EC2 was used to host the website using the Apache HTTP Server on an Amazon Linux instance.

### EC2 Instance Setup

1. Selected **EC2** from the AWS Services Menu.
2. Clicked **Launch Instance**.
3. Chose **Amazon Linux** as the operating system.
4. Created a key pair (.pem/.ppk) for secure access.
5. Launched the EC2 instance.

---

### Connecting to the EC2 Instance

After the instance was launched, it was connected using one of the following methods:

1. Using PuTTY with converted .ppk file
2. Using an existing .ppk file
3. Connecting directly through the AWS console

For this project, the **AWS console connection method** was used.

---

### Server Configuration

After connecting to the instance, the following commands were executed:

```bash
sudo su -
yum update -y
yum install -y httpd
systemctl status httpd
```

A project directory was created:

```bash
mkdir aws_assg3
cd aws_assg3
```

---

### Website Deployment

1. Created a portfolio website and uploaded it to GitHub.
2. Copied the GitHub repository ZIP download link.
3. Downloaded the ZIP file using `wget`.
4. Extracted the ZIP file.
5. Navigated to the extracted folder.
6. Moved all website files to Apache’s document root.

```bash
wget <github-zip-link>
unzip master.zip
cd <project-folder>
mv * /var/www/html/
```

---

### Apache Service Management

Checked and enabled the Apache service:

```bash
systemctl status httpd
systemctl enable httpd
systemctl start httpd
```

Inbound rules were edited to allow HTTP (port 80) traffic.

---

## EC2 Website URL

After completing the setup, the website became accessible using the EC2 public IPv4 address:

[http://13.222.185.139/](http://13.222.185.139/)

---

## Notes

* Amazon S3 was used for static website hosting.
* Amazon EC2 with Apache was used for server-based hosting.
* All required inbound rules were configured.
* Both deployments were tested successfully.
* The project meets the assignment requirements for AWS deployment.

---

## Conclusion

This assignment demonstrates the successful deployment of a static website using both Amazon S3 and Amazon EC2. It highlights basic cloud hosting, server configuration, and web deployment techniques using AWS services.
