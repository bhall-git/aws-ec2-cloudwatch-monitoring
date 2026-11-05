# AWS EC2 CloudWatch Monitoring Architecture

## Overview

This project demonstrates monitoring an Amazon EC2
instance using Amazon CloudWatch and sending email
notifications through Amazon SNS.

## Infrastructure

- AWS Region: us-east-1 (N. Virginia)
- EC2 Instance: t3.micro
- Operating System: Amazon Linux 2023
- Monitoring: Amazon CloudWatch
- Notifications: Amazon SNS
- Remote Access: AWS Systems Manager Session Manager

## Architecture

1. An Amazon Linux EC2 instance runs in a VPC.
2. An IAM instance role provides the permissions
   required for Systems Manager connectivity.
3. Session Manager provides administrative access
   without opening inbound SSH ports.
4. CloudWatch collects EC2 CPU utilization metrics.
5. A CloudWatch alarm monitors CPU utilization.
6. When average CPU utilization exceeds 50% over
   a five-minute period, the alarm enters ALARM state.
7. Amazon SNS sends an email notification to a
   confirmed subscriber.

## Testing

The stress-ng utility was used to generate CPU load
on the EC2 instance.

The CloudWatch alarm successfully detected elevated
CPU utilization and triggered an SNS email notification.

## Security

- No inbound security group rules were configured.
- EC2 access was performed using Session Manager.
- An IAM instance role was attached to EC2.
- The EBS root volume was encrypted.

## Cost Management

The EC2 instance was stopped after testing to avoid
ongoing compute charges. EBS storage and other AWS
resources may still incur charges.
