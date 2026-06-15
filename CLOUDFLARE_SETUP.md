# Quick Start: Deploy to Cloudflare Pages

Get your Curl Converter live on diwas.pro in 5 minutes!

## 🚀 Quick Setup

### 1. Go to Cloudflare Dashboard
- Visit https://dash.cloudflare.com
- Go to **Pages** section

### 2. Create New Project
- Click **Create a project**
- Select **Connect to Git**
- Choose this repository: `DiwasKhatri07/curlconverter`

### 3. Configure Build
When prompted, use these settings:

```
Build command:        pnpm run build
Build output:         dist/public
Root directory:       /
```

### 4. Deploy
- Click **Save and Deploy**
- Wait 1-2 minutes for build to complete
- You'll get a `.pages.dev` URL

### 5. Connect Custom Domain
- Go to project settings → **Custom domains**
- Add `diwas.pro`
- DNS should auto-configure (if nameservers point to Cloudflare)

## ✅ Done!

Your app is now live at **diwas.pro** 🎉

## 📝 What's Included

- ✓ Automatic builds on every push to `main`
- ✓ Free SSL/TLS certificate
- ✓ Global CDN distribution
- ✓ Automatic minification & optimization
- ✓ Rollback to previous deployments anytime

## 🔧 Troubleshooting

**Build fails?** Make sure:
- Node.js 18+ is available
- `pnpm` is installed globally
- `dist/public` directory is the output

**Domain not working?** Check:
- DNS CNAME record points to `curlconverter.pages.dev`
- Wait 24 hours for DNS propagation
- Verify in Cloudflare DNS settings

## 📚 Full Documentation

See [DEPLOYMENT.md](./DEPLOYMENT.md) for complete deployment guide.

---

**Questions?** Open an issue on GitHub: https://github.com/DiwasKhatri07/curlconverter/issues
