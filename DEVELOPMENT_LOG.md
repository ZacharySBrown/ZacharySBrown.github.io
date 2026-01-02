# Development Log - Portfolio Website Modernization

## Project Overview
Transformation of GitHub Pages portfolio from multi-page academic theme to modern single-page portfolio with clean design and consistent styling.

**Live Site:** https://zacharysbrown.github.io
**Repository:** https://github.com/ZacharySBrown/ZacharySBrown.github.io
**Framework:** Jekyll + Academic Pages Theme
**Date:** January 1, 2026

---

## Phase 1: Initial Content Update (Commits: 20b7390, 02e0c11)

### Objective
Update portfolio with recent work experience from Thomson Reuters, Kensho, and Balto.ai

### Changes Made

**1. Updated Employment History** (`_pages/cv.md`)
- Added Thomson Reuters Labs - Senior Manager, Applied Research (Oct 2024 - Present)
- Added Kensho - NLP ML Lead (Dec 2022 - Sept 2024)
- Added Balto.ai - Speech & Language Team Lead (Aug 2021 - Dec 2022)
- Updated Capital One dates (Jan 2020 - Aug 2021, was incorrectly showing "Present")
- Total: 10 positions from Feb 2014 to Present

**2. Updated Homepage Bio** (`_pages/about.md`)
- Changed from "data scientist" to "data scientist and applied research leader"
- Added current role at Thomson Reuters Labs
- Updated focus areas: generative AI, agentic workflows, evaluation frameworks
- Added Recent Highlights section featuring:
  - Westlaw Advantage Deep Research (first agentic legal research system)
  - S&P's first generative AI solution (ChatIQ)
- Updated reading list with current papers (2023-2024)

**3. Updated Technical Skills** (`_pages/cv.md`)
- Added Generative AI & LLMs category (openai, anthropic, langchain, peft)
- Updated MLOps tools (k8s, seldon core, mlflow)
- Added vector storage (chroma)

**4. Enabled Portfolio Section**
- Uncommented navigation in `_data/navigation.yml`
- Created 3 portfolio items:
  - `_portfolio/westlaw-deep-research.md`
  - `_portfolio/sp-genai-solution.md`
  - `_portfolio/realtime-nlp-balto.md`
- Deleted placeholder files

**5. Enabled Talks Section**
- Uncommented navigation in `_data/navigation.yml`
- Created 4 talk/community items:
  - `_talks/rvatech-ai-summit-2024.md`
  - `_talks/rva-data-science-meetup.md`
  - `_talks/pydata-virginia-committee.md`
  - `_talks/vcu-teaching.md`
- Deleted placeholder files from 2012-2014

**6. Updated Community Section** (`_pages/cv.md`)
- Added PyData Virginia Organizing Committee (2025)
- Added RVATech AI Summit (2024 - Present, note: rebranded from Data Summit)
- Clarified RVATech Data Summit dates (2018 - 2023)
- Added VCU teaching dates (2019 - 2021)

**7. Updated Config** (`_config.yml`)
- Updated sidebar bio to "Applied Research Leader | Generative AI | Former Physicist"
- Added employer: Thomson Reuters Labs

### Date Verification
All dates cross-checked against resume (`/Users/zak/prof/docs/resume_zsb_latest.pdf`):
- ✓ Thomson Reuters: Oct 2024 - Present
- ✓ Kensho: Dec 2022 - Sept 2024
- ✓ Balto.ai: Aug 2021 - Dec 2022
- ✓ Capital One: Jan 2020 - Aug 2021
- ✓ All other positions verified

---

## Phase 2: Single-Page Simplification (Commit: 02e0c11)

### Objective
Simplify multi-page site to single-page portfolio with all content on homepage

### Changes Made

**1. Converted to Single-Page Layout**
- Consolidated all content into `_pages/about.md`
- Removed separate CV, Portfolio, and Talks pages
- Structure: About → Employment → Projects → Community → Education → Skills

**2. Removed Navigation**
- Disabled main navigation in `_data/navigation.yml`
- Deleted unused page files:
  - `_pages/cv.md`
  - `_pages/portfolio.html`
  - `_pages/talks.html`
- Removed portfolio and talks directories

**3. Organized Projects Section**
Created two categories per user requirements:

**Impactful 0-1 ML/AI Projects:**
- Westlaw Advantage Deep Research (2024)
- ChatIQ - S&P's first GenAI (2023-2024)
- Capital One Eno Modernization (2020-2021)

**ML Modernization Efforts:**
- Balto ML Backend Overhaul (2021-2022)
- S&P Content Enrichment Optimization (2017-2019)

**4. Date Corrections**
- PyData Virginia: Changed to 2025 (was Fall 2024 - Spring 2025)
- RVATech: Clarified it's one event rebranded (Data Summit 2018-2023 → AI Summit 2024+)

