# Cloud Fun Facts Generator

### Full-Stack AWS Serverless Project | Recruiter-Ready Portfolio Build

A production-style AWS cloud project designed to showcase hands-on engineering ability using real AWS services.

This repository demonstrates how I designed, built, secured, tested, and deployed a complete cloud-native application using modern serverless architecture.


---

# 🌐 Live Product Idea

Users open a website, click a button, and instantly receive a random cloud computing fact powered by AWS services.

---

# 🏗️ Architecture

```text
User Browser
   ↓
AWS Amplify Hosting
   ↓
API Gateway HTTP API
   ↓
AWS Lambda (Python)
   ↓
Amazon DynamoDB

### Tech Stack
Category	Tools
Cloud Platform	AWS
Compute	Lambda
API Layer	API Gateway
Database	DynamoDB
Hosting	Amplify
Security	IAM
Language	Python
Frontend	HTML / CSS / JavaScript

### Project Breakdown
1️⃣ ### AWS Lambda Backend

Created a serverless Lambda function named:

CloudFunFacts
Responsibilities
Query DynamoDB
Select a random fact
Return JSON response
Handle API requests
Example Output
{
  "fact": "Netflix runs almost all infrastructure on AWS."
}

📸 Proof of Work
Lambda Function Creation

Lambda Test Event Success

2️⃣ ### DynamoDB Database Layer

Created a NoSQL database table:

Table Name	Key
CloudFacts	FactID
Each Record Stores
FactID
FactText

This allows content updates without touching backend code.

📸 Proof of Work
DynamoDB Table

3️⃣ ### IAM Security Configuration

Applied least-privilege permissions so Lambda can securely access required resources.

Policies Configured
CloudWatch Logs
DynamoDB Read Access
📸 Proof of Work
DynamoDB Access Policy Added


4️⃣ ### API Gateway Public API

Created an HTTP API:

FunfactsAPI
Route
GET /funfact

This makes the Lambda publicly accessible.

📸 Proof of Work
API Endpoint Created

Public API Working

5️⃣ ### Frontend Hosted on AWS Amplify

Built a responsive frontend where users click a button to generate cloud facts.

### Features
Clean modern UI
Mobile responsive
Live backend integration
Hosted globally
HTTPS enabled
📸 Proof of Work
Amplify Deployment Dashboard

Live Application Running

### Core Lambda Code
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

### Skills Demonstrated
Cloud Engineering
AWS multi-service integration
Serverless design
Scalable architecture
Cost-efficient deployments
Security
IAM least privilege
Controlled access management
Backend Development
Python Lambda functions
JSON APIs
AWS SDK (Boto3)

### Frontend Development
JavaScript API calls
Responsive design
User interaction workflows
DevOps Mindset
Testing
Debugging
Deployment
Monitoring awareness

### What I Learned

Through this build I gained real-world experience in:

Building serverless applications
Connecting managed AWS services
Solving deployment issues
Hosting public web apps
Working with cloud security controls
Delivering end-to-end products

🔮 Future Improvements

### Planned next versions

Amazon Bedrock AI generated facts
User authentication with Cognito
CI/CD pipelines
Terraform IaC
Monitoring dashboards
Custom domain
Usage analytics


Built and deployed a full-stack AWS serverless application using Lambda, API Gateway, DynamoDB, IAM, and Amplify, delivering a publicly accessible cloud-native web application with secure backend integrations.

📸 Repository Screenshot Assets

Ensure these files remain inside the repository root:

test-event.jpg
Dynamo-table.jpg
dynamodb-access-policy-aded.jpg
function-creation.jpg
funfact-accessible.jpg
bedrock-policy.jpg
API-Endpoint.jpg
amplify-app-goes-live.jpg
amplify-app-deployed.jpg

