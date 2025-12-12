# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview

NextPlayPro Website is a static marketing website for a sports performance tracking application. The site is built with vanilla HTML5, CSS3, and JavaScript (ES6+) without any frameworks or build tools.

## Development Commands

### Starting the Development Server
```powershell
npm start
```
This runs `live-server` on port 8080. The site will be available at `http://localhost:8080`.

### Alternative Local Servers
If npm/live-server is unavailable:
- Python: `python -m http.server 8080`
- PHP: `php -S localhost:8080`

### Opening Directly
The site can be opened directly by opening `index.html` in a browser, though a local server is recommended for testing.

## Architecture

### Project Structure
The codebase follows a traditional static website structure:
- **index.html** - Single-page application containing all sections (home, features, about, contact)
- **css/styles.css** - All styling in one file using CSS3 features (Flexbox, Grid, CSS Variables)
- **js/main.js** - Client-side JavaScript for interactivity
- **images/** - Static image assets

### Key Design Patterns

**Single Page Application (SPA) Approach**
The site uses anchor-based navigation (`#home`, `#features`, etc.) with smooth scrolling implemented in JavaScript. All content is on one page divided into sections.

**Intersection Observer for Animations**
Feature cards use the Intersection Observer API for scroll-triggered animations. Cards are initialized with opacity: 0 and transform: translateY(20px), then animated when they enter the viewport.

**Sticky Navigation**
The header uses `position: sticky` with `z-index: 1000` to remain visible during scrolling.

### Styling Approach
- Mobile-first responsive design with breakpoint at 768px
- CSS Grid for the feature cards with `repeat(auto-fit, minmax(250px, 1fr))`
- Consistent color palette: primary (#667eea, #764ba2), accent (#00d9ff), dark (#1a1a2e)
- Smooth transitions on hover states for interactive elements

### JavaScript Functionality
1. **Smooth Scrolling** - Applied to all anchor links via event delegation
2. **Contact Form** - Prevents default submission, displays alert (no backend integration)
3. **CTA Button** - Scrolls to contact section when clicked
4. **Scroll Animations** - Uses IntersectionObserver to animate feature cards on viewport entry

## Development Practices

### Making Changes
- HTML structure changes go in `index.html`
- Style changes go in `css/styles.css`
- JavaScript functionality changes go in `js/main.js`
- Always test changes in a browser with the local server running

### Adding New Sections
When adding new sections to index.html:
1. Add the section with appropriate ID to the `<main>` element
2. Add corresponding navigation link to `.nav-links` in the header
3. Style the section in `css/styles.css`
4. Smooth scrolling will automatically work for new anchor links

### Adding Images
Place images in the `images/` directory and reference them with relative paths: `images/filename.ext`

### Browser Compatibility
The site uses modern web APIs (Intersection Observer, ES6+). Target browsers are latest versions of Chrome, Firefox, Safari, and Edge.

## Technologies
- **HTML5** with semantic markup
- **CSS3** with Flexbox, Grid, transitions, and gradients
- **JavaScript ES6+** with Intersection Observer API
- **No build process** - all code runs directly in the browser
- **No dependencies** - pure vanilla JavaScript (live-server is dev-only)