### Rationale
- Simpler navigation (everything on one page)
- Easier to maintain (single file vs multiple)
- Better for scanning entire portfolio
- Faster load time
- Mobile-friendly scrolling

---

## Phase 3: Section Navigation (Commit: d7fdeea)

### Objective
Add navbar with anchor links to sections while keeping single-page layout

### Changes Made

**1. Added Section Anchor IDs** (`_pages/about.md`)
- `#employment` - Employment History
- `#projects` - Projects
- `#community` - Community & Extracurricular
- `#education` - Education
- `#skills` - Technical Skills

**2. Updated Navigation** (`_data/navigation.yml`)
```yaml
main:
  - title: "Employment"
    url: /#employment
  - title: "Projects"
    url: /#projects
  - title: "Community"
    url: /#community
  - title: "Education"
    url: /#education
  - title: "Skills"
    url: /#skills
```

**3. Updated Profile Photo**
- Copied new headshot from `docs/headshot.jpeg` to `images/headshot.jpeg`
- Updated `_config.yml` to use new photo
- Fixed avatar styling to be perfectly circular:
  - Set explicit width: 175px and height: 175px
  - Added `object-fit: cover` for proper cropping
  - Maintained `border-radius: 50%`

**File Modified:** `_sass/_sidebar.scss`
```scss
img {
  max-width: 175px;
  width: 175px;
  height: 175px;
  border-radius: 50%;
  object-fit: cover;
  // ...
}
```

### Result
- Top navigation bar with section links
- Smooth scroll to each section
- Single-page with easy navigation
- Circular profile photo displays correctly

---

## Phase 4: Modern Design System (Commit: 4e2edd7)

### Objective
Add modern visual design with timeline, cards, and interactive components

### Changes Made

**1. Updated Color System** (`_sass/_variables.scss`)
- Modern blue: #2563EB (primary)
- Purple accent: #7C3AED (secondary)
- Improved grays for better contrast
- Increased base font size: 16px → 17px
- Better type scale for hierarchy

**2. Created Comprehensive Component System** (`_sass/_modern-portfolio.scss`)
- Timeline component with gradient line
- Date badges with calendar icons
- Company badges with gradients
- Project cards with hover effects
- Skill pills with gradient primary badges
- Community cards
- Education cards
- Tech tags
- Section dividers

**3. Restructured Content** (`_pages/about.md`)
- Converted markdown to HTML with component classes
- Employment: Timeline with markers and cards
- Projects: Grid cards with tech tags
- Community: Grid cards
- Education: Cards with left border accent
- Skills: Categorized pills with primary/secondary styling

### Features Implemented
- Interactive timeline with circular markers
- Pulse animation on current position
- Hover effects (lift + shadow) on cards
- Gradient backgrounds on badges
- Consistent date styling with icons
- Smooth scroll behavior
- Mobile-responsive layouts
- Visual section dividers

### Technical Details
- 600+ lines of custom SCSS
- Grid layouts with `repeat(auto-fit, minmax())`
- CSS animations (pulse, hover transitions)
- Glassmorphism effects
- Flexbox for skills and dates
- Media queries for mobile

### Result
Beautiful modern design but **broke markdown formatting** in projects section.

---

## Phase 5: Simplified Clean Design (Commit: 35c4e88) ⭐ CURRENT

### Objective
Rebuild with simple, clean approach focusing on bold typography and consistency

### Problem Solved
Previous complex HTML/CSS broke markdown rendering and was overly complicated.

### Solution: Back to Basics

**1. Pure Markdown Content** (`_pages/about.md`)
- No complex HTML divs or components
- Standard markdown headers, lists, bold, italic
- Clean, readable structure
- Consistent formatting throughout

**2. Minimal CSS** (`_sass/_modern-portfolio.scss` - simplified to 94 lines)
```scss
// Focus areas:
- Smooth scroll behavior
- Bold, large section headers with blue underline
- Bold dates styled in blue color
- Better spacing and line height
- Gradient HR dividers
- Anchor link offset for navigation
```

**3. Consistent Date Formatting**
All dates bold and styled in primary blue throughout:
- Employment: **October 2024 — Present**
- Projects: **2024**, **2023-2024**
- Community: **2018 — Present**, **2017 — 2021**
- Education: **January 2015**

**4. Typography Hierarchy**
```
H2 (Sections): 2em, bold, blue underline
H3 (Subsections): 1.6em, bold
H4 (Items): 1.3em, semibold
Bold text (dates): Blue color, stands out
Italic text (tech): Gray, metadata
```

**5. Visual Elements**
- Section dividers: Gradient horizontal lines
- Blue underline on section headers
- Consistent spacing (3rem between sections)
- Better line height (1.6) for readability

### Key Design Decisions

**✓ Simplicity Over Complexity**
- Markdown > HTML components
- Simple CSS > complex frameworks
- Readability > fancy effects

