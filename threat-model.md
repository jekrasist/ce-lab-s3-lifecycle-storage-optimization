# Capstone Threat Model (STRIDE)

## Assets
- **User Credentials:** Cognito tokens and email addresses.
- **Uploaded Files:** Sensitive documents stored in S3.
- **Application Secrets:** KMS Keys and API endpoints.

## Threats & Mitigations

### Spoofing
**Threat:** Attacker impersonates a user via stolen session tokens.
- **Mitigation:** Mandatory MFA in Cognito and short-lived JWT tokens.
- **Priority:** High
- **Backlog Item:** Configure Cognito User Pool with MFA and token expiration.

### Tampering
**Threat:** Attacker modifies files in S3 or changes DynamoDB records.
- **Mitigation:** Enable S3 Versioning and use IAM policies with write-only/read-only separation.
- **Priority:** Critical
- **Backlog Item:** Implement S3 Bucket Versioning and KMS encryption.

### Repudiation
**Threat:** A user deletes a critical file and denies doing so.
- **Mitigation:** CloudTrail logs and S3 Object-level logging.
- **Priority:** Medium
- **Backlog Item:** Enable CloudTrail and S3 Access Logs.

### Information Disclosure
**Threat:** S3 bucket accidentally becomes public, exposing all files.
- **Mitigation:** AWS S3 Block Public Access (Account-level).
- **Priority:** Critical
- **Backlog Item:** Configure S3 Block Public Access and CloudFront OAC.

### Denial of Service
**Threat:** Attacker floods the API, causing high AWS costs or downtime.
- **Mitigation:** AWS WAF rate limiting and CloudFront geo-blocking.
- **Priority:** Medium
- **Backlog Item:** Deploy AWS WAF with Rate-Based Rules.

### Elevation of Privilege
**Threat:** A Lambda function is compromised and gains admin access to the AWS account.
- **Mitigation:** Scoped IAM execution roles (Least Privilege).
- **Priority:** High
- **Backlog Item:** Create dedicated IAM roles for each Lambda function.
