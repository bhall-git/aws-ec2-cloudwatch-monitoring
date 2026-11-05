# AWS CloudWatch Monitoring — Testing and Validation

## Objective

Validate that Amazon CloudWatch detects elevated CPU
utilization on an EC2 instance and sends an email
notification through Amazon SNS.

## Test Environment

- EC2 instance: aws-cloudwatch-lab
- Instance type: t3.micro
- Operating system: Amazon Linux 2023
- AWS Region: us-east-1
- Monitoring: Amazon CloudWatch
- Notifications: Amazon SNS

## Test Procedure

### 1. Connect to EC2

Connected to the instance using AWS Systems Manager
Session Manager without opening inbound SSH ports.

### 2. Generate CPU Load

Installed the stress-ng utility using dnf.

Executed the following command from a writable directory:

    stress-ng --cpu 2 --cpu-load 90 --timeout 420s --metrics-brief

This generated CPU load for approximately seven minutes.

### 3. Monitor CloudWatch

Observed the CPUUtilization metric in Amazon CloudWatch.

The configured alarm monitored average CPU utilization
over a five-minute evaluation period.

Alarm threshold:

    CPUUtilization > 50%

### 4. Verify SNS Notification

The CloudWatch alarm triggered during the CPU stress test.

Amazon SNS delivered an email notification to the
confirmed subscriber.

## Test Results

- CPU stress test completed successfully.
- CloudWatch detected elevated CPU utilization.
- CloudWatch alarm entered the ALARM state.
- SNS email notification was received successfully.
- End-to-end monitoring and alerting were validated.

## Cost Management

The EC2 instance was stopped after testing to avoid
additional compute charges.

EBS storage and other AWS resources may continue
to incur charges.

## Lessons Learned

- CloudWatch alarms provide automated infrastructure
  monitoring.
- Amazon SNS integrates with CloudWatch for notifications.
- Systems Manager enables secure administrative access
  without exposing SSH.
- Testing alarms validates the complete alerting workflow.
