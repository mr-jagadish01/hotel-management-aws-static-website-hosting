# Live Demo

This document summarizes the live demo deployment and evidence for the Royal Palace Hotel Website.

## Live Deployment Summary

- **AWS S3 bucket:** `royal-palace-website`
- **Region:** `us-east-1`
- **CloudFront distribution ID:** `E8RAZPQ0JFC6B`
- **CloudFront distribution name:** `royal-palace-website`
- **CloudFront domain:** `d4e4x7kim5lj.cloudfront.net`
- **CloudFront origin:** `royal-palace-website.s3`
- **CloudFront ARN:** `arn:aws:cloudfront::800889009437:distribution/E8RAZPQ0JFC6B`
- **Default root object:** `index.html`
- **Price class:** Use all edge locations (best performance)
- **Supported HTTP versions:** HTTP/2, HTTP/1.1, HTTP/1.0
- **Alternate domain names:** none
- **Standard logging:** Off
- **Cookie logging:** Off
- **Last modified:** June 23, 2026 at 3:33:46 AM UTC
- **HTTPS:** enabled (verify in CloudFront Security tab)

## Live URL

- CloudFront URL: `https://d4e4x7kim5lj.cloudfront.net`
- Custom domain: `TBD`

## Validation Checklist

- [x] Static assets uploaded to S3
- [x] CloudFront distribution created and enabled
- [x] Default root object set to `index.html`
- [x] HTTPS enabled with CloudFront
- [ ] Contact form backend verified (requires PHP-enabled hosting)

## Visual Evidence

1. `AWS-Console-screenshot/Screenshot 2026-06-28 192101.png`
   - S3 bucket list showing `royal-palace-website`
2. `AWS-Console-screenshot/Screenshot 2026-06-28 192123.png`
   - S3 objects view with website files
3. `AWS-Console-screenshot/Screenshot 2026-06-28 192158.png`
   - CloudFront distribution detail page
4. `AWS-Console-screenshot/Screenshot 2026-06-28 192234.png`
   - CloudFront distribution list view

## Notes

- The deployment is confirmed via AWS console screenshots.
- The static website should be accessible through the CloudFront URL.
- If the site is not accessible, verify S3 bucket permissions and CloudFront origin settings.
- Contact form submission is not validated in the static S3 deployment.
