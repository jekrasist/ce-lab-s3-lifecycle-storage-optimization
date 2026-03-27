# Security Testing Plan: SecureCloud Vault

## Phase 1: Static Analysis & Infrastructure as Code (Week 1)
- [ ] **Checkov/tfsec Scan:** Run against Terraform/CloudFormation to catch misconfigured S3 buckets or open Security Groups.
- [ ] **IAM Access Analyzer:** Verify that no IAM roles have overly broad permissions (e.g., asterisk actions).
- [ ] **TruffleHog:** Scan the repository for accidentally committed AWS keys or secrets.

## Phase 2: Infrastructure Hardening Verification (Week 2)
- [ ] **Prowler Scan:** Run a full AWS account audit against the CIS Benchmark.
- [ ] **S3 Public Access Check:** Verify "Block Public Access" is active at the account and bucket level.
- [ ] **WAF Rule Testing:** Attempt common SQLi/XSS payloads against the CloudFront URL to ensure WAF blocks them.

## Phase 3: Application Security Testing (Week 3)
- [ ] **OWASP ZAP:** Run a baseline scan on the React frontend and API endpoints.
- [ ] **Authentication Flow Test:** Verify that MFA is enforced and that expired JWT tokens are rejected.
- [ ] **Pre-signed URL Validation:** Ensure shared links expire at the correct time and don't allow broad bucket access.

## Phase 4: Remediation & Final Audit (Week 4)
- [ ] **Risk Register:** Document any "Low" findings that won't be fixed before launch.
- [ ] **Re-test:** Verify all "High" and "Critical" findings from previous phases are closed.

## Deliverables
- Prowler HTML Compliance Report
- OWASP ZAP Vulnerability Report
- Final Security Sign-off Document
