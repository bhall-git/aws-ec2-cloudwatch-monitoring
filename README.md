# AWS EC2 and CloudWatch Monitoring Lab

## Project Overview

This project demonstrates deploying and monitoring an
Amazon Linux EC2 instance using AWS CloudWatch and
Amazon SNS.

## AWS Services Used

- Amazon EC2
- Amazon CloudWatch
- Amazon SNS
- AWS IAM
- AWS Systems Manager Session Manager

## Project Results

- Launched an Amazon Linux 2023 EC2 instance.
- Connected securely using AWS Systems Manager.
- Configured a CloudWatch CPU utilization alarm.
- Generated CPU load using stress-ng.
- Successfully received an SNS email alert.

## Security

- No inbound SSH access required.
- IAM role used for EC2 permissions.
- EC2 instance stopped after testing to reduce costs.

## Documentation

Detailed architecture, screenshots, and testing procedures
will be added as the project develops.
