# Quick Reference

A one-page quick reference for deploying and maintaining the Royal Palace Hotel Website.

## Key AWS Resources

- S3 Bucket: `royal-palace-website`
- CloudFront Distribution ID: `E8RAZPQ0JFC6B`
- CloudFront Domain: `d4e4x7kim5lj.cloudfront.net`
- Default Root Object: `index.html`
- Region: `us-east-1`

## Useful Commands

### Upload website files to S3

```bash
aws s3 sync . s3://royal-palace-website --delete
```

### Invalidate CloudFront cache

```bash
aws cloudfront create-invalidation --distribution-id E8RAZPQ0JFC6B --paths "/*"
```

### Verify AWS credentials

```bash
aws sts get-caller-identity
```

## Deployment Tips

- Keep the S3 bucket public only for static web assets.
- Set the CloudFront Viewer Protocol Policy to `Redirect HTTP to HTTPS`.
- Use `index.html` as the default root object.
- Validate asset URLs after deployment.

## Troubleshooting

- If the website shows 403 errors, check the S3 bucket policy.
- If CloudFront returns stale content, invalidate the cache.
- If HTTPS is not working, confirm the ACM certificate is attached and valid.

## Visual Reference Files

- `AWS-Architecture-screenshot/architecture.png`
- `AWS-Architecture-screenshot/workflow.png`
- `AWS-Console-screenshot/Screenshot 2026-06-28 192101.png`
- `AWS-Console-screenshot/Screenshot 2026-06-28 192123.png`
- `AWS-Console-screenshot/Screenshot 2026-06-28 192158.png`
- `AWS-Console-screenshot/Screenshot 2026-06-28 192234.png`
