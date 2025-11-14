# Testing Guide

Comprehensive testing checklist for Terra Lumina website quality assurance.

## Pre-Deployment Checklist

### HTML Validation
- [ ] Run all HTML files through [W3C Validator](https://validator.w3.org/)
- [ ] Fix any errors or warnings
- [ ] Verify structured data with [Google Rich Results Test](https://search.google.com/test/rich-results)

### SEO Testing
- [ ] Verify all pages have unique titles
- [ ] Check meta descriptions are present and under 160 characters
- [ ] Confirm canonical URLs are set correctly
- [ ] Test Open Graph tags with [Facebook Sharing Debugger](https://developers.facebook.com/tools/debug/)
- [ ] Test Twitter Cards with [Twitter Card Validator](https://cards-dev.twitter.com/validator)
- [ ] Verify sitemap.xml is accessible and valid
- [ ] Check robots.txt is properly configured

### Accessibility (WCAG 2.1 AA)
- [ ] Run [WAVE](https://wave.webaim.org/) accessibility checker
- [ ] Test keyboard navigation (Tab, Enter, Escape)
- [ ] Verify color contrast ratios meet standards (4.5:1 minimum)
- [ ] Check all images have alt text
- [ ] Verify form labels are properly associated
- [ ] Test with screen reader (VoiceOver, NVDA, or JAWS)
- [ ] Ensure ARIA labels are used where appropriate

### Responsive Design
Test on multiple viewports:
- [ ] Mobile (320px - iPhone SE)
- [ ] Mobile (375px - iPhone 12/13)
- [ ] Mobile (414px - iPhone Plus)
- [ ] Tablet (768px - iPad)
- [ ] Tablet (1024px - iPad Pro)
- [ ] Desktop (1280px)
- [ ] Desktop (1920px)
- [ ] Ultrawide (2560px+)

### Cross-Browser Testing
Test on:
- [ ] Chrome (latest)
- [ ] Firefox (latest)
- [ ] Safari (latest)
- [ ] Edge (latest)
- [ ] Mobile Safari (iOS)
- [ ] Chrome Mobile (Android)

### Functional Testing

#### Navigation
- [ ] All internal links work correctly
- [ ] Footer links navigate properly
- [ ] Back to top/home links function
- [ ] Hash links scroll smoothly (#contact, etc.)

#### Forms
- [ ] Contact form submits successfully
- [ ] Data room request form works
- [ ] Required fields are enforced
- [ ] Email validation works
- [ ] Form error messages display correctly
- [ ] Success messages appear after submission
- [ ] No console errors on submission

#### Interactive Elements
- [ ] FAQ accordion toggles work
- [ ] ROI calculator computes correctly
- [ ] Range sliders update values
- [ ] Buttons have proper hover/active states
- [ ] WhatsApp float button links correctly

#### External Links
- [ ] Calendly links open correctly
- [ ] Formspree endpoint is configured
- [ ] GitHub repository link works
- [ ] Email links open mail client
- [ ] All external links open in new tabs (target="_blank")

### Performance Testing

#### Page Speed
Run [Google PageSpeed Insights](https://pagespeed.web.dev/) for:
- [ ] index.html
- [ ] transparency.html
- [ ] roi-calculator.html
- [ ] data-room.html

Target Scores:
- Performance: 90+
- Accessibility: 95+
- Best Practices: 95+
- SEO: 100

#### Load Time Metrics
- [ ] First Contentful Paint < 1.8s
- [ ] Largest Contentful Paint < 2.5s
- [ ] Cumulative Layout Shift < 0.1
- [ ] Time to Interactive < 3.8s

#### Optimization Checks
- [ ] Images are optimized (WebP where possible)
- [ ] CSS is minified (production)
- [ ] JavaScript is minified (production)
- [ ] No render-blocking resources
- [ ] Fonts are preloaded if needed

### Security Testing

#### HTTPS
- [ ] All pages load over HTTPS
- [ ] No mixed content warnings
- [ ] SSL certificate is valid
- [ ] HSTS header is set

#### Content Security
- [ ] No XSS vulnerabilities in forms
- [ ] Input validation works properly
- [ ] No sensitive data in client-side code
- [ ] API endpoints are secured (when implemented)

#### Privacy
- [ ] Privacy policy is accessible
- [ ] Cookie consent mechanism (if using cookies)
- [ ] No PII leakage in URLs or logs

### Content Quality

#### Spelling & Grammar
- [ ] Run spell check on all pages
- [ ] Verify numbers and statistics are accurate
- [ ] Check for consistent terminology
- [ ] Verify all dates are current (2025)

#### Consistency
- [ ] Brand name is consistent (Terra Lumina)
- [ ] Company stage is consistent (Pre-Seed)
- [ ] Funding amounts match ($750K-1.5M)
- [ ] Contact emails are consistent
- [ ] URLs are consistent throughout

#### Legal
- [ ] Privacy policy is complete
- [ ] Terms of service are in place
- [ ] Investment disclaimers are present
- [ ] Copyright year is current (2025)

### Asset Verification
- [ ] All referenced images exist
  - [ ] /assets/icon-192x192.png
  - [ ] /assets/icon-512x512.png
  - [ ] /assets/og-image.png
  - [ ] /assets/logo.png
- [ ] Favicon is present and displays correctly
- [ ] manifest.json validates

## Testing Tools

### Automated Testing
```bash
# HTML Validation (if using html-validate)
npx html-validate "*.html"

# Accessibility testing (if using pa11y)
npx pa11y https://terra.luminousdynamics.org

# Lighthouse CLI
npx lighthouse https://terra.luminousdynamics.org --view
```

### Manual Testing Checklist

#### Mobile Device Testing
1. Test on actual devices if possible:
   - [ ] iPhone (iOS Safari)
   - [ ] Android phone (Chrome)
   - [ ] iPad (Safari)

2. Touch interactions:
   - [ ] Tap targets are at least 44x44px
   - [ ] No hover-only interactions
   - [ ] Forms are easy to fill on mobile
   - [ ] Text is readable without zooming

#### User Flows

**Investor Journey**:
1. [ ] Land on homepage
2. [ ] Read value proposition
3. [ ] Check transparency report
4. [ ] Use ROI calculator
5. [ ] Submit contact form OR schedule call
6. [ ] Request data room access

**Information Seeker Journey**:
1. [ ] Find site via search
2. [ ] Read about platform
3. [ ] Check FAQ
4. [ ] Find contact information
5. [ ] Navigate to privacy/terms

## Post-Deployment Testing

### After Going Live
- [ ] Verify DNS propagation
- [ ] Test from different geographic locations
- [ ] Check Google Search Console for errors
- [ ] Monitor form submissions
- [ ] Check analytics are tracking (if implemented)
- [ ] Verify sitemap is indexed by search engines

### Weekly Monitoring
- [ ] Check for broken links (use [Dead Link Checker](https://www.deadlinkchecker.com/))
- [ ] Monitor page load times
- [ ] Review search console performance
- [ ] Check for security alerts

### Monthly Review
- [ ] Update transparency report
- [ ] Verify all content is current
- [ ] Check for outdated statistics
- [ ] Review and respond to form submissions
- [ ] Update sitemap lastmod dates

## Bug Reporting Template

When reporting bugs, include:

```markdown
**URL**: https://terra.luminousdynamics.org/[page]
**Browser**: Chrome 120.0.6099.109
**OS**: macOS 14.2
**Device**: MacBook Pro / iPhone 15 / etc.
**Viewport**: 1920x1080 / Mobile 375x667

**Steps to Reproduce**:
1. Navigate to...
2. Click on...
3. Observe...

**Expected Behavior**:
[What should happen]

**Actual Behavior**:
[What actually happens]

**Screenshots**:
[Attach if applicable]

**Console Errors**:
[Copy any console errors]
```

## Pre-Launch Final Checklist

48 hours before launch:
- [ ] All testing checkpoints above completed
- [ ] Stakeholder review completed
- [ ] Legal review of privacy/terms completed
- [ ] Contact form tested and working
- [ ] Backup plan documented
- [ ] Rollback procedure ready
- [ ] Monitoring in place

Launch day:
- [ ] DNS configured
- [ ] SSL certificate active
- [ ] All assets loading correctly
- [ ] Forms submitting to correct endpoints
- [ ] Analytics tracking (if used)
- [ ] Search console verified
- [ ] Social sharing preview looks correct

## Continuous Improvement

After launch, track:
- User feedback on contact forms
- Page bounce rates
- Time on site
- Conversion rates (contact form submissions)
- Mobile vs desktop usage
- Most visited pages

Use this data to:
- Optimize underperforming pages
- Improve user flows
- Enhance content based on user interests
- Fix usability issues

---

**Testing Owner**: Tech Lead
**Last Updated**: January 14, 2025
**Next Review**: February 14, 2025

For testing questions: tech@luminousdynamics.org
