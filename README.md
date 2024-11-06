# AWS Cloud Cost Optimization - Identifying Stale Resources

## Overview

This project focuses on optimizing AWS costs by identifying and deleting EBS snapshots that are no longer associated with any active EC2 instance, reducing unnecessary storage expenses.

## Key Features

- **Lambda Automation**: Automates the process of checking for stale snapshots and deleting them to free up storage.
- **Cost Efficiency**: By identifying unused resources, this function aids in cost savings within AWS accounts.

## Lambda Function Workflow

1. **Fetch Snapshots**: Retrieves all EBS snapshots in the AWS account.
2. **Retrieve Active Instances**: Identifies all active EC2 instances, including running and stopped instances.
3. **Stale Check**: Compares each snapshot to see if it is still associated with an active instance.
4. **Deletion**: Deletes any snapshot identified as stale, freeing up storage resources.

## Requirements

1. **AWS IAM Role** with permissions for:
   - `ec2:DescribeSnapshots`
   - `ec2:DescribeInstances`
   - `ec2:DeleteSnapshot`
2. **Lambda Deployment** with a Python environment (e.g., Python 3.8 or above).

## Usage

1. **Deploy** the Lambda function with the provided `.py` script in this repository.
2. **Configure** a scheduled trigger (like a CloudWatch Event Rule) to run the Lambda function at regular intervals, e.g., daily or weekly, for continuous optimization.
