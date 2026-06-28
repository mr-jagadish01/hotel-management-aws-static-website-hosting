# Cost Overview

This document provides a cost summary and estimate guidance for the AWS deployment of the Royal Palace Hotel Website.

## Cost Categories

| Category | Service | Notes |
|---|---|---|
| Storage | Amazon S3 | Static asset storage for HTML, CSS, JS, images
| Bandwidth | Amazon CloudFront | Data transfer out to end users globally
| Requests | S3 & CloudFront | S3 GET requests, CloudFront GET/HEAD requests, invalidations
| SSL | AWS Certificate Manager | Certificate management is typically free for ACM certificates
| DNS | Amazon Route 53 | Optional if using a custom domain (not currently configured)

## Estimated Costs

- **Amazon S3 storage:** Very low for static website assets, likely under $1/month for a small portfolio site.
- **CloudFront bandwidth:** Dependent on traffic volume; low monthly traffic should remain under a few dollars.
- **Requests:** Minimal unless the site receives high traffic.
- **ACM certificate:** Free for AWS-managed public certificates.

## Cost Saving Tips

- Use CloudFront caching and invalidations strategically to reduce origin requests.
- Keep object TTL reasonable for static content. For infrequently updated assets, longer cache times reduce request costs.
- Monitor S3 storage usage and remove unused assets.
- Use AWS Free Tier if eligible for low-volume hosting.

## Notes

- This project is deployed as a static website; no compute charges are expected for the core site.
- If backend services are added later (Lambda, API Gateway, hosted PHP server), additional costs will apply.
- Detailed billing numbers are `TBD` unless AWS billing reports are available.

## Visual Evidence

Refer to these images for deployment and architecture context:
- `AWS-Architecture-screenshot/architecture.png`
- `AWS-Architecture-screenshot/workflow.png`
