# Pinterest Clients Dashboard

Live at: https://janeswiss.github.io/clients-dashboard/

## Setup (one-time)

### 1. Create GitHub repo
- Go to github.com → New repository
- Name: `clients-dashboard`
- Set to **Public** (required for free GitHub Pages)
- Do NOT add a README (we already have the files)

### 2. Push these files
```
cd /Users/janeair/Documents/AI/clients-dashboard
git init
git add .
git commit -m "Initial clients dashboard"
git branch -M main
git remote add origin https://github.com/JaneSwiss/clients-dashboard.git
git push -u origin main
```

### 3. Enable GitHub Pages
- Go to the repo on GitHub → Settings → Pages
- Source: Deploy from branch → main → / (root)
- Save — dashboard will be live in ~1 minute

### 4. Create Cloudinary account (for file uploads in the form)
- Go to cloudinary.com → Sign up free
- In the dashboard: Settings → Upload → Add upload preset
  - Signing mode: **Unsigned**
  - Copy the preset name
- Copy your Cloud Name from the top of the dashboard
- In `onboarding.html`, replace:
  - `YOUR_CLOUD_NAME` with your actual cloud name
  - `YOUR_UPLOAD_PRESET` with your upload preset name

### 5. Generate GitHub token (for dashboard save + auto-sync)
- Go to github.com → Settings → Developer settings → Personal access tokens → Fine-grained tokens
- New token → name it "clients-dashboard"
- Repository access: Only select `clients-dashboard`
- Permissions: Contents → Read and Write
- Generate and copy the token

### 6. Add environment variables to Netlify
- Go to your Netlify site → Site configuration → Environment variables
- Add:
  - `GITHUB_TOKEN` = the token from step 5
  - `GITHUB_REPO` = `JaneSwiss/clients-dashboard`
  - `GITHUB_FILE` = `pinterest_clients.json`

### 7. Re-deploy Netlify site
Drag the entire LANDING folder (including the new `onboarding.html` and `netlify/functions/`) to Netlify to update the site.

### 8. Set dashboard access code
The default access code is `switzer2026`. To change it:
- Edit `pinterest_clients.json` → change the `auth_token` value
- Commit and push to GitHub

## Access
- Dashboard: https://janeswiss.github.io/clients-dashboard/
- Client form: https://pinterest.switzertemplates.com/onboarding

## How saving works
When you update client status, deliverables, or notes in the dashboard, it uses your GitHub token (saved in your browser only) to write changes back to `pinterest_clients.json`. The token is never uploaded anywhere.
