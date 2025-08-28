# Terra Lumina Website Deployment Instructions

## Domain: terra.luminousdynamics.org

### Option 1: GitHub Pages (Recommended)
1. Create repo: github.com/Luminous-Dynamics/terra-lumina
2. Push website-deploy contents to gh-pages branch
3. Configure custom domain in repo settings
4. Add CNAME record: terra.luminousdynamics.org → luminous-dynamics.github.io

### Option 2: Netlify
1. Deploy from website-deploy directory
2. Add custom domain: terra.luminousdynamics.org
3. Enable automatic HTTPS

### Option 3: Vercel
1. Import project from website-deploy
2. Add domain: terra.luminousdynamics.org
3. Deploy

### DNS Configuration
Add these records at your DNS provider:
- A record: terra → 185.199.108.153 (GitHub Pages)
- CNAME: terra → luminous-dynamics.github.io (alternative)

### SSL Certificate
- GitHub Pages: Automatic with custom domain
- Netlify/Vercel: Automatic Let's Encrypt

### Post-Deployment
1. Test all links
2. Verify HTTPS works
3. Check mobile responsiveness
4. Submit to search engines
5. Set up analytics

## Support
For deployment help: tech@luminousdynamics.org
