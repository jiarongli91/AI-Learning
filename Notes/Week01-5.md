# Day 5: Cloud Platform AI Service Practice & Project Architecture Design
Learning Date: March 21, 2026
Learning Time: 19:00–21:00 (Evening)
Learning Objective: Gain hands‑on proficiency with AWS AI services, design an intelligent customer service system architecture, and master cost monitoring and security best practices

## 🎯 Overview
This session uses AWS as the core cloud platform to explore AI service API usage, free tier utilization, cost monitoring, and security architecture design. Based on knowledge from the week, you will design your first runnable AI application: an Intelligent Customer Service System.

### Key Learning Focus
- AWS AI service overview: main service categories and free tier policies
- API practice: Python SDK usage for Bedrock, Comprehend, and other services
- Cost optimization: cost monitoring tools and budget alert setup
- Security design: end‑to‑end secure architecture with encryption and access control
- Project architecture: complete technical design for an intelligent customer service system

## 1. AWS AI Service Overview
### 1.1 Main AI Service Categories
| Service Category | Representative Service | Core Function | Free Tier Policy |
|------------------|------------------------|---------------|------------------|
| Foundation Models | Amazon Bedrock | Access 100+ foundation models for generative AI | Access via credits for free and paid features |
| Natural Language Processing | Amazon Comprehend | Sentiment analysis, entity recognition, keyword extraction | 12‑month free trial, 50K text units per month |
| Speech | Amazon Polly | Text-to-speech synthesis | Access via credits |
| Speech | Amazon Transcribe | Speech-to-text conversion | 12‑month free trial, 60 minutes per month |
| Computer Vision | Amazon Rekognition | Image and video analysis | Access via credits |
| Document Processing | Amazon Textract | Extract text and data from documents | 3‑month free trial, 1,000 pages per month |

### 1.2 AWS Free Tier New Policy (After July 15, 2025)
- Sign-up bonus: $100 credit
- Task bonus: Up to $100 extra credit for completing 5 guided activities
- Validity: 6 months or until credits are exhausted
- Bedrock exclusive: $20 credit for experimenting in the Bedrock Playground

## 2. API Usage Practice Examples
### 2.1 Amazon Bedrock Basic Usage
- Create a Bedrock Runtime client and configure credentials and region
- Call models using the Converse API with configurable parameters
- Parse response text and view token usage

### 2.2 Amazon Comprehend Sentiment Analysis
- Invoke sentiment detection for Chinese and English text
- Return sentiment labels (POSITIVE, NEGATIVE, NEUTRAL, MIXED) and confidence scores
- Use free monthly quota for small‑scale applications

### 2.3 Cost Estimation Examples
- Calculate monthly costs based on model input/output token pricing
- Compare cost efficiency across Amazon Nova, Llama, and Claude models
- Estimate total expense by monthly call volume and average token length

## 3. Cost Monitoring & Optimization Strategies
### 3.1 Core Monitoring Tools
| Tool | Purpose | Key Features |
|------|---------|--------------|
| AWS Cost Explorer | Cost visualization and analysis | Filter by service/region/tag, forecast costs |
| AWS Budgets | Budget management and alerts | Set cost/usage thresholds, automatic notifications |
| CloudWatch Metrics | Real‑time performance monitoring | Track Bedrock latency, token quota usage |
| Cost Anomaly Detection | Unusual spend detection | ML‑powered automatic cost anomaly alerts |

### 3.2 Optimization Recommendations
#### Maximize free tier usage
- Prioritize 12‑month free services (Comprehend, Transcribe)
- Use Bedrock credits for early prototyping
- Plan $200 sign‑up credit usage across 6 months

#### Model selection strategy
- Simple tasks: Amazon Nova Micro / Lite (lowest cost)
- Medium complexity: Meta Llama 3.3 70B (high cost‑performance)
- High accuracy: Claude Sonnet (use only when required)

#### API usage efficiency
- Batch requests to reduce API calls
- Enable caching for repeated queries
- Set reasonable max_tokens to avoid over‑generation

