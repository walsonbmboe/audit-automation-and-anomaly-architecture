# 📄 Automated Audit & Anomaly Detection (AWS Architecture)

This project demonstrates a scalable cloud-native audit pipeline using AWS services, focused on text extraction, report generation, auditee scoring, anomaly detection and scoring, and document lifecycle automation.
## ⚙️ Architecture Components
- **Amazon S3** – stores uploaded audit files
- **Amazon Textract** – extracts text from scanned documents
- **AWS Lambda** – orchestrates processing and invokes AI/ML services
- **Amazon SageMaker / Bedrock** – performs report genertion as well as anomaly detection or enrichment
- **AWS Step Functions** – manages workflow transitions
- **Amazon EventBridge** – triggers pipeline on S3 upload
- **DynamoDB & Athena** – stores audit metadata and enables queries
- **KMS / IAM / GuardDuty / CloudTrail / CloudWatch / WAF** – ensures security and compliance

## 🗺️ Architecture Overview

![Audit Pipeline Diagram](architecture.png)

## 🚀 How to Deploy (AWS CLI)

```bash
aws cloudformation create-stack \
  --stack-name AuditAnomalyStack \
  --template-body file://cloudformation/audit_pipeline.yaml \
  --parameters file://template-params.json \
  --capabilities CAPABILITY_IAM
  ```

## 🔄 Workflow Example

1. Upload `audit-document.pdf` to the S3 bucket  
2. EventBridge triggers Lambda  
3. Lambda extracts text using Textract  
4. Calls SageMakerBedrock for report generation and auditee scoring  
5. Results stored in DynamoDB  
6. CloudWatch logs the pipeline activity  

## 📂 Repo Structure

```bash
.
├── README.md
├── architecture.png
├── changelog.md
├── template-params.json
└── cloudformation/
    └── audit_pipeline.yaml

## 📄 License
This project is for personal and educational use by Walson, a certified AWS Solutions Architect.

## 📬 Contact
Built by Walson – aspiring Cloud Architect http://www.linkedin.com/in/mboewalsonbaiye



