# Cloud Security — Complete Specification

## Overview

This document provides comprehensive coverage of cloud security vulnerabilities, misconfigurations, and attack methodologies across major cloud providers (AWS, Azure, GCP) and container orchestration platforms (Kubernetes, Docker).

**Target examples:** 6M
**Primary focus:** AWS, Azure, GCP, Kubernetes, Docker, container security

---

## Table of Contents

1. [AWS Security](#1-aws-security)
2. [Azure Security](#2-azure-security)
3. [GCP Security](#3-gcp-security)
4. [Kubernetes Security](#4-kubernetes-security)
5. [Docker Security](#5-docker-security)
6. [Container Orchestration Security](#6-container-orchestration-security)

---

## 1. AWS Security

### 1.1 IAM Security

#### Privilege Escalation
- Overly permissive policies — `*:*` analysis
- Privilege escalation via IAM — all 21 techniques (Rhino Security)
  - UpdateAssumeRolePolicy
  - CreatePolicyVersion
  - SetDefaultPolicyVersion
  - PassRole abuse
  - CreateAccessKey
  - CreateUserLoginProfile
  - AttachUserPolicy
  - AttachRolePolicy
  - PutUserPolicy
  - PutRolePolicy
  - AddUserToGroup
  - CreateLoginProfile
  - CreateAccessKey
  - PutGroupPolicy
  - AttachGroupPolicy
  - SetDefaultPolicyVersion
  - iam:PassRole
  - iam:CreateAccessKey
  - iam:CreateLoginProfile
  - iam:UpdateLoginProfile
  - iam:AttachUserPolicy
- Role chaining attacks
- Confused deputy attack
- Cross-account role abuse
- Service-linked role abuse
- IAM credential exposure in code
- Access key leakage in logs
- IAM user enumeration
- IAM role enumeration

#### IAM Misconfigurations
- Unused IAM credentials
- Over-privileged service accounts
- Missing MFA on root account
- Missing MFA on privileged users
- Password policy misconfiguration
- Access key rotation missing
- Console access without MFA
- IAM user without console access
- Service account without key rotation
- IAM role without trust policy validation

### 1.2 S3 Security

#### Bucket Misconfigurations
- Public bucket enumeration
- Bucket takeover — domain pointing to deleted bucket
- Server-side request forgery via presigned URLs
- S3 bucket policy misconfiguration
- ACL vs bucket policy conflicts
- Versioning abuse — delete markers
- S3 notification injection
- S3 static website hosting issues
- S3 access logging disabled
- S3 server-side encryption missing
- S3 object lock bypass

#### S3 Exploitation
- S3 bucket enumeration via DNS
- S3 bucket brute force
- S3 bucket name prediction
- S3 object enumeration
- S3 presigned URL abuse
- S3 multipart upload abuse
- S3 CORS misconfiguration
- S3 public access block bypass
- S3 encryption key exposure
- S3 KMS key abuse

### 1.3 EC2 Security

#### Instance Security
- IMDSv1 SSRF → credential theft
- IMDSv2 bypass techniques
- Security group misconfiguration
- EBS snapshot exposure
- User data script injection
- Instance profile abuse
- EC2 instance metadata abuse
- EC2 key pair abuse
- EC2 security group abuse
- EC2 network ACL abuse

#### EC2 Exploitation
- EC2 instance takeover
- EC2 snapshot restoration
- EC2 AMI abuse
- EC2 volume attachment
- EC2 network interface abuse
- EC2 elastic IP abuse
- EC2 placement group abuse
- EC2 dedicated host abuse
- EC2 spot instance abuse
- EC2 reserved instance abuse

### 1.4 Lambda Security

#### Function Vulnerabilities
- Environment variable credential exposure
- Event injection via Lambda triggers
- Insecure deserialization in Lambda
- Lambda privilege escalation via layers
- Cold start timing attacks
- Lambda function URL abuse
- Lambda alias abuse
- Lambda version abuse
- Lambda concurrency abuse
- Lambda memory abuse

#### Lambda Misconfigurations
- Lambda function without VPC
- Lambda function with public access
- Lambda function without encryption
- Lambda function without logging
- Lambda function without monitoring
- Lambda function without tracing
- Lambda function without authentication
- Lambda function without authorization
- Lambda function without resource policies
- Lambda function without dead-letter queue

### 1.5 Other AWS Services

#### Cognito
- Cognito misconfiguration — identity pool abuse
- Cognito user pool abuse
- Cognito identity pool abuse
- Cognito federation abuse
- Cognito MFA bypass
- Cognito password policy abuse
- Cognito user migration abuse
- Cognito device tracking abuse
- Cognito risk-based authentication bypass
- Cognito adaptive authentication bypass

#### API Gateway
- API Gateway — authorization bypass
- API Gateway — resource policy abuse
- API Gateway — stage variable abuse
- API Gateway — usage plan abuse
- API Gateway — API key abuse
- API Gateway — Lambda authorizer abuse
- API Gateway — Cognito authorizer abuse
- API Gateway — IAM authorizer abuse
- API Gateway — custom authorizer abuse
- API Gateway — request/response transformation abuse

#### ECS
- ECS task role abuse
- ECS task definition abuse
- ECS service abuse
- ECS cluster abuse
- ECS container instance abuse
- ECS task abuse
- ECS Fargate abuse
- ECS EC2 abuse
- ECS external abuse
- ECS Anywhere abuse

#### EKS
- EKS misconfiguration
- EKS cluster role abuse
- EKS node group role abuse
- EKS fargate profile abuse
- EKS add-on abuse
- EKS pod identity abuse
- EKS IRSA abuse
- EKS VPC CNI abuse
- EKS AWS Load Balancer Controller abuse
- EKS ExternalDNS abuse

#### RDS
- RDS public access + weak credentials
- RDS snapshot exposure
- RDS cluster abuse
- RDS instance abuse
- RDS parameter group abuse
- RDS option group abuse
- RDS subnet group abuse
- RDS security group abuse
- RDS VPC security group abuse
- RDS encryption key abuse

#### Secrets Manager vs Parameter Store
- Secrets Manager vs Parameter Store — security differences
- Secrets Manager rotation misconfiguration
- Parameter Store encryption missing
- Secrets Manager policy abuse
- Parameter Store policy abuse
- Secrets Manager KMS key abuse
- Parameter Store KMS key abuse
- Secrets Manager version abuse
- Parameter Store version abuse
- Secrets Manager secret abuse

#### CloudTrail
- CloudTrail gaps — which actions aren't logged
- CloudTrail log tampering
- CloudTrail S3 bucket misconfiguration
- CloudTrail KMS key abuse
- CloudTrail log group abuse
- CloudTrail trail abuse
- CloudTrail multi-region abuse
- CloudTrail data events abuse
- CloudTrail management events abuse
- CloudTrail insight abuse

---

## 2. Azure Security

### 2.1 Azure AD Security
- Azure AD token theft
- Service principal credential exposure
- Managed Identity abuse
- Azure AD privilege escalation
- Azure AD authentication bypass
- Azure AD authorization bypass
- Azure AD MFA bypass
- Azure AD conditional access bypass
- Azure AD identity protection bypass
- Azure AD PIM abuse

### 2.2 Azure Storage Security
- Azure Blob Storage misconfiguration
- Azure Storage account key exposure
- Azure Storage SAS token abuse
- Azure Storage access tier abuse
- Azure Storage replication abuse
- Azure Storage encryption key abuse
- Azure Storage network rule abuse
- Azure Storage lifecycle abuse
- Azure Storage CORS abuse
- Azure Storage immutability abuse

### 2.3 Azure Key Vault Security
- Key Vault access policy bypass
- Key Vault secret exposure
- Key Vault key abuse
- Key Vault certificate abuse
- Key Vault managed identity abuse
- Key Vault RBAC abuse
- Key Vault soft delete abuse
- Key Vault purge protection abuse
- Key Vault HSM abuse
- Key Vault network rule abuse

### 2.4 Azure Compute Security
- Azure Function misconfiguration
- Azure App Service abuse
- Azure Container Instance abuse
- Azure Container Apps abuse
- Azure Virtual Machine abuse
- Azure Virtual Machine Scale Set abuse
- Azure Dedicated Host abuse
- Azure Spot Instance abuse
- Azure Edge Zone abuse
- Azure Confidential Computing abuse

### 2.5 Azure Kubernetes Service (AKS)
- AKS misconfiguration
- AKS cluster role abuse
- AKS node pool role abuse
- AKS pod identity abuse
- AKS Azure CNI abuse
- AKS kubenet abuse
- AKS Azure Policy abuse
- AKS Azure Monitor abuse
- AKS Azure Defender abuse
- AKS private cluster abuse

### 2.6 Azure DevOps Security
- Azure DevOps pipeline injection
- Azure DevOps service connection abuse
- Azure DevOps agent pool abuse
- Azure DevOps variable group abuse
- Azure DevOps artifact feed abuse
- Azure DevOps build pipeline abuse
- Azure DevOps release pipeline abuse
- Azure DevOps environment abuse
- Azure DevOps deployment group abuse
- Azure DevOps self-hosted agent abuse

### 2.7 Azure Conditional Access
- Conditional Access policy bypass
- Conditional Access location bypass
- Conditional Access device bypass
- Conditional Access app bypass
- Conditional Access user bypass
- Conditional Access risk bypass
- Conditional Access sign-in risk bypass
- Conditional Access real-time bypass
- Conditional Access session control bypass
- Conditional Access legacy auth bypass

### 2.8 Azure PRT (Primary Refresh Token)
- PRT theft
- PRT replay attack
- PRT manipulation
- PRT bypass
- PRT device registration abuse
- PRT certificate abuse
- PRT key trust abuse
- PRT Windows Hello abuse
- PRT FIDO2 abuse
- PRT conditional access abuse

---

## 3. GCP Security

### 3.1 GCP IAM Security
- Service Account key abuse
- Service Account impersonation abuse
- Workload Identity Federation misconfiguration
- GCP IAM privilege escalation
- GCP IAM custom role abuse
- GCP IAM primitive role abuse
- GCP IAM service account abuse
- GCP IAM policy abuse
- GCP IAM binding abuse
- GCP IAM member abuse

### 3.2 GCP Storage Security
- GCS bucket misconfiguration
- GCS object ACL abuse
- GCS bucket policy abuse
- GCS HMAC key abuse
- GCS signed URL abuse
- GCS signed policy abuse
- GCS retention policy abuse
- GCS lifecycle policy abuse
- GCS encryption key abuse
- GCS requester pays abuse

### 3.3 GCP Compute Security
- Cloud Run misconfiguration
- Cloud Function environment variable exposure
- Cloud Build abuse
- Cloud Scheduler abuse
- Cloud Tasks abuse
- Cloud Pub/Sub abuse
- Cloud Firestore abuse
- Cloud Bigtable abuse
- Cloud Spanner abuse
- Cloud SQL abuse

### 3.4 GCP Kubernetes Engine (GKE)
- GKE cluster abuse
- GKE node pool abuse
- GKE pod abuse
- GKE service account abuse
- GKE workload identity abuse
- GKE binary authorization abuse
- GKE policy controller abuse
- GKE network policy abuse
- GKE private cluster abuse
- GKE autopilot abuse

### 3.5 GCP Metadata Security
- Compute Engine metadata SSRF
- Compute Engine metadata token abuse
- Compute Engine metadata SSH key abuse
- Compute Engine metadata startup script abuse
- Compute Engine metadata shutdown script abuse
- Compute Engine metadata custom metadata abuse
- Compute Engine metadata project metadata abuse
- Compute Engine metadata instance metadata abuse
- Compute Engine metadata network metadata abuse
- Compute Engine metadata disk metadata abuse

### 3.6 GCP BigQuery Security
- BigQuery data exposure
- BigQuery dataset abuse
- BigQuery table abuse
- BigQuery view abuse
- BigQuery routine abuse
- BigQuery job abuse
- BigQuery connection abuse
- BigQuery model abuse
- BigQuery row-level security abuse
- BigQuery column-level security abuse

---

## 4. Kubernetes Security

### 4.1 Pod Security
- Pod security context misconfiguration
- Privileged container escape
- `hostPID`, `hostNetwork`, `hostPath` abuse
- `allowPrivilegeEscalation` abuse
- `readOnlyRootFilesystem` bypass
- `runAsUser` abuse
- `runAsGroup` abuse
- `fsGroup` abuse
- `supplementalGroups` abuse
- `seLinuxOptions` abuse

### 4.2 RBAC Security
- RBAC misconfiguration — ClusterAdmin via ServiceAccount
- Role abuse
- ClusterRole abuse
- RoleBinding abuse
- ClusterRoleBinding abuse
- ServiceAccount abuse
- SubjectAccessReview abuse
- SelfSubjectAccessReview abuse
- TokenReview abuse
- LocalSubjectAccessReview abuse

### 4.3 etcd Security
- etcd exposure — no TLS, no auth
- etcd certificate abuse
- etcd key abuse
- etcd snapshot abuse
- etcd backup abuse
- etcd restore abuse
- etcd compaction abuse
- etcd defragmentation abuse
- etcd member abuse
- etcd watch abuse

### 4.4 kubelet Security
- kubelet API exposure
- kubelet authentication bypass
- kubelet authorization bypass
- kubelet exec abuse
- kubelet logs abuse
- kubelet port-forward abuse
- kubelet container log abuse
- kubelet stats abuse
- kubelet metrics abuse
- kubelet pprof abuse

### 4.5 Kubernetes Dashboard
- Kubernetes dashboard without auth
- Kubernetes dashboard authentication bypass
- Kubernetes dashboard authorization bypass
- Kubernetes dashboard privilege escalation
- Kubernetes dashboard secret exposure
- Kubernetes dashboard config map exposure
- Kubernetes dashboard deployment exposure
- Kubernetes dashboard service exposure
- Kubernetes dashboard ingress exposure
- Kubernetes dashboard persistent volume claim exposure

### 4.6 Helm Security
- Helm chart secret exposure
- Helm chart template injection
- Helm chart value injection
- Helm chart hook abuse
- Helm chart dependency abuse
- Helm chart plugin abuse
- Helm chart repository abuse
- Helm chart release abuse
- Helm chart history abuse
- Helm chart rollback abuse

### 4.7 Container Escape
- Container escape via cgroup v1
- Container escape via kernel vulnerabilities
- Container escape via privileged mode
- Container escape via hostPath
- Container escape via hostPID
- Container escape via hostNetwork
- Container escape via volume mounts
- Container escape via capabilities
- Container escape via apparmor
- Container escape via seccomp

### 4.8 Runtime Class Security
- Runtime class abuse
- Runtime class privilege escalation
- Runtime class resource abuse
- Runtime class node selector abuse
- Runtime class toleration abuse
- Runtime class affinity abuse
- Runtime class topology spread constraint abuse
- Runtime class pod overhead abuse
- Runtime class pod scheduling abuse
- Runtime class pod priority abuse

### 4.9 Admission Controller Security
- Admission controller bypass
- Admission controller injection
- Admission controller abuse
- Admission controller policy abuse
- Admission controller webhook abuse
- Admission controller mutating webhook abuse
- Admission controller validating webhook abuse
- Admission controller failure policy abuse
- Admission controller timeout abuse
- Admission controller reinvocation policy abuse

### 4.10 Network Policy Security
- Network policy gaps
- Network policy bypass
- Network policy abuse
- Network policy CNI plugin abuse
- Network policy egress rule abuse
- Network policy ingress rule abuse
- Network policy port abuse
- Network policy protocol abuse
- Network policy IP block abuse
- Network policy namespace selector abuse

---

## 5. Docker Security

### 5.1 Image Security
- Docker image vulnerability scanning
- Docker image base image abuse
- Docker image layer abuse
- Docker image history abuse
- Docker image config abuse
- Docker image metadata abuse
- Docker image signature abuse
- Docker image trust abuse
- Docker image notary abuse
- Docker image content trust abuse

### 5.2 Container Security
- Container privilege escalation
- Container escape techniques
- Container resource abuse
- Container namespace abuse
- Container cgroup abuse
- Container capability abuse
- Container seccomp abuse
- Container apparmor abuse
- Container SELinux abuse
- Container no-new-privileges abuse

### 5.3 Docker Daemon Security
- Docker daemon exposure without auth
- Docker daemon socket abuse
- Docker daemon API abuse
- Docker daemon remote API abuse
- Docker daemon TLS abuse
- Docker daemon certificate abuse
- Docker daemon key abuse
- Docker daemon CA abuse
- Docker daemon client certificate abuse
- Docker daemon client key abuse

### 5.4 Docker Registry Security
- Docker registry authentication bypass
- Docker registry authorization bypass
- Docker registry token abuse
- Docker registry catalog abuse
- Docker registry manifest abuse
- Docker registry blob abuse
- Docker registry tag abuse
- Docker registry repository abuse
- Docker registry organization abuse
- Docker registry user abuse

### 5.5 Docker Compose Security
- Docker Compose file injection
- Docker Compose environment variable abuse
- Docker Compose secret abuse
- Docker Compose volume abuse
- Docker Compose network abuse
- Docker Compose service abuse
- Docker Compose override abuse
- Docker Compose project abuse
- Docker Compose extension abuse
- Docker Compose template abuse

---

## 6. Container Orchestration Security

### 6.1 Docker Swarm Security
- Docker Swarm manager abuse
- Docker Swarm worker abuse
- Docker Swarm service abuse
- Docker Swarm task abuse
- Docker Swarm network abuse
- Docker Swarm secret abuse
- Docker Swarm config abuse
- Docker Swarm raft abuse
- Docker Swarm encryption key abuse
- Docker Swarm join token abuse

### 6.2 Nomad Security
- Nomad server abuse
- Nomad client abuse
- Nomad job abuse
- Nomad allocation abuse
- Nomad task abuse
- Nomad volume abuse
- Nomad CSI abuse
- Nomad ACL abuse
- Nomad TLS abuse
- Nomad gossip encryption abuse

### 6.3 Mesos Security
- Mesos master abuse
- Mesos agent abuse
- Mesos framework abuse
- Mesos task abuse
- Mesos executor abuse
- Mesos containerizer abuse
- Mesos credential abuse
- Mesos principal abuse
- Mesos role abuse
- Mesos quota abuse

### 6.4 Containerd Security
- Containerd runtime abuse
- Containerd snapshot abuse
- Containerd content abuse
- Containerd namespace abuse
- Containerd image abuse
- Containerd container abuse
- Containerd task abuse
- Containerd process abuse
- Containerd lease abuse
- Containerd diff abuse

### 6.5 CRI-O Security
- CRI-O runtime abuse
- CRI-O image abuse
- CRI-O container abuse
- CRI-O sandbox abuse
- CRI-O checkpoint abuse
- CRI-O volume abuse
- CRI-O network abuse
- CRI-O metrics abuse
- CRI-O profiling abuse
- CRI-O tracing abuse

### 6.6 Runc Security
- Runc container abuse
- Runc process abuse
- Runc namespace abuse
- Runc cgroup abuse
- Runc capability abuse
- Runc seccomp abuse
- Runc apparmor abuse
- Runc SELinux abuse
- Runc no-new-privileges abuse
- Runc rootless abuse

---

*End of Cloud Security Specification*
