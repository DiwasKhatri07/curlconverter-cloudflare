# Deploy to Cloudflare Workers

This project is now configured to be deployed as a Cloudflare Worker, which allows for more flexibility including custom subdomains and edge logic.

## 🚀 Deployment Steps

### 1. Login to Cloudflare
If you haven't already, login to wrangler:
```bash
pnpm wrangler login
```

### 2. Build and Deploy
Run the following command to build the frontend and deploy the worker:
```bash
pnpm run build
pnpm run deploy
```

### 3. Custom Subdomain Setup
Once deployed, you can add a custom subdomain:
1. Go to the [Cloudflare Dashboard](https://dash.cloudflare.com).
2. Navigate to **Workers & Pages**.
3. Select your `curlconverter` worker.
4. Go to the **Triggers** tab.
5. Under **Custom Domains**, click **Add Custom Domain**.
6. Enter your desired subdomain (e.g., `curl.diwas.pro`).

## 🔧 Configuration
The configuration is located in `wrangler.toml`. You can change the project name or compatibility date there.

```toml
name = "curlconverter"
main = "server/worker.ts"
compatibility_date = "2024-04-01"

[site]
bucket = "./dist/public"
```

## 📝 SPA Routing
The worker is configured to handle Single Page Application (SPA) routing. If a static asset is not found, it will automatically serve `index.html`, allowing React Router/Wouter to handle the routing on the client side.
