# Identify The AWS Account ID from a Public S3 Bucket Writeup
This challenge gives us a scenario where a global logistics company has tasked our cybersecurity firm with identifying their AWS account ID through a public S3 bucket, starting with the IP address of their website. The goal is to demonstrate how even minor oversights can be exploited, emphasizing the significance of robust security practices. By leveraging detailed error messages from AWS services, we aim to compile a list of possible IAM users and roles, ultimately finding the AWS account ID. This exercise requires basic Linux command line knowledge and offers valuable insights into techniques for discovering AWS account IDs and understanding tool functionalities through code review.

<hr/>

Let's start with the challenge.

We have been given the following information about the entrypoint in the start.
<figure><img src="../src/Identify-the-AWS-Account-ID-from-a-Public-S3-Bucket/entrypoint.png" alt="Information about the entrypoint."></figure>

## Enumeration
Let's start by scanning the IP Address with Nmap.

```
┌──(kali㉿kali)-[~/Desktop/pwnedlabs]
└─$ nmap -sC -sV -vv 54.204.171.32
PORT   STATE SERVICE REASON  VERSION
80/tcp open  http    syn-ack Apache httpd 2.4.52 ((Ubuntu))
| http-methods: 
|_  Supported Methods: POST OPTIONS HEAD GET
|_http-title: Mega Big Tech
|_http-server-header: Apache/2.4.52 (Ubuntu)
```

This reveals the website for Mega Big Tech. 
<figure><img src="../src/Identify-the-AWS-Account-ID-from-a-Public-S3-Bucket/1.png" alt="Home page of mega big tech."></figure>

On inspecting the source code, It reveals that the images are being hosted on a s3 bucket named `mega-big-tech`.
<figure><img src="../src/Identify-the-AWS-Account-ID-from-a-Public-S3-Bucket/2.png" alt="Source code of the website."></figure>