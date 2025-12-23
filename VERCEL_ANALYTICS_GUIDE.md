# Vercel Web Analytics Integration Guide

This document provides a detailed guide for integrating Vercel Web Analytics into the Book Library project.

## Overview

Vercel Web Analytics is a privacy-first analytics platform that provides insights into your website's performance and user behavior. It requires no cookies and is GDPR compliant.

## What's Included

This project includes:

1. **Analytics Script Integration** - Vercel Web Analytics tracking script added to `index.html`
2. **Documentation** - Comprehensive guides for setup and deployment
3. **Package Configuration** - `package.json` configured for project management

## Quick Setup

### 1. Prerequisites

Before you begin, ensure you have:

- A Vercel account (sign up at https://vercel.com/signup if needed)
- A Vercel project created
- Git repository connected to Vercel

### 2. Enable Web Analytics on Vercel Dashboard

1. Visit https://vercel.com/dashboard
2. Select your project
3. Go to the **Analytics** tab
4. Click **Enable** to activate Web Analytics

The analytics feature will be available after your next deployment.

### 3. Deploy to Vercel

Using the Vercel CLI:

```bash
vercel deploy
```

Or connect your Git repository for automatic deployments.

### 4. View Analytics Data

Once deployed and receiving traffic:

1. Go to your Vercel dashboard
2. Select your project
3. Click the **Analytics** tab
4. View visitor metrics, page views, top pages, and geographic data

## Technical Details

### Analytics Script

The following scripts are added to `index.html` in the `<head>` section:

```html
<!-- Vercel Web Analytics -->
<script>
    window.va = window.va || function () { (window.vaq = window.vaq || []).push(arguments); };
</script>
<script defer src="/_vercel/insights/script.js"></script>
```

**How it works:**
- The first script initializes the `window.va` function for queueing analytics calls
- The second script loads the actual Vercel Web Analytics tracking script from `/_vercel/insights/script.js`
- The `defer` attribute ensures the script loads after page content

### Tracking Behavior

The analytics script automatically tracks:

- **Page Views**: Each unique page load
- **Session Duration**: How long users stay on your site
- **Device Information**: Browser, OS, device type
- **Geographic Location**: Country-level data (privacy-respecting)
- **Referrers**: Where visitors come from
- **Custom Events**: Via API (requires additional code)

## Privacy & Compliance

Vercel Web Analytics is designed with privacy first:

- **No Cookies**: Does not use cookies or local storage
- **No Personal Data**: Collects only aggregate, non-identifying information
- **GDPR Compliant**: Fully compliant with GDPR
- **CCPA Compatible**: Compatible with California Consumer Privacy Act
- **Transparent**: Users can opt-out without affecting site functionality

Learn more: https://vercel.com/docs/analytics/privacy-policy

## Customization & Advanced Features

### Custom Events

Users on Pro and Enterprise plans can track custom events such as:

- Button clicks
- Form submissions
- Downloads
- Video plays
- Custom business metrics

### Dashboard Features

Available analytics metrics include:

- **Overview**: Total page views, unique visitors, average session duration
- **Top Pages**: Most visited pages ranked by views
- **Referrers**: Traffic sources and referral channels
- **Device Types**: Desktop, tablet, mobile breakdown
- **Operating Systems**: Visitor OS distribution
- **Browsers**: Browser usage breakdown
- **Countries**: Geographic distribution of visitors

### Data Retention & Limits

Free tier limits:

- 30 days of data retention
- Unlimited page views
- Basic analytics features

Pro/Enterprise tiers:

- Extended data retention
- Custom events
- Advanced analytics
- Priority support

See pricing: https://vercel.com/pricing/analytics

## Troubleshooting

### Analytics Not Showing Data

**Check these items:**

1. **Deployment Verification**
   ```bash
   vercel status
   ```
   Ensure your site is deployed to Vercel

2. **Analytics Enabled**
   - Go to Vercel dashboard
   - Confirm Analytics is enabled for your project

3. **Network Tab Check**
   - Open browser DevTools (F12)
   - Go to Network tab
   - Refresh the page
   - Look for requests to `/_vercel/insights/view`

4. **Time Delay**
   - Wait 5-10 minutes for data to appear
   - Initial data may take up to an hour

5. **Script Verification**
   - Check that the analytics scripts are in `index.html`
   - Verify scripts are not blocked by browser extensions
   - Check browser console for JavaScript errors

### Common Issues & Solutions

**Issue: Script blocked by ad blocker**
- Solution: This is normal and expected. Analytics will still track most visits.

**Issue: No data appearing after 24 hours**
- Solution: Contact Vercel support. Ensure project is using latest deployment.

**Issue: Analytics tab not visible**
- Solution: Only Pro plan and above have analytics. Check your plan at https://vercel.com/dashboard/account/plan

## Useful Resources

- **Vercel Analytics Docs**: https://vercel.com/docs/analytics
- **Package Documentation**: https://vercel.com/docs/analytics/package
- **Custom Events**: https://vercel.com/docs/analytics/custom-events
- **Filtering Data**: https://vercel.com/docs/analytics/filtering
- **Pricing**: https://vercel.com/docs/analytics/limits-and-pricing
- **Troubleshooting**: https://vercel.com/docs/analytics/troubleshooting

## Next Steps

1. **Deploy your project**: `vercel deploy`
2. **Enable analytics** on the Vercel dashboard
3. **Wait for data**: Initial analytics appear after receiving traffic
4. **Explore dashboard**: Review metrics and optimize your site
5. **Consider custom events**: Track specific user interactions (Pro plan)

## Support

For issues or questions:

1. Check the troubleshooting guide above
2. Visit: https://vercel.com/docs/analytics/troubleshooting
3. Contact Vercel support: https://vercel.com/support
4. Check GitHub issues: https://github.com/vercel/analytics

---

**Last Updated**: December 2024
**Analytics Version**: @vercel/analytics@1.4.0+
**Compatibility**: All static sites, including HTML-only projects
