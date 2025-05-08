# Static Website Hosting on Amazon S3

This project demonstrates how to host a static website using *Amazon S3*.

## Features

- Fully static website (HTML, CSS, JS)
- Hosted on Amazon S3
- Public access with static website hosting enabled
- Optional: Custom domain and HTTPS via Amazon CloudFront and Route 53

## Prerequisites

- AWS account
- AWS CLI installed and configured
- Basic knowledge of HTML/CSS/JS

## Setup Instructions

### 1. Create an S3 Bucket

```bash
aws s3 mb s3://your-bucket-name
Bucket name must be globally unique.

Make sure to uncheck "Block all public access" in bucket permissions.

Enable Static website hosting under bucket properties.

2. Upload Website Files
bash
Copy code
aws s3 sync ./website s3://your-bucket-name
3. Set Bucket Policy (to make it public)
Go to the S3 bucket > Permissions > Bucket Policy and add:

json
Copy code
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::your-bucket-name/*"
    }
  ]
}
4. Access Your Website
Go to the Static Website Hosting section in S3 bucket and copy the endpoint URL (e.g., http://your-bucket-name.s3-website-region.amazonaws.com/)
