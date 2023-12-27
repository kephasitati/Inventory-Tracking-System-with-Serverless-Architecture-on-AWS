# Inventory Tracking System with Serverless Architecture on AWS

## Overview

This repository provides a solution for implementing a serverless architecture on AWS to track inventory levels across stores worldwide. The system allows stores to upload inventory files to an Amazon S3 bucket, triggering a series of serverless processes. The architecture includes Lambda functions, DynamoDB for data storage, Amazon Cognito for authentication, and Amazon SNS for notifications.

## Lab Objectives

1. **Upload Inventory File to S3:**
   - Upload an inventory file to an Amazon S3 bucket.

2. **Process Inventory File:**
   - Trigger a Lambda function to read the uploaded file and insert items into a DynamoDB table.

3. **Dashboard Application:**
   - Develop a serverless, web-based dashboard using Amazon Cognito for authentication.
   - Display inventory levels from the DynamoDB table.

4. **Notification System:**
   - Implement a Lambda function to receive updates from the DynamoDB table.
   - Send a message to an SNS topic when an inventory item is out of stock.
   - Receive notifications through SMS or email.

## Serverless Architecture

Traditionally, applications run on servers, requiring management and provisioning. This solution leverages AWS Lambda, eliminating the need for pre-allocated servers. The code runs on-demand, scaling automatically and incurring costs only when in use.

## Lab Steps

### Task 1: Creating a Lambda function to load data

1. Navigate to the Lambda service on the AWS Management Console.
2. Create a new Lambda function named **Load-Inventory** using the Python 3.7 runtime.
3. Configure the function to use an existing role named **Lambda-Load-Inventory-Role**.
4. Copy and paste the provided Python code (`lambda_function.py`) into the code editor.
5. Deploy the function.

### Task 2: Configuring an Amazon S3 event

1. Navigate to the S3 service on the AWS Management Console.
2. Create a unique bucket, e.g., **inventory-123**.
3. Configure the bucket to trigger the **Load-Inventory** Lambda function on object creation.

### Task 3: Testing the loading process

1. Download inventory files for testing.
2. Upload a file to the S3 bucket and verify successful data loading.

### Task 4: Configuring notifications

1. Navigate to the Simple Notification Service (SNS) on the AWS Management Console.
2. Create a topic named **NoStock** for inventory alerts.
3. Subscribe to the topic via email for notifications.

### Task 5: Creating a Lambda function to send notifications

1. Create a new Lambda function named **Check-Stock** using Python 3.7 runtime.
2. Configure the function to use an existing role named **Lambda-Check-Stock-Role**.
3. Copy and paste the provided Python code (`lambda_function.py`) into the code editor.
4. Deploy the function and add a trigger for DynamoDB on the **Inventory** table.

### Task 6: Testing the System

1. Upload a different inventory file to S3.
2. Verify the Inventory System Dashboard for updated data.
3. Receive a notification via SMS or email for any out-of-stock items.

## Conclusion

This lab demonstrates the implementation of a serverless architecture on AWS for efficient inventory tracking. The solution is scalable, cost-effective, and provides real-time notifications for inventory management.

---

