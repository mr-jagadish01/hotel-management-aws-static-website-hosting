# Architecture Overview

## Project Summary

The Royal Palace Hotel Website is a static frontend deployed on AWS using Amazon S3 for storage and Amazon CloudFront as a CDN.
This architecture provides global distribution, HTTPS delivery, and scalable static web hosting for the hotel's website assets.

## Architecture Diagram

```text
+----------------------+      +-------------------------+      +-------------------------+
|  Ubuntu Terminal     | ---> |  AWS IAM Credentials    | ---> |  Amazon S3 Bucket       |
|  (AWS CLI)           |      |  (aws configure)        |      |  Royal Palace Files     |
+----------------------+      +-------------------------+      +-------------------------+
                                           |
                                           v
                                 +-------------------------+
                                 |  S3 Bucket Policy       |
                                 |  Public Read Access     |
                                 +-------------------------+
                                           |
                                           v
                                 +-------------------------+
                                 |  S3 Website Endpoint    |
                                 |  HTTP Testing URL       |
                                 +-------------------------+
                                           |
                                           v
                                 +-------------------------+
                                 |  CloudFront Distribution|
                                 |  Default Root: index.html|
                                 +-------------------------+
                                           |
                                           v
+-------------------+      +-------------------------+      +-------------------------+
|  End User Browser | <--- |  HTTPS Enabled          | <--- |  SSL Managed by ACM     |
|  (HTTPS Request)  |      |  Redirect HTTP         |      |                         |
+-------------------+      +-------------------------+      +-------------------------+
                                           |
                                           v
                                 +-------------------------+
                                 |  Cache Invalidation     |
                                 |  Refresh Content        |
                                 +-------------------------+
                                           |
                                           v
                                 +-------------------------+
                                 |  End Users              |
                                 |  HTTPS Website Live     |
                                 +-------------------------+
```

## Components

- **Amazon S3**
  - Bucket name: `royal-palace-website`
  - Region: `us-east-1`
  - Content: `index.html`, `inner-page.html`, `portfolio-details.html`, `assets/`
  - Static website hosting enabled
- **S3 Bucket Policy**
  - Public read access configured for static assets
  - Provides HTTP testing URL and origin access
- **S3 Website Endpoint**
  - Used for initial HTTP testing and origin configuration
  - Not the final public URL when CloudFront is enabled
- **Amazon CloudFront**
  - Distribution ID: `E8RAZPQ0JFC6B`
  - Distribution name: `royal-palace-website`
  - Domain name: `d4e4x7kim5lj.cloudfront.net`
  - Origin domain: `royal-palace-website.s3`
  - Default root object: `index.html`
  - Price class: `Use all edge locations (best performance)`
  - Supported HTTP versions: `HTTP/2, HTTP/1.1, HTTP/1.0`
  - Alternate domain names: none
  - Standard logging: Off
  - Cookie logging: Off
  - Serves assets from edge locations with low latency
- **AWS Certificate Manager (ACM)**
  - Provides SSL certificate for secure HTTPS delivery
- **Browser / End User**
  - Accesses the site over HTTPS through CloudFront
  - Receives cached content after invalidation and refresh

## Deployment Topology

1. Deployment begins in the terminal using AWS CLI and IAM credentials.
2. Files are uploaded to the S3 bucket and public read access is configured.
3. The S3 website endpoint provides HTTP testing access.
4. CloudFront distribution is configured with the S3 origin and default root object.
5. HTTPS is enforced and managed by ACM at the CloudFront edge.
6. Cache invalidation refreshes content for end users.
7. Users access the website via HTTPS through CloudFront.

## Evidence Images

- `AWS-Architecture-screenshot/architecture.png`
- `AWS-Architecture-screenshot/workflow.png`
- `AWS-Console-screenshot/Screenshot 2026-06-28 192101.png`
- `AWS-Console-screenshot/Screenshot 2026-06-28 192123.png`
- `AWS-Console-screenshot/Screenshot 2026-06-28 192158.png`
- `AWS-Console-screenshot/Screenshot 2026-06-28 192234.png`

## Notes

- The architecture is appropriate for static content delivery and portfolio presentation.
- The contact form functionality requires additional backend hosting beyond static S3 deployment.
- Any custom domain or DNS configuration is not present in the repository and is marked `TBD` if required.
