# AWS Serverless URL Shortener

A production-ready serverless URL shortener built on AWS. All business logic runs at the API Gateway level — no Lambda or compute required.

## 🔗 Live Demo
https://master.d379yxg4f0t2fp.amplifyapp.com

## Architecture
User → CloudFront → API Gateway → DynamoDB
                 ↓
            Cognito (Auth)
                 ↓
         Amplify (Vue.js Frontend)

## AWS Services Used
- Amazon API Gateway - Business logic and URL routing
- Amazon DynamoDB - URL storage
- Amazon Cognito - User authentication
- AWS Amplify - Frontend hosting and CI/CD
- Amazon CloudFront - CDN
- Amazon S3 - Static assets
- AWS SAM - Infrastructure as Code

## Features
- Serverless with zero compute cost at rest
- Secure authentication via Cognito
- Create, update, delete short URLs
- Vue.js dashboard
- Globally distributed via CloudFront

## Deployment
```bash
sam deploy -g
```

## Author
Gayatri Sawant
- GitHub: https://github.com/sawantgayatri19
- LinkedIn: https://linkedin.com/in/gayatri-saw
