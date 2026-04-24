# poke-kitchen

A recipe-based automation platform for building and sharing custom workflows.

## Getting Started

```bash
python3 -m http.server 8080
```

Then navigate to `https://127.0.0.1:8080/#`

## Features

- **Cook for yourself** — Create custom automation workflows
- **Community recipes** — Browse and install pre-made automations
- **Remix** — Fork and customize existing recipes
- **Drafts** — Auto-save recipes to localStorage
- **Integrations** — Connect with Notion, Uber, Canvas, Venmo, Strava, and more

## Project Structure

```
kitchen/
├── index.html              # Main application (single-page)
├── manifest.json           # PWA manifest
├── package.json            # Dependencies & scripts
│
├── dist/
│   └── output.css          # Compiled Tailwind CSS
│
├── src/
│   └── input.css           # Tailwind source with custom styles
│
├── recipies/
│   ├── styles.css          # Coastal design system tokens
│   └── recipes-form.css    # Recipe modal styles & animations
│
├── mobile-adaptive.css     # iOS optimizations & safe areas
├── tailwind.config.js      # Tailwind configuration
│
├── icons/                  # SVG icons
└── logos/                  # Integration logos (Notion, Uber, etc.)
```