**✓ Bold Elements**
- All dates bold and blue
- Job titles and project names bold
- Section headers extra bold

**✓ Consistent Styling**
- Same date format throughout
- Same spacing patterns
- Same color usage

**✓ Mobile-First**
- Markdown naturally responsive
- No complex grids to break
- Works on all screen sizes

### File Changes Summary
```
_pages/about.md: 166 lines (clean markdown)
_sass/_modern-portfolio.scss: 94 lines (simple CSS)
_sass/_variables.scss: Updated colors & typography
```

### Result
**Clean, professional portfolio that:**
- Loads fast
- Works everywhere
- Easy to maintain
- Looks great
- Won't break

---

## Final Architecture

### File Structure
```
ZacharySBrown.github.io/
├── _config.yml                 # Site config, author info
├── _data/
│   └── navigation.yml          # Section anchor links
├── _pages/
│   └── about.md                # SINGLE PAGE - ALL CONTENT
├── _sass/
│   ├── _variables.scss         # Modern colors & typography
│   └── _modern-portfolio.scss  # Simple, clean styles
├── assets/css/main.scss        # Imports all SCSS
└── images/
    └── headshot.jpeg           # Profile photo
```

### Content Sections
1. **About** - Intro paragraph
2. **Employment History** - 10 positions (2014-Present)
3. **Projects** - 5 major projects in 2 categories
4. **Community & Extracurricular** - 6 activities
5. **Education** - 3 degrees
6. **Technical Skills** - 5 categories

### Technology Stack
- **Framework:** Jekyll 3.9+
- **Theme:** Academic Pages (modified)
- **Hosting:** GitHub Pages
- **CSS:** SASS/SCSS
- **Deployment:** Automatic on push to master

---

## Lessons Learned

### What Worked
1. **Start simple** - Phase 5's simple approach was best
2. **Verify dates** - Always check against source documents
3. **User feedback** - "This broke formatting" led to better solution
4. **Markdown-first** - More maintainable than HTML

### What Didn't Work
1. **Complex components** - Timeline/cards broke markdown
2. **Too much CSS** - 600+ lines was overkill
3. **HTML in markdown** - Harder to maintain, easier to break

### Best Practices Established
1. Keep content in clean markdown
2. Use CSS for styling, not HTML structure
3. Bold dates consistently throughout
4. Test locally before pushing (when possible)
5. Simple is better than fancy

---

## Maintenance Guide

### Updating Content

**Add New Position:**
```markdown
### Job Title | Company Name
**Start Date — End Date**

* Bullet point
* Bullet point
```

**Add New Project:**
```markdown
**Project Name** | Company | **Year**

Description paragraph.

_Technologies: Tool1, Tool2, Tool3_
```

**Add Community Activity:**
```markdown
**Activity Name** | Organization | **Dates**

Description paragraph.
```

### Updating Styles

All styling in `_sass/_modern-portfolio.scss`:
- Section header underlines
- Date colors
- Spacing values
- HR dividers

Colors defined in `_sass/_variables.scss`:
- `$primary-color`: #2563EB (blue)
- `$secondary-color`: #7C3AED (purple)
- `$darker-gray`: #1F2937 (text)

### Testing Changes

**Local testing** (if Ruby/Jekyll installed):
```bash
cd /Users/zak/prof/ZacharySBrown.github.io
bundle install
bundle exec jekyll serve --livereload
# Visit http://localhost:4000
```

**Deploy:**
```bash
git add .
git commit -m "Description of changes"
git push origin master
# Site rebuilds automatically in 2-3 minutes
```

---

## Future Enhancements (Optional)

### Could Add Without Breaking Current Design
1. **Dark mode** - Prefers-color-scheme media query
2. **Print stylesheet** - Optimized CV print layout
3. **Open Graph tags** - Better social media sharing
4. **Animations** - Subtle fade-in on scroll
5. **Blog section** - If needed for thought leadership

### Should NOT Add
1. Complex JavaScript frameworks
2. Heavy component libraries
3. Complex HTML in markdown
4. Elaborate visual effects
5. Anything that makes it harder to maintain

---

## Git History Summary

```
35c4e88 - Rebuild with simplified, clean design (CURRENT)
4e2edd7 - Complete modern portfolio redesign (complex, broke formatting)
d7fdeea - Add section navigation and update profile photo
02e0c11 - Simplify to single-page portfolio
20b7390 - Update portfolio with recent work (initial content update)
```

---

## Credits

- **Theme:** Academic Pages (Jekyll theme)
- **Design:** Custom modern design system
- **Content:** Zachary S. Brown
- **Development:** Claude Code (Anthropic)
- **Date:** January 1, 2026

---

## Contact & Links

- **Website:** https://zacharysbrown.github.io
- **Email:** zachary.s.brown@gmail.com
- **Location:** Richmond, VA
- **Current Role:** Senior Manager, Applied Research @ Thomson Reuters Labs
