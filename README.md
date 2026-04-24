# poke-kitchen

to launch in the web run 
python3 -m http.server 8080
in the project's directory and then go to
https://127.0.0.1:8080/#
to see the webpage


# Features:
Cook for yourself: Create custom automation workflows
Community recipes: Browse and install pre-made automations
Remix feature: Fork and customize existing recipes
Drafts: Auto-save recipes to localStorage
Integrations: Connect with Notion, Uber, Canvas, Venmo, Strava, and more

# Structure:
kitchen/
├── index.html              # Main application (single-page)
├── manifest.json           # PWA manifest
├── package.json            # Dependencies & scripts
│
├── dist/
│   └── output.css         # Compiled Tailwind CSS
│
├── src/
│   └── input.css          # Tailwind source with custom styles
│
├── recipies/
│   ├── styles.css         # Coastal design system tokens
│   └── recipes-form.css   # Recipe modal styles & animations
│
├── mobile-adaptive.css    # iOS optimizations & safe areas
├── tailwind.config.js     # Tailwind configuration
│
├── icons/                 # SVG icons
├── logos/                 # Integration logos (Notion, Uber, etc.)
