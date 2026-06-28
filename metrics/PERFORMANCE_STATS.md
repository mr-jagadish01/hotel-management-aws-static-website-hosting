# Performance and Metrics

This document tracks performance considerations for the Royal Palace Hotel Website deployed with S3 and CloudFront.

## Performance Goals

- Fast page load for static assets
- Global content delivery via CloudFront
- Secure HTTPS access
- Minimal origin requests through caching

## Key Metrics

| Metric | Target | Status |
|---|---|---|
| Time to First Byte (TTFB) | < 500 ms | TBD |
| First Contentful Paint (FCP) | < 2.5 s | TBD |
| Largest Contentful Paint (LCP) | < 2.5 s | TBD |
| Total Page Size | < 2 MB | TBD |
| Number of Requests | < 50 | TBD |
| HTTPS Coverage | 100% | ✓ |

## Monitoring Strategy

- Use browser developer tools to inspect network load times.
- Validate CDN caching by measuring responses served from CloudFront.
- Use Lighthouse or PageSpeed Insights for performance scoring.
- Track CloudFront cache hit ratio and error rate in AWS console.

## Recommendations

- Compress CSS, JS, and image assets.
- Use CloudFront caching headers and versioned asset filenames if updates are frequent.
- Keep static HTML lightweight and load images lazily if possible.
- Review `assets/css/style.css` and `assets/js/main.js` for any heavy blocking resources.

## Evidence Images

- `AWS-Architecture-screenshot/architecture.png`
- `AWS-Architecture-screenshot/workflow.png`

## Notes

- The site is primarily static, so content delivery performance is expected to be strong.
- Performance metrics are marked `TBD` where actual measurement data was not available from the repository.
