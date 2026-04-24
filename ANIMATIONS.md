# Animation System

This document describes all the subtle animations added to the Poke interface.

## 🎬 View Transitions

### Modal Opening
- **Overlay**: Fades in with backdrop blur (0.25s ease-out)
- **Panel**: Slides up from bottom with scale effect (0.3s ease-out)
  - Starts at: translateY(20px) scale(0.98) with opacity 0
  - Ends at: translateY(0) scale(1) with opacity 1

### View Switching (Cooking ↔ Drafts)
- **Animation**: Slide in from right (0.3s ease-out)
- **Effect**: Content slides in with 20px horizontal offset and fade
- Applies to:
  - `#cookComposerView` (recipe creation form)
  - `#cookDraftsView` (saved drafts list)
  - `#exploreContent` (community recipes)
  - `#recipesSubView` (sub-pages)

### Hub Navigation
- **Animation**: Fade in (0.25s ease-out)
- Simple opacity transition for returning to main hub

## 🎯 Interactive Elements

### Action Cards (Main Interface)
```css
Hover: No visual change
Active: scale(0.97)
Focus-visible: Blue outline ring
Transition: transform 0.2s, background 0.2s, box-shadow 0.2s
```

### Segment Buttons (Cooking/Drafts Toggle)
```css
Hover: Background darkens slightly
Active: scale(0.97)
Transition: background-color 0.2s, color 0.2s, font-weight 0.2s
```
- Smooth color and weight transitions when switching between states

### Integration Tiles
```css
Hover: scale(1.05) + opacity 0.8
Active: scale(0.95)
Selected: "Pop in" animation (0.2s ease-out)
  - 0%: scale(0.9) opacity(0.6)
  - 50%: scale(1.08)
  - 100%: scale(1) opacity(1)
```

### Primary Buttons (Cook Recipe, etc.)
```css
Hover: translateY(-1px) + shadow increase
Active: translateY(0) + shadow decrease
Transition: background 0.15s, transform 0.15s, opacity 0.15s
```

### Draft Cards & Community Tiles
```css
Hover: translateY(-1px) + border darkens + shadow
Transition: All properties 0.15s ease
```

### New Recipe Button
```css
Hover: translateY(-1px) + opacity(0.92) + shadow
Active: Returns to original position
```

## ♿ Accessibility

### Reduced Motion Support
All animations respect `prefers-reduced-motion: reduce`:

```css
@media (prefers-reduced-motion: reduce) {
  /* Disable all view transitions */
  #cookComposerView, #cookDraftsView, etc. {
    animation: none;
  }
  
  /* Disable all scale transforms */
  .action-card:active,
  .recipe-seg:active,
  .integration-tile:hover {
    transform: none;
  }
  
  /* Disable integration tile pop animation */
  .integration-tile.is-selected {
    animation: none;
  }
}
```

## 🎨 Animation Principles

### Timing
- **Fast interactions**: 0.15s - 0.2s (buttons, hovers, clicks)
- **View transitions**: 0.25s - 0.3s (page changes, modals)
- **Easing**: ease-out for all animations (natural deceleration)

### Transform Properties
All animations use GPU-accelerated properties only:
- ✅ `transform` (translateY, translateX, scale)
- ✅ `opacity`
- ❌ No layout-shifting properties (width, height, margin, padding)

### Subtle Scale Effects
- Hover: Slight grow (1.05x) or lift (translateY -1px)
- Active: Slight shrink (0.95-0.97x) for tactile feedback
- Selected: Pop effect with overshoot (1.08x peak)

## 📱 Mobile Considerations

### Touch Interactions
- Active states provide immediate visual feedback
- No hover effects on touch devices (handled by CSS)
- Transform animations are subtle to prevent "jank"

### Performance
- All animations use `transform` and `opacity` for 60fps
- No `transition: all` - explicit properties only
- Animations are interruptible (can be cancelled mid-flight)

## 🔑 Key Files

1. **recipies/recipes-form.css**
   - View transition keyframes
   - Integration tile animations
   - Button hover states
   - Modal entrance animations

2. **src/input.css**
   - Action card interactions
   - Focus-visible styles
   - Base component animations

3. **mobile-adaptive.css**
   - Touch-optimized interactions
   - Reduced motion overrides
   - Mobile-specific transitions

## 🎯 Animation Inventory

| Element | Animation | Duration | Easing |
|---------|-----------|----------|--------|
| Modal overlay | Fade in | 250ms | ease-out |
| Modal panel | Slide up + scale | 300ms | ease-out |
| View switch | Slide from right | 300ms | ease-out |
| Hub return | Fade in | 250ms | ease-out |
| Action card press | Scale down | 200ms | ease |
| Segment button | Color + weight | 200ms | ease |
| Integration tile select | Pop (scale overshoot) | 200ms | ease-out |
| Integration tile hover | Scale up | 150ms | ease |
| Button hover | Lift + shadow | 150ms | ease |
| Draft card hover | Lift + shadow | 150ms | ease |

All animations maintain consistency and follow Vercel's performance guidelines.
