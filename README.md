# AWS Serverless URL Shortener

A production-ready serverless URL shortener built on AWS. This application shortens long URLs without using any compute layer like AWS Lambda — all business logic runs directly at the API Gateway level.

## Live Demo
[Add your deployed URL here after deployment]

## Architecture Overview
```
User → CloudFront → S3 (Vue.js Frontend)
         ↓
    API Gateway (Business Logic)
         ↓
    DynamoDB (URL Storage)
         ↑
    Cognito (Authentication)
```

## AWS Services Used

| Service | Purpose |
|---|---|
| Amazon API Gateway | Core business logic, URL routing and redirects |
| Amazon DynamoDB | Stores original and shortened URL mappings |
| Amazon Cognito | User authentication and authorization |
| AWS Amplify | CI/CD pipeline and frontend hosting |
| Amazon CloudFront | CDN for fast global access |
| Amazon S3 | Static asset storage for frontend |
| AWS SAM | Infrastructure as Code for deployment |

## Features

- Serverless architecture with zero compute cost at rest
- Secure user authentication via Amazon Cognito
- Create short URLs from long URLs
- Update and delete existing short URLs
- Vue.js dashboard to manage all your links
- Globally distributed via CloudFront CDN
- Fully automated deployment via AWS SAM

## Tech Stack

- **Frontend:** Vue.js, hosted on AWS Amplify
- **Backend:** Amazon API Gateway (no Lambda)
- **Database:** Amazon DynamoDB
- **Auth:** Amazon Cognito
- **IaC:** AWS SAM (CloudFormation)

## Prerequisites

- AWS Account
- AWS CLI configured
- AWS SAM CLI v0.37.0+
- Node.js and npm

## Deployment

### Step 1: Clone the repository
```bash
git clone https://github.com/sawantgayatri19/url-shortener-aws.git
cd url-shortener-aws
```

### Step 2: Deploy using SAM
```bash
sam deploy -g
```

### Step 3: Configure environment variables
After deployment, update Amplify environment variables:
```bash
aws amplify update-app --app-id <MyAmplifyAppId> --environment-variables \
VUE_APP_NAME=<VueAppName>\
,VUE_APP_CLIENT_ID=<VUE_APP_CLIENT_ID>\
,VUE_APP_API_ROOT=<VUE_APP_API_ROOT>\
,VUE_APP_AUTH_DOMAIN=<VUE_APP_AUTH_DOMAIN>
```

### Step 4: Trigger first build
```bash
aws amplify start-job --app-id <MyAmplifyAppId> --branch-name master --job-type RELEASE
```

## Screenshots
[Add screenshots after deployment]

## Cleanup
To delete all AWS resources:
1. Open CloudFormation console
2. Find stack named URLShortener
3. Select and delete the stack

## Author
Gayatri Sawant
- GitHub: [@sawantgayatri19](https://github.com/sawantgayatri19)
- LinkedIn: [Gayatri Sawant](https://www.linkedin.com/in/gayatri-saw)
