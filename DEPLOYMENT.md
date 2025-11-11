# Deployment Setup Guide

## Enable GitHub Actions

Since this is a forked repository, GitHub Actions are disabled by default for security reasons. To enable them:

1. Go to your repository on GitHub: `https://github.com/theresahuang/faleproxy`
2. Click on the **Actions** tab
3. Click the green button that says **"I understand my workflows, go ahead and enable them"**

Alternatively, visit directly: `https://github.com/theresahuang/faleproxy/actions`

## Configure Vercel Deployment

To enable automatic deployment to Vercel when tests pass, you need to set up Vercel tokens:

### 1. Get Your Vercel Token

1. Go to [Vercel Account Settings](https://vercel.com/account/tokens)
2. Click **Create Token**
3. Give it a name (e.g., "GitHub Actions")
4. Copy the token (you won't be able to see it again!)

### 2. Add Vercel Token to GitHub Secrets

1. Go to your repository settings: `https://github.com/theresahuang/faleproxy/settings/secrets/actions`
2. Click **New repository secret**
3. Name: `VERCEL_TOKEN`
4. Value: Paste your Vercel token
5. Click **Add secret**

### 3. Link Your Vercel Project

If you haven't already deployed to Vercel:

1. Install Vercel CLI: `npm install -g vercel`
2. Run `vercel` in your project directory
3. Follow the prompts to link to your Vercel project
4. This creates a `.vercel` directory (already in `.gitignore`)

## How the CI/CD Pipeline Works

1. **On Push/PR**: Tests run automatically on Node.js 18.x and 20.x
2. **Tests Pass**: If all tests pass AND you're on the main/master branch, deployment starts
3. **Tests Fail**: Deployment is skipped - your production site stays safe!
4. **Deployment**: The app is automatically deployed to your Vercel production URL

## Vercel Production URL

After successful deployment, your app will be available at:
- `https://faleproxy.vercel.app` (or your custom domain)
- Check your Vercel dashboard for the exact URL

## Troubleshooting

- **Actions not running?** Make sure you've enabled them in the Actions tab
- **Deployment failing?** Check that `VERCEL_TOKEN` is set correctly in GitHub secrets
- **Want to test locally?** Run `npm test` to run the test suite
