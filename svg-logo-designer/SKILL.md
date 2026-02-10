---
name: "SVG Logo Designer"
description: "Create professional SVG logos from descriptions and design specifications. Generates multiple logo variations with different layouts, styles, and concepts. Produces scalable vector graphics that can be used directly or exported to PNG. Use this skill when users ask to create logos, brand identities, icons, or visual marks for their designs."
---

# SVG Logo Designer

This skill creates professional, scalable vector graphic (SVG) logos from design specifications, offering multiple variations and layout options.

## When to Use This Skill

Activate this skill when the user requests:
- Create a logo from a description or specification
- Design a brand identity or visual mark
- Generate logo variations and concepts
- Create icons or symbols
- Design wordmarks or lettermarks
- Produce scalable graphics for branding
- Export logos in different layouts and styles

## Core Workflow

### Phase 1: Requirements Gathering

When a user requests a logo, gather comprehensive design requirements:

1. **Brand Information**
   - Company/product name
   - Industry and market
   - Target audience
   - Brand personality (modern, classic, playful, serious, etc.)
   - Brand values and messaging
   - Competitors (for differentiation)

2. **Design Preferences**
   - Logo type:
     - **Wordmark**: Text-based logo (Google, Coca-Cola style)
     - **Lettermark**: Initials/abbreviation (IBM, HBO style)
     - **Pictorial Mark**: Icon/symbol (Apple, Twitter style)
     - **Abstract Mark**: Abstract geometric form (Pepsi, Adidas style)
     - **Mascot**: Character-based (KFC Colonel, Michelin Man style)
     - **Combination Mark**: Icon + text (Burger King, Lacoste style)
     - **Emblem**: Text inside symbol (Starbucks, Harley-Davidson style)

3. **Style Guidelines**
   - Color palette (specific colors or let AI choose)
   - Color psychology considerations
   - Font preferences (if text-based)
   - Visual style:
     - Minimalist
     - Geometric
     - Organic/flowing
     - Bold/strong
     - Elegant/refined
     - Playful/friendly
     - Tech/modern
     - Vintage/retro

4. **Technical Requirements**
   - Size constraints (will it be used small? large?)
   - Application contexts (website, print, merchandise, etc.)
   - Color vs monochrome versions needed
   - Background usage (light, dark, transparent)
   - Scalability requirements

5. **Number of Variations**
   - How many different concepts? (Recommend 3-5)
   - How many layouts per concept? (Horizontal, vertical, square, circular)
   - Color variations needed?

### Phase 2: Design Concept Development

Create multiple logo concepts based on requirements:

#### Concept 1: Primary Direction

Develop the main design direction:

**Design Thinking:**
- Research visual metaphors related to brand
- Consider negative space opportunities
- Ensure memorability and uniqueness
- Balance simplicity with distinctiveness
- Consider cultural appropriateness

**SVG Structure:**
```xml
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 200 200" width="200" height="200">
  <defs>
    <!-- Gradients, patterns, filters -->
    <linearGradient id="gradient1" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#4F46E5;stop-opacity:1" />
      <stop offset="100%" style="stop-color:#7C3AED;stop-opacity:1" />
    </linearGradient>
  </defs>

  <!-- Logo elements -->
  <g id="logo-symbol">
    <!-- Symbol/icon elements -->
  </g>

  <g id="logo-text">
    <!-- Text elements (if applicable) -->
  </g>
</svg>
```

#### Concept 2-5: Alternative Directions

Create variations exploring different visual approaches:
- Different visual metaphors
- Different style treatments
- Different layouts and compositions
- Different color applications

### Phase 3: Layout Variations

For each concept, create multiple layout options:

#### Layout A: Horizontal Lockup
- Icon on left, text on right
- Best for website headers, business cards
- Wider aspect ratio

#### Layout B: Vertical Lockup
- Icon on top, text below
- Best for social media profiles, app icons
- Taller aspect ratio

#### Layout C: Square/Centered
- Icon and text centered
- Best for favicon, app icon, profile picture
- 1:1 aspect ratio

#### Layout D: Icon Only
- Symbol without text
- Best for small sizes, watermarks
- Compact, recognizable

#### Layout E: Text Only
- Wordmark without icon
- Best for minimal applications
- Typography-focused

### Phase 4: SVG Generation

Create professional, optimized SVG code:

**Best Practices:**

1. **Clean, Semantic Code**
```xml
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 200 60">
  <!-- Use groups for organization -->
  <g id="icon">
    <!-- Icon elements -->
  </g>
  <g id="wordmark">
    <!-- Text elements -->
  </g>
</svg>
```

