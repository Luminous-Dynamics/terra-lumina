# Changelog

All notable changes to the Terra Lumina project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added (Phase 5: Business Documentation - January 14, 2025)
- **ONE-PAGER.md**: Executive one-pager for quick investor sharing
  - Complete investment opportunity summary on a single page
  - Key metrics, timeline, team, and contact information
  - Perfect for forwarding to potential investors

- **FAQ.md**: Comprehensive Q&A document
  - 8 major topic areas with detailed answers
  - Covers platform, investment, market, competition, financials, team, legal, and risks
  - Professional resource for investor due diligence

- **BRAND-GUIDELINES.md**: Complete brand and messaging guidelines
  - Brand essence (mission, vision, values, personality)
  - Visual identity (logo usage, colors, typography, imagery)
  - Voice & tone guidelines with do's and don'ts
  - Messaging framework with positioning and key messages
  - Channel-specific guidelines and templates

- **LAUNCH-CHECKLIST.md**: Comprehensive launch preparation checklist
  - Pre-launch phase (legal, team, funding, brand)
  - Platform development phase with testing requirements
  - Pre-launch marketing timeline (4-6 weeks before)
  - Launch week and launch day procedures
  - Post-launch monitoring (Week 1 and Month 1)
  - Risk mitigation strategies and success criteria

- **README.md enhancement**: Added comprehensive Documentation section
  - Organized resources for investors vs. team/contributors
  - Clear navigation to all key documents
  - Updated repository structure with all current files

### Added (Phase 4: Operational Excellence - January 14, 2025)
- **TESTING.md**: Comprehensive 300+ line QA guide
  - HTML validation, SEO testing, accessibility audits (WCAG 2.1 AA)
  - Cross-browser and responsive design testing procedures
  - Performance metrics and optimization guidelines
  - Security testing checklist
  - Pre-launch and post-launch monitoring procedures

- **ROADMAP.md**: Transparent product roadmap (Q1 2025 - 2030)
  - Quarterly milestones with success metrics
  - Feature prioritization framework (Must Have/Should Have/Nice to Have)
  - Path to Series A clearly defined
  - Community feedback mechanisms

- **assets/README.md**: Complete asset creation guide
  - Specifications for all required images (icons, OG image, logo)
  - Design guidelines and color palette documentation
  - Tool recommendations (free and paid options)
  - Optimization and testing procedures

- **.email-templates/investor-response-template.md**:
  - 7 professional email templates covering full investor journey
  - Initial contact, follow-ups, data room access, commitment
  - Monthly updates and passing on investments
  - Best practices and legal considerations

- **DEPLOY_INSTRUCTIONS.md enhancement**: Expanded from 39 to 456 lines
  - Three deployment options (GitHub Pages, Netlify, Vercel) with detailed steps
  - Pre/post-deployment checklists
  - Form configuration guides, SSL setup, rollback procedures
  - Monitoring schedules and common issues with solutions

### Added (Phase 3: Professional Polish)
- Comprehensive README.md with project overview, setup instructions, and documentation
- Privacy Policy (privacy.html) with GDPR and CCPA compliance
- Terms of Service (terms.html) with proper investment disclaimers
- SEO meta tags (Open Graph, Twitter Cards, keywords) to index.html
- Accessibility improvements (ARIA labels on interactive elements)
- changefreq attributes to sitemap.xml for better SEO crawling
- JSON-LD structured data to index.html for rich search results (Organization & WebSite schemas)
- .gitignore with industry-standard patterns
- 404.html custom error page with 10-second auto-redirect and popular pages list
- SECURITY.md responsible disclosure policy with safe harbor provisions
- Enhanced robots.txt with bot-specific rules and AI scraper blocking

### Changed
- **CRITICAL**: Fixed WhatsApp link from "Series D" to "Pre-Seed Investment" in index.html
- Completely rewrote transparency.html (212 lines) to align with Pre-Seed platform model
- Standardized all currency from EUR (€) to USD ($) across all pages
- Updated copyright year from 2024 to 2025 in all footers
- Updated sitemap.xml with all current pages and January 2025 dates
- Changed footer tagline to "Democratizing energy investment where consciousness and capital unite"
- **executive-summary.md**: Fixed "MVP already built" → "architecture designed", "Luminous Chimera" → "Sacred Reciprocity License"
- **pitch-deck-outline.md**: Complete rewrite (152 lines) - removed Iceland city concept, 100% platform model alignment
- **manifest.json**: Updated description, added PWA categories (finance, sustainability)

### Fixed
- Business model inconsistency: All documents now describe Pre-Seed platform model
- Currency formatting in roi-calculator.html JavaScript (formatCurrency function)
- Missing links: Created privacy.html and terms.html pages referenced in footer
- Outdated messaging throughout site to accurately reflect Pre-Seed stage
- All contact emails and URLs audited for consistency

### Removed
- index-enhanced.html (duplicate file with outdated Series D messaging)

## [0.1.0] - 2024-11-01

### Added
- Initial website launch
- Landing page (index.html)
- Transparency report (transparency.html)
- Data room access page (data-room.html)
- ROI calculator (roi-calculator.html)
- Executive summary (executive-summary.md)
- CONTRIBUTING.md guidelines
- Dual licensing (Sacred Reciprocity License v4.0 + MIT)
- Basic sitemap.xml and robots.txt
- PWA manifest.json

---

## Migration Notes

### Pre-Seed Platform Model (Current)
Terra Lumina is now positioned as a **Pre-Seed platform** seeking $750K-1.5M to build infrastructure connecting investors to renewable energy projects globally. The platform focuses on democratizing energy investment.

### Previous Concept (Deprecated)
Earlier versions described a $650M Series D fundraise for building geothermal cities in Iceland. This concept has been replaced with the platform model approach.

---

## Versioning Strategy

- **Major version (X.0.0)**: Significant platform milestones (MVP launch, Series A, etc.)
- **Minor version (0.X.0)**: New features, significant content updates
- **Patch version (0.0.X)**: Bug fixes, minor content updates, SEO improvements

---

*For questions about changes, contact: transparency@luminousdynamics.org*
