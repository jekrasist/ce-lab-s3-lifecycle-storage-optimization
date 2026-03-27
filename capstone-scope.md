# Capstone Project: SecureCloud Vault

## Overview
A secure, serverless file storage and sharing platform that allows users to upload sensitive documents, manage permissions, and track access logs.

## Architecture
- **Frontend:** React.js hosted on S3 with CloudFront Distribution
- **Backend:** Node.js running on AWS Lambda
- **Database:** Amazon DynamoDB for metadata storage
- **Other:** Amazon S3 (File storage), AWS Cognito (Auth), AWS KMS (Encryption), AWS WAF

## User Stories
1. As a user, I can securely sign up and log in using MFA.
2. As a user, I can upload files that are encrypted automatically at rest.
3. As an admin, I can view audit logs of who accessed which files.
4. As a user, I can generate a pre-signed URL to share a file temporarily.

## Security Requirements
- **Authentication:** Amazon Cognito with Mandatory MFA.
- **Data Protection:** AES-256 encryption at rest (KMS) and TLS 1.2+ in transit.
- **Edge Security:** AWS WAF protecting the CloudFront distribution.
- **Access Control:** Least-privilege IAM roles for every compute resource.
- **Visibility:** CloudTrail and VPC Flow Logs enabled.