2. **Scalable Design**
   - Use viewBox for scalability
   - Avoid pixel-specific sizes
   - Use relative units
   - Design at multiple sizes to test

3. **Color Management**
```xml
<!-- Define colors once, reuse throughout -->
<defs>
  <style>
    .primary { fill: #4F46E5; }
    .secondary { fill: #10B981; }
    .text { fill: #1F2937; }
  </style>
</defs>

<rect class="primary" x="0" y="0" width="100" height="100" />
```

4. **Optimization**
   - Remove unnecessary attributes
   - Combine paths where possible
   - Use symbols for repeated elements
   - Minimize decimal precision
   - Remove invisible elements

5. **Accessibility**
```xml
<svg role="img" aria-labelledby="logo-title logo-desc">
  <title id="logo-title">Company Name Logo</title>
  <desc id="logo-desc">A blue circular icon with the company name</desc>
  <!-- Logo content -->
</svg>
```

### Phase 5: Presentation

Present logos in an organized, professional manner:

```markdown
# Logo Design Concepts

## Concept 1: [Concept Name/Theme]

### Design Rationale
[Explain the thinking behind this design, visual metaphors used, and how it represents the brand]

### Primary Logo (Horizontal)
[SVG code here]

**Usage:** Headers, website navigation, business cards
**Dimensions:** 200x60px (scalable)

### Vertical Layout
[SVG code here]

**Usage:** Social media profiles, mobile apps
**Dimensions:** 100x120px (scalable)

### Icon Only
[SVG code here]

**Usage:** Favicon, app icon, small spaces
**Dimensions:** 64x64px (scalable)

### Color Variations

**Full Color:**
- Primary: #4F46E5 (Indigo)
- Secondary: #10B981 (Emerald)

**Monochrome (Dark):**
- Single color: #1F2937 (Gray-900)

**Monochrome (Light):**
- Single color: #FFFFFF (White)

**Reversed:**
- For dark backgrounds
```

### Phase 6: File Generation

Save SVG files with proper naming:

```
company-name-logo-concept1-horizontal.svg
company-name-logo-concept1-vertical.svg
company-name-logo-concept1-icon.svg
company-name-logo-concept2-horizontal.svg
```

Use the Write tool to save each variation.

### Phase 7: Usage Guidelines

Provide comprehensive usage documentation:

## Clear Space
- Maintain minimum clear space around logo
- Distance = Height of logo symbol

## Minimum Sizes
- **Digital:** 100px width minimum
- **Print:** 1 inch width minimum

## Color Usage
- Use full color on white/light backgrounds
- Use monochrome white on dark backgrounds
- Use monochrome dark on light backgrounds

## Incorrect Usage
- Do not stretch or distort the logo
- Do not change colors outside approved palette
- Do not add effects (shadows, glows, etc.)
- Do not rotate or skew the logo
- Do not place on busy backgrounds without clear space

## Web Implementation
```html
<!-- Inline SVG (Recommended for control) -->
<svg><!-- SVG code --></svg>

<!-- Image tag (Simpler) -->
<img src="logo.svg" alt="Company Name Logo" />

<!-- CSS Background -->
<style>
.logo {
  background-image: url('logo.svg');
  background-size: contain;
}
</style>
```

## Export to PNG
```bash
# Using Inkscape (Free)
inkscape logo.svg --export-png=logo.png --export-width=1000

# Using ImageMagick
convert -background none logo.svg logo.png
```

## Color Psychology Guide

| Color | Meaning | Industries |
|-------|---------|------------|
| **Blue** | Trust, professionalism, stability | Finance, technology, healthcare |
| **Green** | Growth, health, eco-friendly | Environment, wellness, finance |
| **Red** | Energy, passion, urgency | Food, entertainment, retail |
| **Purple** | Creativity, luxury, spirituality | Beauty, tech, creative |
| **Orange** | Friendly, energetic, affordable | Retail, food, entertainment |
| **Yellow** | Optimism, clarity, warmth | Food, children, energy |
| **Black/Gray** | Sophisticated, modern, classic | Luxury, fashion, technology |

## Iteration Process

1. **Gather Feedback** - Which concept resonates most?
2. **Refine Selected Concept** - Adjust colors, proportions, details
3. **Create Final Variations** - All layouts and color variations
4. **Deliver Final Package** - All SVG files + usage guidelines

## Deliverables

1. **SVG Files** - All concepts, layouts, and color variations
2. **Documentation** - Usage guidelines, color specs, size recommendations
3. **Technical Info** - Export instructions, web implementation examples
4. **Optional: Mockups** - Logo on business card, website header, product

Great logos are simple, memorable, timeless, versatile, and appropriate. Focus on creating designs that will work across all applications and stand the test of time.
