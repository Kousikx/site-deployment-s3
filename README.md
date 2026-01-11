## Deploying a Live DevOps Portfolio Website using GitHub Actions on AWS S3 | CI/CD automation

This project is a hands-on DevOps implementation where I built and deployed my DevOps portfolio website using AWS S3 and GitHub Actions. The main goal of this project was to understand real-world CI/CD, automate deployments, and host a website without managing servers.
Every time I push code to the main branch, the website gets deployed automatically.

### Tools & Technologies Used
•	AWS S3 – Hosting the static website.
•	AWS IAM – Managing secure access and permissions.
•	Git & GitHub – Source code management.
•	GitHub Actions – CI/CD automation.
•	Ubuntu (GitHub Runner) – Deployment environment.

### Deployment Works ----
1.	I push changes to the main branch
2.	GitHub Actions automatically starts the workflow
3.	AWS credentials are securely loaded using GitHub Secrets
4.	Website files are synced to the S3 bucket
5.	The live website gets updated instantly

### GitHub Push → GitHub Actions → AWS S3 → Live Website

### Demo website is available at: http://weits-demo.s3-website-us-east-1.amazonaws.com

### I Learned from This Project
•	How CI/CD pipelines actually work in production
•	Secure handling of AWS credentials
•	Automating deployments without servers
•	Using GitHub Actions instead of traditional CI tools
•	Debugging real pipeline failures
Last updated on 11 Jan 2026


### GitHub Actions Workflow
The workflow file is placed inside:.github/workflows/deploy.yml

### Deployment Workflow
```yaml
name: Website Deployment
on:
  push:
    branches:
      - main
jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v3
      - name: Configure AWS credentials
        uses: aws-actions/configure-aws-credentials@v2
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: us-east-1
      - name: Deploy website to S3
        run: aws s3 sync . s3://weits-demo --delete





Last updated on 10 Jan 2026


