# Assets Directory

This directory contains visual assets for the Terra Lumina website.

## Required Assets

The following assets are referenced throughout the site but need to be created:

### Icons (PWA/Mobile)

**icon-192x192.png**
- Size: 192x192 pixels
- Format: PNG with transparency
- Purpose: Android/Chrome app icon
- Referenced in: `manifest.json`

**icon-512x512.png**
- Size: 512x512 pixels
- Format: PNG with transparency
- Purpose: High-resolution app icon
- Referenced in: `manifest.json`

### Social Sharing

**og-image.png**
- Size: 1200x630 pixels (recommended)
- Format: PNG or JPG
- Purpose: Social media preview (Facebook, LinkedIn, Twitter)
- Referenced in: `index.html` (Open Graph meta tags)
- Content suggestion: Terra Lumina logo + tagline + key stat

### Branding

**logo.png**
- Size: Flexible (suggest 512x512 minimum)
- Format: PNG with transparency
- Purpose: Primary brand logo, JSON-LD schema
- Referenced in: `index.html` (structured data)

**favicon.ico**
- Size: 32x32, 16x16 (multi-size)
- Format: ICO
- Purpose: Browser tab icon
- Location: Root directory
- Not yet created or referenced

## Design Guidelines

### Color Palette

Primary colors (from CSS variables):
```css
--primary: #1a73e8     /* Blue */
--secondary: #00c853   /* Green */
--dark: #0f172a        /* Near black */
--light: #f8fafc       /* Off white */
--gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%)
```

Theme color: `#0066cc` (specified in manifest.json)

### Brand Elements

**Tagline**: "Democratizing Energy Investment"

**Key Visual Themes**:
- Clean energy (solar, wind, hydro)
- Community/democracy
- Technology/platform
- Transparency/trust
- Growth/abundance

**Typography**:
- Primary: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif
- Secondary: Inter (used in some pages)

## Asset Creation Tools

### Free Options

**Design Tools**:
- [Canva](https://canva.com) - Templates and easy design
- [Figma](https://figma.com) - Professional design tool
- [Photopea](https://photopea.com) - Free Photoshop alternative

**Icon Generation**:
- [RealFaviconGenerator](https://realfavicongenerator.net/) - Complete favicon package
- [PWA Asset Generator](https://www.pwabuilder.com/) - PWA icon sets
- [Favicon.io](https://favicon.io/) - Simple favicon creator

**Image Optimization**:
- [TinyPNG](https://tinypng.com/) - PNG compression
- [Squoosh](https://squoosh.app/) - Image optimizer
- [ImageOptim](https://imageoptim.com/) - Mac app

### AI-Powered Options

**Logo/Icon Design**:
- [Looka](https://looka.com) - AI logo generator
- [Brandmark](https://brandmark.io) - AI branding
- [Hatchful](https://hatchful.shopify.com/) - Free logo maker

**Image Generation**:
- [Midjourney](https://midjourney.com) - AI art (subscription)
- [DALL-E](https://openai.com/dall-e-2) - AI images
- [Stable Diffusion](https://stability.ai/) - Open source AI

## Quick Start

### Option 1: Professional Design

1. Hire designer on Fiverr/Upwork
2. Provide:
   - This README
   - Brand guidelines above
   - Website URL for context
3. Budget: $50-200 for full asset package

### Option 2: DIY with Canva

1. Create free Canva account
2. Use templates:
   - Logo: Search "tech logo" or "energy logo"
   - Icons: Search "app icon"
   - OG Image: Custom size 1200x630px
3. Export as PNG
4. Optimize with TinyPNG
5. Place files in this directory

### Option 3: Placeholder Assets

For development/testing only:

```bash
# Create simple colored squares as placeholders
convert -size 192x192 xc:#1a73e8 icon-192x192.png
convert -size 512x512 xc:#1a73e8 icon-512x512.png
convert -size 1200x630 xc:#667eea og-image.png
convert -size 512x512 xc:#1a73e8 logo.png
```

**Note**: Replace these with proper branding before launch!

## Asset Checklist

Before deployment, verify:
- [ ] All icons created and placed in `/assets/`
- [ ] OG image created with proper dimensions
- [ ] Logo file created
- [ ] Favicon generated and placed in root
- [ ] All assets optimized (compressed)
- [ ] Assets tested in manifest validator
- [ ] Social sharing tested (Facebook debugger)
- [ ] Icons appear correctly on mobile

## File Naming Convention

Use lowercase, hyphens for spaces:
- ✅ `og-image.png`
- ✅ `icon-192x192.png`
- ❌ `OG Image.png`
- ❌ `icon_192x192.png`

## Optimization Guidelines

### Icons
- PNG-8 if simple colors
- PNG-24 if gradients/transparency
- Compress with TinyPNG
- Target: < 50KB each

### OG Image
- JPG for photos, PNG for graphics
- Quality: 80-90%
- Compress to < 300KB
- Test preview on multiple platforms

### Logo
- PNG with transparency
- SVG preferred for scalability
- Keep original high-res version

## Testing Assets

After creation:

1. **Manifest Validation**
   - https://manifest-validator.appspot.com/

2. **Social Sharing**
   - Facebook: https://developers.facebook.com/tools/debug/
   - Twitter: https://cards-dev.twitter.com/validator
   - LinkedIn: https://www.linkedin.com/post-inspector/

3. **PWA**
   - Chrome DevTools → Application → Manifest
   - Verify icons display correctly

4. **Favicon**
   - Test in multiple browsers
   - Check both light/dark modes

## Future Assets

Consider creating:
- [ ] Hero background image
- [ ] Team member photos/avatars
- [ ] Project placeholder images
- [ ] Infographic assets
- [ ] Video thumbnails
- [ ] Email signature graphics

## Asset Delivery

When assets are ready:
1. Place files in this `/assets/` directory
2. Verify file names match references in HTML
3. Commit to git
4. Test on staging before production
5. Update this README if adding new assets

---

**Questions?** Contact: design@luminousdynamics.org

**Last Updated**: January 14, 2025
