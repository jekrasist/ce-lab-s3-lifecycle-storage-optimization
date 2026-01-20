# Lab M8.10 - Draft Capstone Backlog & Responsibilities

**Repository:** [https://github.com/cloud-engineering-bootcamp/ce-lab-draft-capstone-backlog](https://github.com/cloud-engineering-bootcamp/ce-lab-draft-capstone-backlog)

**Activity Type:** Team Formation & Planning  
**Estimated Time:** 90 minutes

## Learning Objectives

- [ ] Define capstone project scope and security requirements
- [ ] Create threat model for capstone architecture
- [ ] Build security backlog with priorities
- [ ] Assign team roles and responsibilities
- [ ] Plan security testing approach

## Prerequisites

- [ ] Capstone project idea defined
- [ ] Team formed (or individual project planned)
- [ ] Completed Module 8 Lessons

## Task

Create a comprehensive security backlog for your capstone project, including threat model, risks, mitigations, and testing plan.

## Step-by-Step Instructions

### Step 1: Define Project Scope

Create `capstone-scope.md`:

```markdown
# Capstone Project: [Your Project Name]

## Overview
[Brief description of your application]

## Architecture
- Frontend: [e.g., React + S3 + CloudFront]
- Backend: [e.g., Node.js + ECS Fargate]
- Database: [e.g., RDS PostgreSQL]
- Other: [e.g., Redis for caching, SQS for queues]

## User Stories
1. As a user, I can register an account
2. As a user, I can log in with email/password
3. As a user, I can view my dashboard
4. ...

## Security Requirements
- Authentication with MFA
- Data encrypted at rest and in transit
- HTTPS only
- Least-privilege IAM roles
- CloudTrail and Flow Logs enabled
```

### Step 2: Create Threat Model

```markdown
# Capstone Threat Model (STRIDE)

## Assets
- User credentials (email, password)
- Customer PII (name, address, payment info)
- Application secrets (API keys, database credentials)

## Threats & Mitigations

### Spoofing
**Threat:** Attacker steals session cookie
- **Mitigation:** HttpOnly cookies, short-lived JWTs, MFA
- **Priority:** High
- **Backlog Item:** Implement secure session management

### Tampering
**Threat:** SQL injection modifies data
- **Mitigation:** Parameterized queries, WAF SQL injection rules
- **Priority:** Critical
- **Backlog Item:** Implement input validation and parameterized queries

### Repudiation
**Threat:** User denies action
- **Mitigation:** CloudTrail logs, application audit trail
- **Priority:** Medium
- **Backlog Item:** Enable CloudTrail and application logging

### Information Disclosure
**Threat:** S3 bucket exposes data
- **Mitigation:** Block Public Access, encryption, access logging
- **Priority:** Critical
- **Backlog Item:** Configure S3 security controls

### Denial of Service
**Threat:** DDoS attack
- **Mitigation:** AWS Shield, CloudFront, rate limiting
- **Priority:** Medium
- **Backlog Item:** Enable Shield and configure WAF

### Elevation of Privilege
**Threat:** ECS task role has admin access
- **Mitigation:** Least privilege IAM
- **Priority:** High
- **Backlog Item:** Create least-privilege IAM roles
```

### Step 3: Build Security Backlog

```markdown
# Security Backlog

## Epic 1: Authentication & Authorization
- [ ] Implement user registration with email verification
- [ ] Implement login with bcrypt password hashing
- [ ] Add MFA using TOTP (Google Authenticator)
- [ ] Create IAM roles with least privilege
- [ ] Implement JWT-based sessions (15min expiration)

## Epic 2: Data Protection
- [ ] Enable S3 default encryption
- [ ] Enable RDS encryption
- [ ] Configure HTTPS-only ALB listener
- [ ] Store secrets in Secrets Manager
- [ ] Implement S3 Block Public Access

## Epic 3: Network Security
- [ ] Deploy VPC with public/private subnets
- [ ] Configure security groups (least privilege)
- [ ] Deploy database in private subnet
- [ ] Enable VPC Flow Logs
- [ ] Configure Network ACLs

## Epic 4: Monitoring & Incident Response
- [ ] Enable CloudTrail in all regions
- [ ] Enable GuardDuty
- [ ] Configure CloudWatch Alarms (unauthorized API calls, root usage)
- [ ] Create incident response runbook
- [ ] Set up SNS alerts for critical findings

## Epic 5: Compliance & Auditing
- [ ] Enable Security Hub with CIS Benchmark
- [ ] Create compliance matrix
- [ ] Automate evidence collection
- [ ] Document security controls
- [ ] Prepare for demo presentation

## Epic 6: Security Testing
- [ ] Run Prowler security assessment
- [ ] Scan Docker images with Trivy
- [ ] Conduct OWASP ZAP scan
- [ ] Perform manual security review
- [ ] Document findings and remediations
```

### Step 4: Assign Responsibilities

```markdown
# Team Responsibilities

## [Team Member 1] - Infrastructure & Networking
- VPC and subnet configuration
- Security groups and NACLs
- VPC Flow Logs
- CloudTrail setup

## [Team Member 2] - Application Security
- Authentication and authorization
- Input validation
- Secrets management
- WAF configuration

## [Team Member 3] - Data Protection & Compliance
- Encryption at rest and in transit
- S3 security controls
- Compliance matrix
- Evidence collection

## [Team Member 4] - Monitoring & Testing
- GuardDuty and Security Hub
- CloudWatch Alarms
- Security testing (Prowler, Trivy, ZAP)
- Incident response documentation
```

### Step 5: Create Testing Plan

```markdown
# Security Testing Plan

## Phase 1: Static Analysis (Week 8)
- [ ] Terraform code review
- [ ] Secrets scanning (truffleHog)
- [ ] IAM policy analysis (Access Analyzer)

## Phase 2: Infrastructure Testing (Week 9 Day 1-2)
- [ ] Prowler CIS Benchmark scan
- [ ] Security Hub compliance check
- [ ] Config rules evaluation

## Phase 3: Application Testing (Week 9 Day 3-4)
- [ ] Docker image scanning (Trivy)
- [ ] OWASP ZAP web application scan
- [ ] Manual penetration testing
- [ ] Authentication and session testing

## Phase 4: Remediation (Week 9 Day 5)
- [ ] Fix critical and high findings
- [ ] Document accepted risks
- [ ] Re-test to verify fixes

## Testing Deliverables
- Prowler HTML report
- Trivy scan results
- OWASP ZAP report
- Manual testing documentation
```

## Submission

- `capstone-scope.md` with architecture
- `threat-model.md` with STRIDE analysis
- `security-backlog.md` with epics and tasks
- `team-responsibilities.md` (or solo plan)
- `testing-plan.md` with timeline

## Verification Checklist

- [ ] Project scope clearly defined
- [ ] Threat model completed (STRIDE)
- [ ] Security backlog with 20+ tasks
- [ ] Responsibilities assigned
- [ ] Testing plan with timeline

**Good luck with your capstone project! 🚀🔒**
