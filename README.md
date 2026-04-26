# CloudFunFacts – Serverless AWS Project

A full-stack serverless web application that delivers random cloud computing facts using AWS services.

---

![screenshots/amplify-app-goes-live.jpg](screenshots/amplify-app-goes-live.jpg)

## Architecture Flow

User Browser  
→ AWS Amplify Hosting  
→ API Gateway (HTTP API)  
→ AWS Lambda (Python)  
→ Amazon DynamoDB  

---

## Tech Stack

| Category | Tools |
|----------|------|
| Cloud Platform | AWS |
| Compute | Lambda |
| API Layer | API Gateway |
| Database | DynamoDB |
| Hosting | Amplify |
| Security | IAM |
| Language | Python |
| Frontend | HTML |

---

## Features

- Random cloud facts generator  
- Serverless backend architecture  
- REST API integration  
- Fully managed NoSQL database  
- Global frontend hosting via Amplify  
- Secure IAM-based access control  

---

## AWS Lambda Backend

Created a serverless function:

**CloudFunFacts**

### Responsibilities:

- Query DynamoDB  
- Select a random fact  
- Return JSON response  
- Handle API requests  

### Example Output:

```
{
  "fact": "Netflix runs almost all infrastructure on AWS."
}
```
---
![screenshots/function-creation.jpg](screenshots/function-creation.jpg)

### DynamoDB Database Layer

Created a table:

CloudFacts

Structure:
FactID (Primary Key)
FactText

Each record stores a cloud computing fact, allowing updates without modifying backend code.

![screenshots/DynamoDB Table](screenshots/Dynamo-table.jpg)

IAM Security Configuration

Applied least-privilege permissions:

CloudWatch Logs access
DynamoDB read access

Ensures Lambda only accesses required resources.

IAM Policy Screenshot

API Gateway

Created HTTP API:

FunfactsAPI

Route:

GET /funfact

This exposes the Lambda function publicly.

![screenshots/API-Endpoint](screenshots/API-Endpoint.jpg)

### Frontend (AWS Amplify)

A responsive web interface where users click a button to generate cloud facts.

Features:
Clean UI design
Mobile responsive layout
Real-time API integration
HTTPS secured hosting
Amplify Deployment Screenshots

Lambda Function Code
```
import boto3
import random
import json

dynamodb = boto3.resource("dynamodb")
table = dynamodb.Table("CloudFacts")

def lambda_handler(event, context):
    response = table.scan()
    items = response.get("Items", [])

    fact = random.choice(items)["FactText"]

    return {
        "statusCode": 200,
        "headers": {"Content-Type": "application/json"},
        "body": json.dumps({"fact": fact})
    }
```
---
![test-event.jpg](screenshots/test-event.jpg)

### Skills Demonstrated
Cloud Engineering
AWS multi-service integration
Serverless architecture
Scalable system design
Security
IAM least privilege
Controlled resource access
Backend Development
Python (Lambda)
REST APIs
AWS SDK (Boto3)
Frontend Development
JavaScript API calls
Responsive UI design
DevOps Mindset
Deployment
Testing
Debugging
Cloud hosting

---
### What I Learned
Building serverless applications on AWS
Integrating multiple cloud services
Deploying full-stack applications
Managing cloud security policies
Designing scalable architectures

---
### Future Improvements
Amazon Bedrock AI-generated facts
User authentication with Cognito
CI/CD pipeline (GitHub Actions)
Infrastructure as Code (Terraform)
Cloud monitoring dashboard
Custom domain setup
Usage analytics

---
![funfact-accessible.jpg](screenshots/funfact-accessible.jpg)

Project Screenshots Gallery

![function-creation.jpg](screenshots/function-creation.jpg)

![Dynamo-table.jpg](screenshots/Dynamo-table.jpg)

![API-Endpoint.jpg](screenshots/API-Endpoint.jpg)

![amplify-app-goes-live.jpg](screenshots/amplify-app-goes-live.jpg)
