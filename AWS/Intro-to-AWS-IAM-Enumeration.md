# Intro to AWS IAM Enumeration Writeup

<hr/>

Let's start with the challenge.

We have been given the following information about the entry point in the start.
<figure><img src="../src/Intro-to-AWS-IAM-Enumeration/entry.png" alt="Information about the entry point."></figure>

The subdomain in the link is the Account ID `794929857501`.
<figure><img src="../src/Intro-to-AWS-IAM-Enumeration/1.png" alt="Logging in to the AWS Console."></figure>

I configured my `aws-cli` according to the given credentials.
```sh
$ aws sts get-caller-identity | jq
```

<figure><img src="../src/Intro-to-AWS-IAM-Enumeration/2.png" alt="Checking the user in aws-cli."></figure>

Let's get more information about the user.
```sh
$ aws iam get-user | jq
```

<figure><img src="../src/Intro-to-AWS-IAM-Enumeration/3.png" alt="Enumerating about the IAM user."></figure>

We can list the attached policies of the user.
```sh
$ aws iam list-attached-user-policies --user-name dev01 | jq
```
<figure><img src="../src/Intro-to-AWS-IAM-Enumeration/4.png" alt="Attached user policies of dev01."></figure>