# 🔗 AWS Serverless URL Shortener

[![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white)](https://aws.amazon.com)
[![Vue.js](https://img.shields.io/badge/Vue.js-%234FC08D.svg?style=for-the-badge&logo=vue.js&logoColor=white)](https://vuejs.org)
[![DynamoDB](https://img.shields.io/badge/Amazon%20DynamoDB-4053D6?style=for-the-badge&logo=Amazon%20DynamoDB&logoColor=white)](https://aws.amazon.com/dynamodb)
[![SAM](https://img.shields.io/badge/AWS%20SAM-FF9900?style=for-the-badge&logo=amazon-aws&logoColor=white)](https://aws.amazon.com/serverless/sam)

A production-ready **serverless URL shortener** built entirely on AWS — with zero compute layer. All business logic is handled directly at the Amazon API Gateway level, eliminating the need for AWS Lambda or any server infrastructure.

## 🔗 Live Demo
**[https://master.d379yxg4f0t2fp.amplifyapp.com](https://master.d379yxg4f0t2fp.amplifyapp.com)**

## 📸 Screenshot
![App Screenshot](screenshot.png)

## 🏗️ Architecture
```
User Request
     │
     ▼
Amazon CloudFront (CDN)
     │
     ├──── Static Assets ──── Amazon S3
     │
     ▼
Amazon API Gateway
(All business logic here - no Lambda!)
     │
     ├──── URL Storage ──── Amazon DynamoDB
     │
     └──── Auth ──── Amazon Cognito
     
Frontend: Vue.js hosted on AWS Amplify
Infrastructure: AWS SAM (CloudFormation)
```

## ☁️ AWS Services Used

| Service | Role |
|---|---|
| **Amazon API Gateway** | Handles all business logic - creates, reads, updates, deletes short URLs |
| **Amazon DynamoDB** | NoSQL database storing URL mappings |
| **Amazon Cognito** | User authentication and authorization |
| **AWS Amplify** | Hosts Vue.js frontend with CI/CD pipeline |
| **Amazon CloudFront** | CDN for fast global content delivery |
| **Amazon S3** | Static asset storage |
| **AWS SAM** | Infrastructure as Code - deploys entire stack |

## ✨ Features

- **Fully Serverless** - No servers, no EC2, no Lambda
- **Zero Compute Cost at Rest** - Only pay when URLs are accessed
- **Secure Authentication** - Cognito user pools with JWT tokens
- **Create Short URLs** - Shorten any long URL instantly
- **Manage Links** - Update and delete your short URLs
- **Global CDN** - CloudFront ensures fast access worldwide
- **Auto CI/CD** - Amplify rebuilds frontend on every git push

## 🚀 Deployment

### Prerequisites
- AWS Account with CLI configured
- AWS SAM CLI v0.37.0+
- Node.js and npm
- GitHub personal access token

### Steps

**1. Clone the repository**
```bash
git clone https://github.com/sawantgayatri19/url-shortener-aws.git
cd url-shortener-aws
```

**2. Deploy with SAM**
```bash
sam deploy -g
```

**3. Follow the prompts**
```
Stack Name: URLShortener
AWS Region: us-west-2
AppName: shortener
GithubRepository: https://github.com/sawantgayatri19/url-shortener-aws
PersonalAccessToken: <your-github-token>
```

**4. Set Amplify environment variables**
```bash
aws amplify update-app --app-id <AmplifyAppId> \
  --environment-variables \
  VUE_APP_NAME=shortener,\
  VUE_APP_CLIENT_ID=<VueAppClientId>,\
  VUE_APP_API_ROOT=<VueAppAPIRoot>,\
  VUE_APP_AUTH_DOMAIN=<VueAppAuthDomain>
```

**5. Trigger first build**
```bash
aws amplify start-job --app-id <AmplifyAppId> --branch-name master --job-type RELEASE
```

## 🧹 Cleanup
```bash
aws cloudformation delete-stack --stack-name URLShortener
```

## 💻 Tech Stack
- **Frontend:** Vue.js, SCSS
- **Backend:** Amazon API Gateway (VTL mapping templates)
- **Database:** Amazon DynamoDB
- **Auth:** Amazon Cognito
- **IaC:** AWS SAM / CloudFormation
- **CI/CD:** AWS Amplify Console

## 👩‍💻 Author
**Gayatri Sawant**
- 🐙 GitHub: [sawantgayatri19](https://github.com/sawantgayatri19)
- 💼 LinkedIn: [Gayatri Sawant](https://www.linkedin.com/in/sawantgayatri/)
