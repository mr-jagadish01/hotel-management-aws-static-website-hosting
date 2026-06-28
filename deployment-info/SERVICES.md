# AWS Services Inventory

This document describes the AWS services used to host and deliver the Royal Palace Hotel Website.

## Core Services

### Amazon S3
- Purpose: Static website storage and origin for CloudFront
- Bucket name: `royal-palace-website`
- Region: `us-east-1`
- Content: HTML, CSS, JS, images, and static assets
- Hosting type: Static website hosting / origin for CloudFront

### Amazon CloudFront
- Purpose: Content delivery network for low-latency global distribution
- Distribution ID: `E8RAZPQ0JFC6B`
- Distribution name: `royal-palace-website`
- Domain: `d4e4x7kim5lj.cloudfront.net`
- Origin domain: `royal-palace-website.s3`
- Default root object: `index.html`
- Price class: `Use all edge locations (best performance)`
- Supported HTTP versions: `HTTP/2, HTTP/1.1, HTTP/1.0`
- Alternate domain names: none
- Standard logging: Off
- Cookie logging: Off
- HTTPS: enabled
- Cache behavior: static content caching

### AWS Certificate Manager (ACM)
- Purpose: TLS/SSL certificate management for secure HTTPS delivery
- Certificate used by CloudFront: `TBD` (reference certificate ARN or name if available)

## Supporting Services

### AWS Identity and Access Management (IAM)
- Purpose: Deployment credential management and least privilege access
- Recommended role: `S3ReadWriteDeployRole` or similar
- Policy scope: limit access to `royal-palace-website` and CloudFront invalidation

## Optional Services

### Amazon Route 53
- Purpose: Custom domain DNS management
- Current status: `TBD`
- Note: If a custom domain is added, Route 53 can be used for aliasing to CloudFront.

### AWS Lambda / API Gateway
- Purpose: Not currently used. Would be required for server-side contact form handling if extended.
- Status: `TBD`

## Security Services

### AWS WAF (Web Application Firewall)
- Purpose: Optional protection at CloudFront edge
- Current status: `TBD`

### AWS CloudTrail
- Purpose: Audit and governance of AWS API activity
- Current status: `TBD`

## Notes

- The current deployment uses a static site architecture, so the active service set is focused on S3 and CloudFront.
- Any additional backend or custom domain capabilities are marked `TBD` until configured.
