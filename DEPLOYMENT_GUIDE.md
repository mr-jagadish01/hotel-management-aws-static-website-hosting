# Deployment Guide

This deployment guide documents the AWS hosting setup for the Royal Palace Hotel Website.
It covers S3 hosting, CloudFront distribution, security settings, and validation steps.

## 1. Prepare the Project

1. Confirm the repository contains:
   - `index.html`
   - `inner-page.html`
   - `portfolio-details.html`
   - `assets/`
   - `forms/`
2. Verify the homepage and asset paths are relative and compatible with static hosting.

## 2. Create and Configure S3 Bucket

1. Create S3 bucket: `royal-palace-website`
2. Select region: `us-east-1`
3. Enable public access settings for website hosting if required.
4. Upload website files to the bucket root.

### S3 Static Website Hosting
- Index document: `index.html`
- Error document: `404.html` (optional, not included in the repo)

### Bucket Policy
Add a bucket policy to allow public read access for website assets:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::royal-palace-website/*"
    }
  ]
}
```

## 3. Configure CloudFront Distribution

1. Create CloudFront distribution.
2. Set origin domain to `royal-palace-website.s3` for the S3 bucket origin.
3. Set default root object to `index.html`.
4. Configure Viewer Protocol Policy: `Redirect HTTP to HTTPS`.
5. Enable compression for common static file types.
6. If using a custom domain, attach the ACM certificate and add the domain to the distribution.

### CloudFront Settings Summary
- Origin: `royal-palace-website.s3`
- Default Root Object: `index.html`
- Viewer Protocol Policy: Redirect HTTP to HTTPS
- Price class: Use all edge locations (best performance)
- Supported HTTP versions: HTTP/2, HTTP/1.1, HTTP/1.0
- Alternate domain names: none
- Standard logging: Off
- Cookie logging: Off
- Allowed HTTP Methods: `GET, HEAD`
- TTL Settings: default `86400` seconds (TBD depending on cache strategy)

## 4. Optional: Configure HTTPS with ACM

1. Request or import a certificate in AWS Certificate Manager.
2. Select the certificate for CloudFront distribution.
3. Confirm the certificate is issued and valid.

## 5. Deploy Updates

### Upload files to S3
Use AWS CLI to sync the project files to the S3 bucket:

```bash
aws s3 sync . s3://royal-palace-website --delete
```

### Invalidate CloudFront Cache
After updates, invalidate CloudFront to ensure fresh content:

```bash
aws cloudfront create-invalidation --distribution-id E8RAZPQ0JFC6B --paths "/*"
```

## 6. Verify Deployment

- Confirm website loads from CloudFront domain.
- Validate HTTPS and SSL certificate.
- Check asset paths and page navigation.
- Confirm `index.html` is served as the default root object.

## 7. Security and Best Practices

- Keep the S3 bucket policy scoped to only the required bucket.
- Use CloudFront for secure HTTPS delivery.
- Avoid storing sensitive data in the bucket.
- Use IAM least privilege for deployment credentials.

## 8. Notes and TBD

- Custom domain name configuration: `TBD`
- DNS records / Route 53 setup: `TBD`
- Server-side contact form deployment for `forms/contact.php`: `TBD`

## Visual References

- `AWS-Architecture-screenshot/workflow.png`
- `AWS-Console-screenshot/Screenshot 2026-06-28 192101.png`
- `AWS-Console-screenshot/Screenshot 2026-06-28 192123.png`
- `AWS-Console-screenshot/Screenshot 2026-06-28 192158.png`
- `AWS-Console-screenshot/Screenshot 2026-06-28 192234.png`
