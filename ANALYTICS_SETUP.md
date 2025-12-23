# Getting Started with Vercel Web Analytics

This guide will help you get started with using Vercel Web Analytics on the Book Library project, showing you how to enable it, add the package to your project, deploy your app to Vercel, and view your data in the dashboard.

## Prerequisites

- A Vercel account. If you don't have one, you can [sign up for free](https://vercel.com/signup).
- A Vercel project. If you don't have one, you can [create a new project](https://vercel.com/new).
- The Vercel CLI installed. If you don't have it, you can install it using the following command:

```bash
npm install -g vercel
```

Or use your preferred package manager:

```bash
# Using pnpm
pnpm install -g vercel

# Using yarn
yarn global add vercel

# Using bun
bun add -g vercel
```

## Enable Web Analytics in Vercel

1. Go to the [Vercel dashboard](https://vercel.com/dashboard)
2. Select your Project
3. Click the **Analytics** tab
4. Click **Enable** from the dialog

> **💡 Note:** Enabling Web Analytics will add new routes (scoped at `/_vercel/insights/*`) after your next deployment.

## Add `@vercel/analytics` to your project

For static HTML sites like this project, add the `@vercel/analytics` package:

```bash
npm install @vercel/analytics
```

Or use your preferred package manager:

```bash
# Using pnpm
pnpm install @vercel/analytics

# Using yarn
yarn add @vercel/analytics

# Using bun
bun add @vercel/analytics
```

## Add the tracking script to your site

For plain HTML sites, add the following script tags to your `index.html` file (or any `.html` files you want to track):

```html
<script>
  window.va = window.va || function () { (window.vaq = window.vaq || []).push(arguments); };
</script>
<script defer src="/_vercel/insights/script.js"></script>
```

**Place these scripts:**
- In the `<head>` section for early tracking
- Before the closing `</body>` tag for optimal performance

> **💡 Note:** When using the HTML implementation, there is no need to install the `@vercel/analytics` package separately. However, there is no route support. The tracking script will still work and collect visitor data.

## Deploy your app to Vercel

Deploy your app using the Vercel CLI:

```bash
vercel deploy
```

If you haven't already, we also recommend [connecting your project's Git repository](https://vercel.com/docs/git#deploying-a-git-repository), which will enable Vercel to deploy your latest commits to main without terminal commands.

Once your app is deployed, it will start tracking visitors and page views.

> **💡 Note:** If everything is set up properly, you should be able to see a Fetch/XHR request in your browser's Network tab from `/_vercel/insights/view` when you visit any page.

## View your data in the dashboard

Once your app is deployed and users have visited your site:

1. Go to your [dashboard](https://vercel.com/dashboard)
2. Select your project
3. Click the **Analytics** tab

After a few days of visitors, you'll be able to start exploring your data by viewing and filtering the panels.

Users on Pro and Enterprise plans can also add custom events to their data to track user interactions such as:
- Button clicks
- Form submissions
- Page views
- Custom events

## Key Metrics Tracked

Vercel Web Analytics automatically tracks:

- **Page Views**: Number of times each page was viewed
- **Visitors**: Number of unique visitors to your site
- **Top Pages**: Most visited pages on your site
- **Referrers**: Where your visitors are coming from
- **Device Types**: Desktop, tablet, or mobile
- **Countries**: Geographic location of visitors (privacy-respecting)
- **Operating Systems**: Which OS visitors are using
- **Browsers**: Which browsers visitors are using

## Privacy and Compliance

Vercel Web Analytics is designed with privacy in mind:

- No cookies required
- GDPR compliant
- No personal data collection
- Visitor data is anonymized

For more information, see the [privacy and compliance documentation](https://vercel.com/docs/analytics/privacy-policy).

## Next Steps

Now that you have Vercel Web Analytics set up, you can:

- Learn how to use the [@vercel/analytics package](https://vercel.com/docs/analytics/package)
- Set up [custom events](https://vercel.com/docs/analytics/custom-events)
- Learn about [filtering data](https://vercel.com/docs/analytics/filtering)
- Explore [pricing and limits](https://vercel.com/docs/analytics/limits-and-pricing)
- Troubleshoot common issues in the [troubleshooting guide](https://vercel.com/docs/analytics/troubleshooting)

## Troubleshooting

If you're not seeing analytics data:

1. Make sure the scripts are added to your HTML files
2. Verify that you've deployed the changes to Vercel
3. Check your browser's Network tab to see if the tracking request is being made
4. Wait a few minutes for data to appear in the dashboard
5. Make sure your Vercel project is in the correct region
6. Check the browser console for any JavaScript errors

For more help, see the [Vercel Analytics troubleshooting guide](https://vercel.com/docs/analytics/troubleshooting).
