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

## Architecture Components

- **Ubuntu Terminal / AWS CLI**
  - Entry point for deployment commands and AWS configuration.
- **AWS IAM Credentials**
  - Provides authorized access for S3 and CloudFront operations.
- **Amazon S3 Bucket**
  - Stores static website files and serves content via static website hosting.
- **S3 Bucket Policy**
  - Grants public read access to website assets.
- **S3 Website Endpoint**
  - Used for initial HTTP website testing.
- **CloudFront Distribution**
  - Distributes content globally from the S3 origin and uses `index.html` as the default root object.
- **HTTPS Enabled / SSL Managed by ACM**
  - Secures site delivery and enables HTTPS redirection.
- **Cache Invalidation**
  - Refreshes CloudFront cached content after updates.
- **End Users**
  - Access the live website over HTTPS through CloudFront.

## Architecture Execution

1. Configure AWS CLI in the Ubuntu terminal using IAM credentials.
2. Upload website files to the S3 bucket and enable static website hosting.
3. Configure the S3 bucket policy to allow public read access.
4. Use the S3 website endpoint to test the site over HTTP.
5. Create a CloudFront distribution with the S3 website endpoint as the origin.
6. Set the default root object to `index.html` and enable HTTPS redirection.
7. Apply an ACM-managed SSL certificate for secure delivery.
8. Invalidate CloudFront cache after updates.
9. End users access the website via HTTPS through CloudFront.

## Deployment Workflow Diagram

```text
+----------------------+   +---------------------------+   +------------------------------+   +--------------------------------+
| Local Setup          |-->| Open Ubuntu Terminal      |-->| Install & Configure AWS CLI  |-->| Configure AWS Credentials      |
| Prepare Environment  |   | Open terminal             |   | Verify installation           |   | aws configure                  |
+----------------------+   +---------------------------+   +------------------------------+   +--------------------------------+
                 |                                                                                            |
                 v                                                                                            v
+----------------------+   +-----------------------------+   +--------------------------------+   +-------------------------------------------+
| S3 Setup             |-->| Create S3 Bucket            |-->| Enable Static Website Hosting |-->| Upload Project Files                       |
| Create & Prepare S3  |   | Bucket name: royal-palace-  |   | Index document: index.html     |   | aws s3 sync ./dist s3://royal-palace-site/|
| Bucket               |   | site                        |   |                                |   |                                           |
+----------------------+   +-----------------------------+   +--------------------------------+   +-------------------------------------------+
                 |                                                                                            |
                 v                                                                                            v
+---------------------------+   +---------------------------------+   +-----------------------------+   +----------------------------------------+
| Security & Access         |-->| Set Bucket Policy               |-->| Get S3 Website Endpoint     |-->| Test Website                           |
| Configure Policy & Access |   | Allow Public Read Access        |   | HTTP URL for testing         |   | Open endpoint in browser (HTTP)        |
+---------------------------+   +---------------------------------+   +-----------------------------+   +----------------------------------------+
                 |                                                                                            |
                 v                                                                                            v
+----------------------+   +---------------------------------+   +-----------------------------+   +-------------------------------+
| CDN Setup            |-->| Create CloudFront Distribution  |-->| Default Root Object         |-->| Configure Settings             |
| Distribute with      |   | Origin: S3 Website Endpoint     |   | Set index.html               |   | Redirect HTTP to HTTPS         |
| CloudFront           |   |                                 |   |                             |   | Enable Compression             |
+----------------------+   +---------------------------------+   +-----------------------------+   +-------------------------------+
                 |                                                                                            |
                 v                                                                                            v
+---------------------------+   +-----------------------------+   +-----------------------------+   +-----------------------------+
| Security & Performance    |-->| Enable HTTPS                |-->| SSL Certificate             |-->| Global CDN                  |
| Secure & Optimize         |   | Redirect HTTP Requests       |   | Managed by AWS (ACM)        |   | Content delivered via edge    |
|                           |   |                             |   |                             |   | locations                    |
+---------------------------+   +-----------------------------+   +-----------------------------+   +-----------------------------+
                 |                                                                                            |
                 v                                                                                            v
+---------------------------+   +-----------------------------+   +-----------------------------+   +-----------------------------+
| Cache Management          |-->| Invalidate Cache            |-->| Deploy Updates              |-->| Verify Changes               |
| Keep Content Up-to-Date   |   | Use /* to clear cached content|   | Upload new files to S3      |   | Check updated website content |
+---------------------------+   +-----------------------------+   +-----------------------------+   +-----------------------------+
                 |                                                                                            |
                 v                                                                                            v
+-------------------------+   +-----------------------------+   +-----------------------------+   +--------------------------------+
| End Users              |-->| Access Website              |-->| Users Browse Website         |-->| Website Live Success            |
| Website Live & Accessible|  | Via CloudFront Domain (HTTPS)|   | Fast, Secure & Reliable      |   | Hotel Management Website is Live|
+-------------------------+   +-----------------------------+   +-----------------------------+   +--------------------------------+
```

## Workflow Components

- **Local Setup**
  - Prepare environment for deployment
  - Open Ubuntu terminal
  - Install and verify AWS CLI
  - Configure AWS credentials via `aws configure`
- **Amazon S3 Setup**
  - Create S3 bucket named `royal-palace-site`
  - Enable static website hosting
  - Set index document to `index.html`
  - Upload website files with `aws s3 sync ./dist s3://royal-palace-site/`
- **Security & Access**
  - Configure S3 bucket policy for public read access
  - Use the S3 website endpoint for HTTP testing
  - Validate website availability and asset loading
- **CloudFront CDN Setup**
  - Create CloudFront distribution using the S3 website endpoint origin
  - Set default root object to `index.html`
  - Redirect HTTP to HTTPS and enable compression
- **Security & Performance**
  - Enable HTTPS with redirect from HTTP
  - Use AWS Certificate Manager (ACM) for SSL
  - Deliver content through global CDN edge locations
- **Cache Management**
  - Invalidate CloudFront cache using `/*`
  - Deploy updated files to S3
  - Verify latest content is live on the website
- **End User Access**
  - Users access the site via CloudFront domain over HTTPS
  - The website is fast, secure, and reliable
  - Website is live and ready for users

## Workflow Execution

1. Start locally on the terminal and configure AWS CLI credentials.
2. Create and configure the S3 bucket for static website hosting.
3. Upload the project files to S3 and verify `index.html` is in the bucket root.
4. Apply public read bucket policy, then test the S3 website endpoint in a browser.
5. Configure CloudFront distribution with the S3 endpoint as origin and enforce HTTPS.
6. Use ACM-managed SSL and global CDN distribution for secure delivery.
7. Invalidate CloudFront cache after updates, deploy new files to S3, and confirm the site is updated.

## Evidence Images

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
