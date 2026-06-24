# Arafatullah Rifat — Personal Portfolio

A modern, professional single-page portfolio website built for a CSE student and web developer. Features a dark glassmorphism aesthetic, smooth GSAP scroll animations, interactive skill/service/project modals, and a fully functional contact form with free email delivery.

![Portfolio Preview](https://img.shields.io/badge/Status-Live-success) ![License](https://img.shields.io/badge/License-MIT-blue) ![Responsive](https://img.shields.io/badge/Responsive-Yes-brightgreen)

---

## Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Configuration](#configuration)
- [Contact Form Setup](#contact-form-setup)
- [Deployment](#deployment)
- [Customization Guide](#customization-guide)
- [Browser Support](#browser-support)
- [Performance](#performance)
- [Known Issues & Solutions](#known-issues--solutions)
- [License](#license)

---

## Features

### Core
- **Single-page application** — All content on one page with smooth scroll navigation
- **Fully responsive** — Optimized for mobile, tablet, and desktop viewports
- **Dark glassmorphism UI** — Modern frosted-glass card design with subtle gradients
- **GSAP scroll animations** — Elements animate in smoothly as they enter the viewport
- **Interactive modals** — Click any skill, service, or project to view detailed documentation

### Sections
| Section | Description |
|---------|-------------|
| **Hero** | Animated headline with a live "code editor" visual showing developer profile as a JS object |
| **About Me** | Profile photo with floating social links, bio text, and animated stats bar (8+ Projects, 10+ Technologies, 100% Passion) |
| **Skills** | 8 interactive skill cards — clicking opens a modal with detailed expertise description and key achievements |
| **Services** | 3 service cards (Web Design, Prototyping, Web Development) — each with a "View Documentation" modal |
| **Projects** | 6 featured projects (Ghorkhuji, Car Rental, Travel Management, E-commerce, Calculator App, Weather Control) with tech stack and feature documentation |
| **FAQ** | 6-item accordion with smooth expand/collapse animations |
| **Contact** | Split layout with contact info cards + functional email form |

### Contact Form
- Powered by **FormSubmit.co** — 100% free, no API key or backend required
- Sends submissions directly to `Aryanrifat1@gmail.com`
- Includes honeypot spam protection
- Real-time loading state and success/error feedback

### Social Links
All social icons use **official brand SVG logos** with branded hover colors:
- Facebook (`#1877F2`)
- LinkedIn (`#0A66C2`)
- Instagram (`#E4405F`)
- GitHub (`#333333`)
- WhatsApp (`#25D366`)
- Email (`#EA4335`)

---

## Tech Stack

| Technology | Purpose | CDN/Source |
|-----------|---------|-----------|
| **HTML5** | Structure | Native |
| **Tailwind CSS** | Utility-first styling | `cdn.tailwindcss.com` |
| **GSAP 3.12** | Scroll-triggered animations | `cdnjs.cloudflare.com` |
| **ScrollTrigger** | GSAP scroll plugin | `cdnjs.cloudflare.com` |
| **Lucide Icons** | SVG icon library | `unpkg.com/lucide` |
| **Google Fonts** | Typography (Inter + Syne) | `fonts.googleapis.com` |
| **FormSubmit.co** | Free email form backend | `formsubmit.co` |

> **No build step required.** The entire site is a single `index.html` file with inline CSS and JavaScript.

---

## Project Structure

```
portfolio/
├── index.html          # Complete portfolio (single file, ~900 lines)
├── profile.jpeg        # Profile photo (displayed in About section)
├── resume.pdf          # CV/Resume file (linked in Download CV button)
└── README.md           # This documentation file
```

---

## Getting Started

### Prerequisites
- A modern web browser (Chrome, Firefox, Safari, Edge)
- A local server (optional but recommended)

### Quick Start

1. **Clone or download** the project files
2. **Add your profile photo** — Place your photo as `profile.jpeg` in the project root
3. **Add your resume** — Place your CV as `resume.pdf` in the project root
4. **Open the site:**

```bash
# Option 1: Direct file open
open index.html

# Option 2: Local server (recommended)
python3 -m http.server 3000
# Then visit http://localhost:3000
```

---

## Configuration

### Personal Information

All personal data is stored directly in the HTML. Search and replace to update:

| What to Change | Search For | Location |
|---------------|-----------|----------|
| Name | `Arafatullah Rifat` | Hero, About, Footer |
| Email | `Aryanrifat1@gmail.com` | About, Contact, Form |
| Phone | `+880 1947-653255` | Contact section |
| WhatsApp | `8801947653255` | Contact section (no `+`) |
| Facebook URL | `facebook.com/share/17iGBRuHxW` | About, Contact |
| LinkedIn URL | `linkedin.com/jobs/...` | About, Contact |
| Instagram URL | `instagram.com/tawsif_tibro` | About, Contact |
| GitHub URL | `github.com/Rifat-009` | About, Contact |

### Adding/Removing Skills

Locate the `skillsData` array in the `<script>` section:

```javascript
const skillsData = [
    { 
        name: "HTML5 & CSS3", 
        icon: "file-code", 
        color: "text-accent", 
        details: "Your detailed description here...", 
        achievements: ["Achievement 1", "Achievement 2", "Achievement 3"] 
    },
    // Add more skills here...
];
```

### Adding/Removing Projects

Locate the `projectsData` array:

```javascript
const projectsData = [
    { 
        id: 1, 
        title: "Project Name", 
        category: "Category",
        description: "Project description...",
        tech: ["React", "Node.js"],
        features: ["Feature 1", "Feature 2"]
    },
    // Add more projects here...
];
```

### Adding/Removing Services

Locate the `servicesData` array:

```javascript
const servicesData = [
    { 
        title: "Service Name", 
        icon: "layout", 
        color: "text-accent",
        shortDesc: "Brief description for card...",
        details: "Full description for modal...",
        documentation: ["Item 1", "Item 2", "Item 3"]
    },
    // Add more services here...
];
```

---

## Contact Form Setup

The contact form uses **FormSubmit.co** — a free service that requires zero API keys and no backend code.

### How It Works

1. When a visitor submits the form, the data is sent via AJAX to `https://formsubmit.co/ajax/Aryanrifat1@gmail.com`
2. **First-time activation:** FormSubmit sends a one-time confirmation email to `Aryanrifat1@gmail.com`. You **must** click the activation link in that email.
3. After activation, all future form submissions arrive directly in your Gmail inbox instantly.

### Form Features

| Feature | Implementation |
|---------|---------------|
| Spam protection | Honeypot field (`_honey`) |
| Custom subject | `_subject` hidden field |
| Table-format emails | `_template: table` hidden field |
| No captcha | `_captcha: false` for cleaner UX |
| Loading state | Button shows spinner during submission |
| Success feedback | Green success message appears for 6 seconds |
| Error handling | Red error message with fallback instructions |

### Changing the Email Recipient

If you want to change the email address, find this line in the JavaScript:

```javascript
const response = await fetch('https://formsubmit.co/ajax/YOUR_NEW_EMAIL@gmail.com', {
```

Replace `YOUR_NEW_EMAIL@gmail.com` with your desired email. You will need to re-activate with the new email.

---

## Deployment

### GitHub Pages (Recommended)

1. Create a new GitHub repository (e.g., `Portfolio`)
2. Push all project files:

```bash
git init
git add .
git commit -m "Initial portfolio commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/Portfolio.git
git push -u origin main
```

3. Go to **Settings → Pages**
4. Set **Source** to `main` branch, `/ (root)` directory
5. Your site will be live at `https://YOUR_USERNAME.github.io/Portfolio/`

### Netlify

1. Drag and drop the project folder into [Netlify Drop](https://app.netlify.com/drop)
2. Or connect your GitHub repository for automatic deployments

### Vercel

1. Import your GitHub repository in [Vercel](https://vercel.com)
2. Vercel auto-detects the static site and deploys

### Important Notes for Deployment

- **Image filenames are case-sensitive** on Linux servers. Ensure your photo is named exactly `profile.jpeg` (all lowercase).
- **Email links** must use `mailto:Aryanrifat1@gmail.com` — avoid Cloudflare's email obfuscation which can break `mailto:` links. If using Cloudflare, disable "Email Address Obfuscation" in the Scrape Shield settings.
- **FormSubmit.co** works on any hosting platform since it's an external API.

---

## Customization Guide

### Color Scheme

The site uses CSS custom properties via Tailwind config. To change the accent color:

```javascript
// In the <script> tailwind.config section:
colors: {
    accent: '#6366f1',        // Change this to your preferred color
    accentHover: '#4f46e5',   // Change hover state
}
```

Also update these CSS values to match:

```css
.text-gradient {
    background: linear-gradient(135deg, #818cf8 0%, #c084fc 100%); /* Update gradient */
}

.nav-link::after {
    background: #818cf8; /* Update underline color */
}
```

### Typography

The site uses two Google Fonts:
- **Syne** (display/headings) — Bold, geometric, modern
- **Inter** (body text) — Clean, highly readable

To change fonts, update the Google Fonts `<link>` and the `fontFamily` config.

### Animations

All animations use GSAP. To adjust timing:

```javascript
// Hero entrance
gsap.from(".hero-content > *", { 
    duration: 1,      // Speed of animation
    y: 40,            // Starting offset
    stagger: 0.1,     // Delay between elements
    delay: 0.2        // Initial delay
});

// Scroll-triggered cards
gsap.utils.toArray(".glass-card").forEach((card, i) => {
    gsap.from(card, {
        scrollTrigger: { trigger: card, start: "top 90%" },
        y: 30, 
        delay: i * 0.05  // Stagger delay per card
    });
});
```

---

## Browser Support

| Browser | Support |
|---------|---------|
| Chrome | ✅ Full support |
| Firefox | ✅ Full support |
| Safari | ✅ Full support |
| Edge | ✅ Full support |
| Mobile Safari | ✅ Full support |
| Chrome Android | ✅ Full support |

> Requires JavaScript enabled. Uses `backdrop-filter` for glass effects (supported in all modern browsers).

---

## Performance

| Metric | Value |
|--------|-------|
| Total file size | ~45 KB (HTML only) |
| External resources | 5 CDN scripts + 2 font families |
| Render-blocking | None (all scripts use `defer` or are placed at end of body) |
| Images | 1 profile photo (optimize to <200 KB for best performance) |
| Lighthouse score | 90+ (depends on image optimization and hosting) |

### Optimization Tips
- Compress `profile.jpeg` to under 200 KB using [TinyPNG](https://tinypng.com)
- Add `loading="lazy"` to the profile image if you add more images later
- Consider self-hosting Tailwind CSS for production (the CDN version is ~300 KB)

---

## Known Issues & Solutions

### Issue: Profile image not showing
**Cause:** Filename mismatch (case-sensitive servers)  
**Fix:** Ensure the image file is named exactly `profile.jpeg` (lowercase)

### Issue: Email form not sending
**Cause:** FormSubmit not activated  
**Fix:** Submit the form once, then check your Gmail for the activation email from FormSubmit. Click the activation link.

### Issue: Email links showing `[email protected]`
**Cause:** Cloudflare email obfuscation  
**Fix:** In Cloudflare dashboard → Scrape Shield → Disable "Email Address Obfuscation" → Purge cache

### Issue: Social icons not rendering
**Cause:** Lucide CDN not loading  
**Fix:** The site now uses inline SVGs for social icons, so this should not occur. If Lucide icons elsewhere are missing, check your internet connection.

### Issue: Animations not playing
**Cause:** GSAP not loading from CDN  
**Fix:** Check browser console for network errors. The site degrades gracefully — all content remains accessible without animations.

---

## License

This project is open source and available under the [MIT License](https://opensource.org/licenses/MIT).

---

<div align="center">

**Designed & Built by [Arafatullah Rifat](https://github.com/Rifat-009)**

[Facebook](https://www.facebook.com/share/17iGBRuHxW/?mibextid=wwXIfr) · [LinkedIn](https://www.linkedin.com/jobs/?skipRedirect=true&lipi=urn%3Ali%3Apage%3Ap_mwlite_my_network%3B20%2FZbiTIQ4uul9IN0kpJGA%3D%3D) · [Instagram](https://www.instagram.com/tawsif_tibro?igsh=MTlsMGlpN3Z2ZmxyZQ%3D%3D&utm_source=qr) · [GitHub](https://github.com/Rifat-009)

</div>