#### Security‑cost balance
- Use standard KMS encryption tiers
- Follow least privilege for IAM permissions
- Audit access logs regularly to detect anomalies

## 4. Security Architecture Design
### 4.1 Core Security Components
#### Intelligent Customer Service System Security Architecture
- **Identity & Access Management (IAM)**
  - Least privilege principle
  - Role separation: dev / ops / audit
  - MFA enforcement
- **Data Protection Layer**
  - KMS encryption for data at rest and in transit
  - Data anonymization
  - Automatic PII detection and redaction
- **Network & Infrastructure Security**
  - VPC isolation and security groups
  - WAF protection for API Gateway
  - DDoS protection
- **Monitoring & Compliance**
  - CloudTrail audit logs
  - Config compliance checks
  - GuardDuty threat detection

### 4.2 Key Security Practices
#### Data privacy protection
- Anonymize input data (remove PII)
- Review and filter output content
- Compliance checks (GDPR, CCPA)

#### API security
- API Gateway authentication and authorization
- Rate limiting and quota management
- Input validation and injection protection

#### Deployment security
- Container security scanning
- Infrastructure‑as‑Code (IaC) security review
- Key management and rotation

## 5. Intelligent Customer Service System Architecture Design
### 5.1 Overall System Architecture
#### Client Layer
- Web App (React)
- Mobile App (Flutter)
- API integration interface

#### Access Layer
- API Gateway (routing, throttling)
- CloudFront (CDN)
- WAF

#### Business Logic Layer
- Lambda (serverless logic)
- Step Functions (orchestration)
- SQS/SNS (messaging)

#### AI Service Layer
- Amazon Bedrock (foundation models)
- Amazon Lex (dialog management)
- Amazon Comprehend (sentiment analysis)
- Amazon Translate (multilingual support)

#### Data Layer
- DynamoDB (sessions, knowledge base)
- RDS PostgreSQL (structured data)
- S3 (file storage, logs)
- OpenSearch (intelligent search)

#### Operations & Monitoring Layer
- CloudWatch (monitoring, alerts)
- X-Ray (distributed tracing)
- CloudTrail (audit logs)

### 5.2 Technology Selection Table
| Component | Technology | Reason | Cost Consideration |
|-----------|------------|--------|--------------------|
| Frontend | React + TypeScript | Componentized, rich ecosystem | Static hosting on S3 + CloudFront |
| API Gateway | Amazon API Gateway | Auth, throttling, monitoring | Pay‑per‑use, generous free tier |
| Business Logic | AWS Lambda | Serverless, auto‑scaling | Pay‑per‑request, no idle cost |
| Workflow | Step Functions | Visual orchestration, error handling | Pay‑per‑state‑transition |
| AI Services | Amazon Bedrock | Multi‑model, unified API | Pay‑per‑token, controllable |
| Dialog Management | Amazon Lex | Prebuilt intent, multi‑turn | Pay‑per‑request |
| Database | DynamoDB | Serverless, scalable | Pay‑per‑read/write |
| Search | OpenSearch | Full‑text & semantic search | Pay‑per‑node‑hour |
| Monitoring | CloudWatch | Native integration | Free basic metrics |

### 5.3 Deployment Plan
#### Development environment
- Local: Docker containerization
- CI testing: GitHub Actions + AWS SAM
- Repository: GitHub with branch protection

#### Deployment pipeline
- Code commit → unit test → build → deploy to staging
- Approval → production deployment
- Blue/green deployment for minimal downtime

#### Infrastructure management
- Terraform (IaC)
- Environment separation: dev / staging / prod
- Parameter store: SSM Parameter Store

## 6. Monthly Cost Budget Table
### 6.1 Estimated Usage & Cost
| Service | Free Quota | Estimated Usage | Estimated Cost | Optimization Tips |
|---------|------------|-----------------|----------------|-------------------|
| AWS Bedrock | $20 credit | 100,000 tokens | $0.20 | Use Nova series, cache queries |
| AWS Comprehend | 50K units | 10,000 calls | $0.00 | Within free tier |
| AWS Lambda | 1M requests | 200,000 requests | $0.40 | Optimize duration, reduce cold starts |
| API Gateway | 1M calls | 500,000 calls | $1.50 | Enable caching |
| DynamoDB | 25GB storage | 10GB | $0.00 | Within free tier |
| S3 | 5GB storage | 3GB | $0.00 | Within free tier |
| CloudWatch | Basic free | 1GB logs | $0.50 | Set retention policy |
| **Total** | — | — | **$2.60** | Keep under $3 per month |

