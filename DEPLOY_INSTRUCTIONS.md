# Deployment Instructions

Complete guide for deploying Terra Lumina to production.

## Prerequisites

Before deploying, ensure:
- [ ] All tests pass (see [TESTING.md](TESTING.md))
- [ ] Assets are created (see [assets/README.md](assets/README.md))
- [ ] Forms are configured with live endpoints
- [ ] Domain DNS is ready
- [ ] SSL certificate is configured

---

## Deployment Options

### Option 1: GitHub Pages (Recommended)

**Pros**: Free, automatic HTTPS, simple deployment
**Cons**: Static sites only, limited server-side features

#### Setup Steps

1. **Repository Settings**
   ```bash
   # Ensure you're on the main branch
   git checkout main
   git pull origin main
   ```

2. **Enable GitHub Pages**
   - Go to repository Settings → Pages
   - Source: Deploy from branch
   - Branch: `main` / `root`
   - Click "Save"

3. **Custom Domain Setup**
   - Add CNAME file to repository root:
     ```bash
     echo "terra.luminousdynamics.org" > CNAME
     git add CNAME
     git commit -m "Add custom domain"
     git push
     ```

4. **DNS Configuration**
   Add DNS records at your domain provider:
   ```
   Type: CNAME
   Name: terra
   Value: luminous-dynamics.github.io
   TTL: 3600
   ```

5. **SSL Certificate**
   - GitHub Pages automatically provisions SSL
   - May take 10-20 minutes after DNS propagation
   - Check "Enforce HTTPS" in repository settings

6. **Verify Deployment**
   - Visit https://terra.luminousdynamics.org
   - Check HTTPS is working
   - Verify all pages load correctly

---

### Option 2: Netlify

**Pros**: Continuous deployment, form handling, serverless functions
**Cons**: Costs for advanced features

#### Setup Steps

1. **Create Netlify Account**
   - Sign up at https://netlify.com
   - Connect GitHub account

2. **Import Repository**
   - Click "Add new site"
   - Choose "Import an existing project"
   - Select terra-lumina repository

3. **Build Settings**
   ```
   Build command: (leave empty - static site)
   Publish directory: /
   ```

4. **Deploy Site**
   - Click "Deploy site"
   - Wait for deployment to complete

5. **Custom Domain**
   - Go to Site settings → Domain management
   - Click "Add custom domain"
   - Enter: terra.luminousdynamics.org
   - Follow DNS configuration instructions

6. **Configure Forms**
   Netlify can handle forms natively:
   - Add `netlify` attribute to forms
   - Remove Formspree action
   - Example:
     ```html
     <form name="contact" method="POST" netlify>
     ```

7. **Environment Variables** (if needed)
   - Site settings → Environment variables
   - Add any API keys or secrets

---

### Option 3: Vercel

**Pros**: Excellent performance, edge network, analytics
**Cons**: Costs for team features

#### Setup Steps

1. **Install Vercel CLI**
   ```bash
   npm install -g vercel
   ```

2. **Login to Vercel**
   ```bash
   vercel login
   ```

3. **Deploy**
   ```bash
   cd /path/to/terra-lumina
   vercel --prod
   ```

4. **Custom Domain**
   ```bash
   vercel domains add terra.luminousdynamics.org
   ```

5. **Follow DNS Instructions**
   - Vercel will provide DNS records to add
   - Add them at your domain provider
   - Verify with: `vercel domains verify terra.luminousdynamics.org`

---

## Pre-Deployment Checklist

### Assets
- [ ] Icon files created (192x192, 512x512)
- [ ] OG image created for social sharing
- [ ] Logo file created
- [ ] Favicon generated

### Forms
- [ ] Formspree/Netlify forms configured
- [ ] Test form submissions work
- [ ] Email notifications configured
- [ ] Spam protection enabled

### Configuration
- [ ] Update Calendly links with real URLs
- [ ] Configure WhatsApp number (or remove)
- [ ] Update all placeholder content
- [ ] Set correct form action URLs

### Content
- [ ] Final spelling/grammar check
- [ ] Verify all numbers and stats
- [ ] Check copyright year (2025)
- [ ] Validate all links work

### Technical
- [ ] Run HTML validation
- [ ] Test on multiple browsers
- [ ] Check mobile responsiveness
- [ ] Verify HTTPS everywhere
- [ ] Test page load speed

---

## Post-Deployment Tasks

### Immediate (Day 1)

1. **Verify Deployment**
   - [ ] All pages load correctly
   - [ ] HTTPS is enforced
   - [ ] Forms submit successfully
   - [ ] No console errors
   - [ ] Mobile site works

2. **Submit to Search Engines**
   ```bash
   # Google Search Console
   https://search.google.com/search-console

   # Bing Webmaster Tools
   https://www.bing.com/webmasters
   ```

