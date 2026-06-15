# Deployment Guide - Cloudflare Pages

This guide explains how to deploy the Curl Converter to Cloudflare Pages and connect it to your custom domain (diwas.pro).

## Prerequisites

- GitHub account with the repository pushed
- Cloudflare account with your domain (diwas.pro) added
- Domain nameservers pointing to Cloudflare

## Step-by-Step Deployment

### 1. Connect GitHub to Cloudflare Pages

1. Log in to your **Cloudflare Dashboard**
2. Go to **Pages** → **Create a project**
3. Select **Connect to Git**
4. Authorize Cloudflare to access your GitHub account
5. Select the repository: `DiwasKhatri07/curlconverter`
6. Click **Begin setup**

### 2. Configure Build Settings

On the "Set up builds and deployments" page, configure:

| Setting | Value |
|---------|-------|
| **Framework preset** | None (custom) |
| **Build command** | `pnpm run build` |
| **Build output directory** | `dist/public` |
| **Root directory** | `/` |

### 3. Environment Variables (Optional)

No environment variables are required for this static frontend application. All conversion happens in the browser.

### 4. Deploy

1. Click **Save and Deploy**
2. Cloudflare will build and deploy your site
3. You'll get a temporary URL like `curlconverter.pages.dev`
4. Wait for the deployment to complete (usually 1-2 minutes)

### 5. Connect Custom Domain

1. After deployment, go to your project settings
2. Click **Custom domains**
3. Click **Set up a custom domain**
4. Enter your domain: `diwas.pro`
5. Follow the DNS configuration steps (usually already configured if nameservers are pointing to Cloudflare)
6. Verify the domain connection

### 6. SSL/TLS Configuration

Cloudflare automatically provides free SSL certificates. To ensure HTTPS is enforced:

1. Go to **SSL/TLS** settings in Cloudflare Dashboard
2. Set **SSL/TLS encryption mode** to **Full** or **Full (strict)**
3. Enable **Always Use HTTPS**

## Automatic Deployments

After initial setup, every push to the `main` branch will automatically trigger a new deployment:

1. Push code to GitHub: `git push origin main`
2. Cloudflare automatically detects the change
3. Build starts automatically
4. New version is live within 1-2 minutes

## Monitoring Deployments

### View Deployment Status

1. Go to **Cloudflare Pages** → **Curl Converter** project
2. Click **Deployments** tab
3. See all deployment history with status (success/failed)

### View Build Logs

1. Click on any deployment
2. Click **View build log**
3. See detailed build output and any errors

## Troubleshooting

### Build Fails with "Command not found: pnpm"

**Solution:** Cloudflare might not have pnpm installed. Update build command:

```
npm install -g pnpm && pnpm run build
```

### Site Shows 404 on Routes

**Solution:** The `_redirects` file in `client/public/` handles client-side routing. Ensure it exists with content:

```
/* /index.html 200
```

### Custom Domain Not Working

**Solution:** Check DNS settings:

1. Go to **Cloudflare Dashboard** → **DNS**
2. Verify CNAME record points to `curlconverter.pages.dev`
3. Wait up to 24 hours for DNS propagation

### Slow Build Times

**Solution:** Cloudflare caches dependencies. First build is slower. Subsequent builds are faster.

## Local Testing Before Deployment

Test the production build locally:

```bash
pnpm run build
pnpm run preview
```

Then visit `http://localhost:4173` to verify everything works.

## Rollback to Previous Deployment

1. Go to **Deployments** tab
2. Find the previous working deployment
3. Click the three dots (⋯)
4. Select **Rollback to this deployment**

## Performance Optimization

Cloudflare automatically optimizes your site:

- **Minification**: Automatically minifies CSS, JavaScript, HTML
- **Image Optimization**: Compresses images automatically
- **Caching**: Static assets cached globally
- **CDN**: Served from Cloudflare's global CDN

## Custom Redirects and Rules

To add custom redirects or security rules:

1. Go to **Rules** → **Page Rules** in Cloudflare Dashboard
2. Add rules as needed (e.g., redirect www to non-www)

## Support

For issues with Cloudflare Pages:

- **Cloudflare Docs**: https://developers.cloudflare.com/pages/
- **Community**: https://community.cloudflare.com/
- **Support**: Contact Cloudflare support

For issues with the Curl Converter app:

- **GitHub Issues**: https://github.com/DiwasKhatri07/curlconverter/issues
- **Author**: [@diwazz](https://github.com/DiwasKhatri07)

---

**Happy deploying! 🚀**
