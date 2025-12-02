# Deployment Guide - Vercel

## Option 1: Deploy via GitHub (Recommended)

### Step 1: Create GitHub Repository

```bash
# In the devsurvey directory
cd /d/devsurvey

# Create a new GitHub repository (via GitHub CLI)
gh repo create devsurvey --public --source=. --remote=origin --push
```

Or manually:
1. Go to https://github.com/new
2. Repository name: `devsurvey`
3. Make it public or private (your choice)
4. **DO NOT** initialize with README (we already have one)
5. Click "Create repository"

Then push:
```bash
git remote add origin https://github.com/YOUR_USERNAME/devsurvey.git
git branch -M main
git push -u origin main
```

### Step 2: Deploy to Vercel

1. Go to https://vercel.com/new
2. Import your GitHub repository: `YOUR_USERNAME/devsurvey`
3. Configure project:
   - **Framework Preset**: Other
   - **Root Directory**: ./
   - **Build Command**: (leave empty)
   - **Output Directory**: (leave empty)
4. Click "Deploy"
5. Your survey will be live at: `https://devsurvey.vercel.app`

---

## Option 2: Deploy Directly with Vercel CLI

### Install Vercel CLI

```bash
npm install -g vercel
```

### Login to Vercel

```bash
vercel login
```

### Deploy

```bash
cd /d/devsurvey
vercel --prod
```

Follow the prompts:
- **Set up and deploy?** Y
- **Which scope?** (Select your account)
- **Link to existing project?** N
- **What's your project's name?** devsurvey
- **In which directory is your code located?** ./

Your survey will be deployed and you'll get a URL like: `https://devsurvey.vercel.app`

---

## Post-Deployment

### Update Edge Function URL in Frontend

After deployment, you need to update the Supabase Edge Function URL if your frontend needs to point to a production Edge Function.

**File: `index.html` (Line 989)**

Current:
```javascript
const EDGE_FUNCTION_URL = 'https://rosnhltrmvtlnekqbjos.supabase.co/functions/v1/wtp-survey-chat';
```

This is already pointing to your production Supabase Edge Function, so no changes needed!

### Custom Domain (Optional)

1. Go to Vercel Dashboard → Your Project → Settings → Domains
2. Add your custom domain (e.g., `survey.yourdomain.com`)
3. Follow DNS configuration instructions
4. Vercel automatically provisions SSL certificate

---

## Environment Variables (If Needed)

If you add any frontend environment variables:

1. Go to Vercel Dashboard → Your Project → Settings → Environment Variables
2. Add variables (e.g., `VITE_API_URL`)
3. Redeploy

**Note:** Currently no frontend environment variables are needed since the Edge Function URL is hardcoded.

---

## Automatic Deployments

Once connected to GitHub:
- **Every push to `main`** → Automatic production deployment
- **Pull requests** → Preview deployments with unique URLs
- **Rollbacks** → One-click rollback to previous versions

---

## Verify Deployment

After deploying, test these URLs:

1. **Main Survey**: `https://your-app.vercel.app/`
2. **Admin Dashboard**: `https://your-app.vercel.app/admin`

### Test Referral System

1. Complete a survey
2. Copy your referral link (should include `?ref=XXXXXXXX`)
3. Open in incognito: `https://your-app.vercel.app/?ref=XXXXXXXX`
4. Complete another survey
5. Check admin dashboard for referral count

---

## Troubleshooting

### Issue: 404 on /admin

**Solution:** Vercel.json routes should handle this. If not:
1. Check `vercel.json` exists in root
2. Redeploy: `vercel --prod --force`

### Issue: CORS errors

**Solution:** Edge Function already has CORS headers configured:
```typescript
'Access-Control-Allow-Origin': '*'
```

### Issue: Survey not loading

**Check:**
1. Browser console for errors
2. Edge Function is deployed and active
3. Supabase project is not paused
4. ANTHROPIC_API_KEY is set in Supabase secrets

---

## Monitoring

### Vercel Analytics

Enable Web Analytics:
1. Vercel Dashboard → Your Project → Analytics
2. Enable Web Analytics (free)
3. View traffic, performance, and Web Vitals

### Supabase Logs

Monitor Edge Function:
1. Supabase Dashboard → Edge Functions → wtp-survey-chat
2. View Logs tab for real-time requests
3. Check for errors

---

## Updating the Survey

### Make Changes Locally

```bash
cd /d/devsurvey
# Edit files (index.html, admin.html, etc.)
git add .
git commit -m "Update survey design"
git push origin main
```

Vercel automatically deploys on push to main.

### Quick Updates via Vercel CLI

```bash
cd /d/devsurvey
# Make changes
vercel --prod
```

---

## Performance

Current setup is optimized:
- ✅ Static HTML (instant load)
- ✅ Global CDN (Vercel Edge Network)
- ✅ Automatic HTTPS
- ✅ Brotli/Gzip compression
- ✅ HTTP/2 enabled

**Expected Performance:**
- Time to First Byte (TTFB): <100ms
- Largest Contentful Paint (LCP): <1s
- First Input Delay (FID): <10ms

---

## Cost

### Vercel
- **Hobby Plan**: Free
  - Unlimited deployments
  - 100 GB bandwidth/month
  - Automatic HTTPS
  - Perfect for this survey

### Supabase
- **Free Tier**: Currently used
  - 500 MB database
  - 2 GB storage
  - 50k monthly active users
  - Enough for 1000s of survey responses

**Total Cost: $0/month** (within free tier limits)

---

## Next Steps

1. Deploy to Vercel
2. Test the survey end-to-end
3. Share the URL!
4. Monitor responses in admin dashboard

---

**Repository**: `/d/devsurvey`
**Status**: ✅ Ready to deploy