3. **Verify DNS Propagation**
   ```bash
   # Check DNS propagation
   dig terra.luminousdynamics.org

   # Or use online tool
   https://www.whatsmydns.net/
   ```

### Week 1

- [ ] Monitor form submissions
- [ ] Check analytics (if configured)
- [ ] Review Search Console for errors
- [ ] Test from different locations/networks
- [ ] Gather initial user feedback

### Month 1

- [ ] Review performance metrics
- [ ] Check for broken links
- [ ] Update sitemap if needed
- [ ] Monitor security alerts
- [ ] Plan first content update

---

## Form Configuration

### Formspree Setup

1. **Create Formspree Account**
   - Go to https://formspree.io
   - Sign up with email

2. **Create Forms**
   - Contact form: `contact@terra-lumina`
   - Data room: `data-room@terra-lumina`

3. **Update HTML**
   ```html
   <form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
   ```

4. **Configure Notifications**
   - Set email destination
   - Enable spam filtering
   - Set up auto-responder (optional)

### Netlify Forms (Alternative)

Simply add `netlify` attribute to forms:
```html
<form name="contact" method="POST" netlify>
  <input type="hidden" name="form-name" value="contact">
  <!-- rest of form -->
</form>
```

---

## SSL/HTTPS Setup

### GitHub Pages
- Automatic once DNS is configured
- Check "Enforce HTTPS" in settings

### Netlify/Vercel
- Automatic with custom domains
- Let's Encrypt certificates

### Manual SSL (if self-hosting)
```bash
# Using Certbot
sudo certbot --nginx -d terra.luminousdynamics.org
```

---

## Rollback Procedure

If deployment issues occur:

### GitHub Pages
```bash
# Revert to previous commit
git revert HEAD
git push origin main
```

### Netlify
- Go to Deploys tab
- Find previous successful deploy
- Click "Publish deploy"

### Vercel
```bash
# Rollback to previous deployment
vercel rollback
```

---

## Monitoring & Maintenance

### Regular Checks

**Daily** (first week):
- Form submissions working
- No error alerts

**Weekly**:
- Check Search Console
- Review analytics
- Monitor uptime

**Monthly**:
- Update transparency report
- Check for broken links
- Review performance
- Update dependencies

### Tools to Use

- **Uptime Monitoring**: UptimeRobot, Pingdom
- **Analytics**: Google Analytics, Plausible
- **Error Tracking**: Sentry (if using JS)
- **Performance**: Google PageSpeed Insights

---

## Common Issues & Solutions

### Issue: DNS not propagating
**Solution**: Wait 24-48 hours. Use CloudFlare for faster propagation.

### Issue: HTTPS not working
**Solution**:
1. Verify DNS is correct
2. Wait for certificate provisioning (10-20 min)
3. Clear browser cache
4. Check "Enforce HTTPS" setting

### Issue: Forms not submitting
**Solution**:
1. Check form action URL
2. Verify method="POST"
3. Test with browser dev tools
4. Check Formspree dashboard

### Issue: Assets not loading
**Solution**:
1. Check file paths (case-sensitive)
2. Verify files are committed to git
3. Clear CDN cache
4. Check browser console for 404s

### Issue: Mobile site broken
**Solution**:
1. Test viewport meta tag is present
2. Check media queries
3. Verify touch targets are sized correctly
4. Test on actual devices

---

## Security Checklist

Before going live:
- [ ] All forms have CSRF protection
- [ ] No API keys in client code
- [ ] HTTPS enforced everywhere
- [ ] Security headers configured
- [ ] Input validation on all forms
- [ ] Rate limiting on forms (if possible)
- [ ] Content Security Policy set

---

## Deployment Automation

### GitHub Actions (Future)

Create `.github/workflows/deploy.yml`:
```yaml
name: Deploy

on:
  push:
    branches: [ main ]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Validate HTML
        run: npx html-validate "*.html"
      - name: Deploy to GitHub Pages
        run: echo "Deployed!"
```

---

## Support

### Deployment Help
**Email**: tech@luminousdynamics.org

### Emergency Contact
If site is down and urgent:
**Email**: hello@luminousdynamics.org
**Subject**: [URGENT] Site Down - terra.luminousdynamics.org

---

## Deployment Checklist

Print and use for each deployment:

```
PRE-DEPLOYMENT
□ All tests passed
□ Assets created
□ Forms configured
□ Content reviewed
□ Performance tested

DEPLOYMENT
□ DNS configured
□ Site deployed
□ HTTPS enabled
□ Forms working
□ All pages accessible

POST-DEPLOYMENT
□ Search engines notified
□ Analytics configured
□ Monitoring enabled
□ Team notified
□ Documentation updated

Date: ______________
Deployed by: ______________
Deployment method: ______________
Issues encountered: ______________
```

---

**Last Updated**: January 14, 2025
**Next Review**: Before each major deployment