### 6.2 Budget Alert Setup
- Create monthly budget with a $10 threshold
- Set alert at 80% of budget
- Send email notifications for over‑threshold spending

## 7. Security Checklist
### 7.1 Required Security Measures
#### Identity & Access Management
- Enable IAM MFA
- Create least‑privilege IAM roles
- Role separation: dev / ops / audit
- Rotate access keys regularly

#### Data Protection
- Enable S3 bucket encryption (KMS)
- Enable DynamoDB encryption at rest
- Enforce TLS 1.2+ for transit
- Deploy data anonymization

#### Network Protection
- Security groups with minimum exposure
- Deploy WAF
- Enable Shield Standard DDoS protection
- Implement NACLs

#### Monitoring & Auditing
- Enable CloudTrail in all regions
- Configure CloudWatch alerts
- Deploy GuardDuty
- Regular security audits

### 7.2 Compliance Checks
- GDPR compliance: data processing agreements, user rights
- CCPA compliance: California consumer privacy
- HIPAA: if handling health data
- SOC 2: if required for enterprise customers

## 8. Knowledge Quiz
### Multiple Choice (Single Answer)
1. What is the AWS Bedrock free tier primarily based on?
   A. Fixed monthly quota
   B. Credit‑based access ✅
   C. Fully free unlimited
   D. Enterprise only

2. Which model offers the best cost‑performance for simple text classification?
   A. Claude Sonnet 4.5
   B. Amazon Nova Micro ✅
   C. Meta Llama 3.3 70B
   D. Cohere Command R

3. What is the best tool to monitor AWS AI API costs?
   A. AWS Config
   B. AWS Cost Explorer ✅
   C. AWS Trusted Advisor
   D. AWS Systems Manager

4. What is the top measure to protect data privacy in AI applications?
   A. Use the most expensive model
   B. Data anonymization ✅
   C. Deploy multiple firewalls
   D. Enable all monitoring

5. Which service is core to serverless architecture in the customer service system?
   A. EC2
   B. RDS
   C. AWS Lambda ✅
   D. ECS

### True / False
- Amazon Comprehend offers permanent free sentiment analysis. ❌ (12‑month free trial)
- Setting AWS budget alerts helps prevent unexpected costs. ✅
- Enabling KMS encryption significantly increases cost. ❌ (Standard tier is low cost)
- Caching reduces Bedrock API call volume. ✅
- Blue/green deployment minimizes downtime during updates. ✅

## 9. Daily Execution Card
### 3 Key Takeaways
1. Understood AWS AI tiered pricing: learned to select cost‑efficient models from Nova Micro to Claude Sonnet based on project needs.
2. Mastered cloud cost monitoring tools: used Cost Explorer, Budgets, and CloudWatch to track spending and performance.
3. Built end‑to‑end security architecture thinking: gained the ability to design complete protection from IAM, encryption, to network security.

### 1 Question / Challenge
Question: In real projects, how to balance strict security measures and development efficiency? Frequent KMS key rotation and IAM policy updates increase operational overhead—how to find the optimal balance?

### 1 Insight / Adjustment
Insight: The real value of cloud AI services is not only technical capability but also pay‑as‑you-go and scalable economics. Even small teams can build enterprise‑grade AI applications. This democratized access drives widespread AI innovation.

## 10. Next Action Plan
- Tomorrow noon: Review today’s cloud service content and complete the quiz
- Tomorrow evening: Start Day 6 hands‑on: intelligent customer service prototype development
- This weekend: Deliver MVP version of the intelligent customer service system
- Long-term: Continuously monitor cost and performance, iterate security measures

### Core Weekly Goal
Build a runnable intelligent customer service system on AWS AI services with verified security and cost control.
