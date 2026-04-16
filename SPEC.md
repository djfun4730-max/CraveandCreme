# CraveandCreme - Premium Cake Ordering App

## Concept & Vision

A luxurious, mobile-first cake ordering experience that feels like a high-end AI app. The design evokes the elegance of a boutique patisserie with soft pastels, floating decorative elements, and buttery-smooth animations. Every interaction should feel intentional and delightful, transforming cake ordering into an aspirational experience.

## Design Language

### Aesthetic Direction
Inspired by luxury dessert photography meets modern fintech apps. Soft, feminine, premium with glassmorphism and gentle organic shapes.

### Color Palette
- Primary Pink: `#f8c8dc` (light pink)
- Cream: `#fff5e1` (warm cream background)
- Soft Rose: `#ff8fb1` (accent/active states)
- Deep Rose: `#e75480` (buttons, emphasis)
- Text Dark: `#4a3728` (warm brown for readability)
- Text Light: `#8b7355` (secondary text)
- White: `#ffffff` (cards, surfaces)
- Glass White: `rgba(255, 255, 255, 0.7)`

### Typography
- Headings: "Playfair Display" (serif, elegant)
- Body: "Poppins" (clean, modern sans-serif)
- Accent: System emoji for decorative elements

### Spatial System
- Base unit: 8px
- Card padding: 24px
- Border radius: 16px (cards), 12px (buttons), 50% (circles)
- Shadows: Soft, diffused (0 8px 32px rgba(0,0,0,0.1))

### Motion Philosophy
- Entrance: Fade + slide up, 400ms ease-out
- Exit: Fade + slide out, 300ms ease-in
- Hover: Scale 1.02, 200ms ease
- Selection: Scale pulse + color transition, 300ms
- Background floats: 15-25s infinite, linear with varying delays

## Layout & Structure

### Screens
1. **Login Screen** - Full viewport, gradient background with floating elements
2. **Builder Screen** - Split layout: Wizard (left/main), Summary Panel (right/sticky)

### Login Layout
- Centered card (max-width: 400px)
- Logo + Title + Subtitle vertical stack
- Single CTA button
- Floating background elements in 3 layers (different speeds)

### Builder Layout
- Desktop: Two columns (60% wizard, 40% sticky summary)
- Mobile: Single column, summary as collapsible bottom panel
- Progress bar fixed at top
- Step content centered with max-width constraint

## Features & Interactions

### Login Screen
- Floating elements: 🍓🫐🧁🍥✨ (15-20 elements)
- Parallax effect: Elements move at different speeds on mouse movement
- Enter button: Gradient background, hover glow effect
- Transition: Fade out → slide up into main app

### Cake Builder Wizard
7 sequential steps with smooth transitions:

1. **Cake Size**
   - Options: 6", 8", 10" (card selection)
   - Visual: Cake icons of increasing size
   - Price indicator per option

2. **Flavour Selection**
   - Options: Chocolate, Vanilla, Red Velvet, Strawberry
   - Visual: Color swatches matching flavors
   - Red Velvet shows +$6 badge

3. **Frosting Type**
   - Options: Buttercream, Cream Cheese, Fondant
   - Visual: Texture preview icons
   - Cream Cheese shows +$4 badge

4. **Filling**
   - Options: Chocolate, Fruit, Caramel
   - Visual: Color swatches

5. **Custom Text**
   - Input field with character limit (50)
   - Live preview of text on cake illustration
   - Placeholder: "e.g., Happy Birthday!"

6. **Pickup Date**
   - Native date picker
   - Minimum date: tomorrow
   - Styled to match theme

7. **Review & Generate**
   - Summary card of all selections
   - Total price prominently displayed
   - Generate Order Message button
   - Share buttons: Copy, WhatsApp, Email

### Selection Interactions
- Default state: White background, subtle border
- Hover: Slight lift shadow, scale 1.02
- Selected: Pink gradient border, pink background tint, checkmark badge
- Transition: 300ms ease-out

### Summary Panel
- Sticky position on desktop
- Live-updating cake preview (CSS illustration)
- Clean list of selected options
- Dynamic price calculation
- "Your Dream Cake" header

### Price Calculator
- Base: $25
- 6" = +$0, 8" = +$12, 10" = +$20
- Red Velvet = +$6
- Cream Cheese frosting = +$4
- Displayed with $ prefix, animated counter

### Order Message Generation
Format:
```
Hello! I would like to order a custom cake:

🎂 Size: [X]"
🥛 Flavour: [Flavor]
🎨 Frosting: [Frosting]
🍰 Filling: [Filling]
💌 Message: "[Text]"
📅 Pickup: [Date]

Thank you! 🧁
```

### Share Actions
- Copy: Clipboard API with success toast
- WhatsApp: wa.me link with encoded message
- Email: mailto link with subject and body

## Component Inventory

### Floating Element
- Random emoji/symbol
- Size: 24-40px
- Position: Absolute, random start
- Animation: translateY(-100vh) over 15-25s, infinite
- Opacity: 0.3-0.6

### Primary Button
- Background: Linear gradient (#ff8fb1 → #e75480)
- Text: White, Poppins 600
- Padding: 16px 32px
- Border-radius: 12px
- States: Default, Hover (glow + lift), Active (pressed), Disabled (50% opacity)

### Option Card
- Size: Flexible, min 100px width
- Background: White
- Border: 2px solid transparent
- Border-radius: 16px
- States: Default, Hover (shadow), Selected (pink border + tint)

### Progress Bar
- Height: 4px
- Background: #f8c8dc (track)
- Fill: Linear gradient (#ff8fb1 → #e75480)
- Steps indicator: Dots/circles
- Animation: Width transition 400ms

### Summary Card
- Background: Glass white (blur 10px)
- Border: 1px solid rgba(255,255,255,0.5)
- Shadow: Soft diffused
- Sticky on scroll

### Toast Notification
- Position: Bottom center
- Background: Dark with opacity
- Text: White
- Animation: Slide up + fade in, auto-dismiss 3s

## Technical Approach

### Stack
- Single HTML file
- Embedded CSS (in <style>)
- Embedded JavaScript (in <script>)
- Google Fonts CDN (Playfair Display, Poppins)
- Font Awesome CDN for icons

### Architecture
- State object tracking all selections
- Step-based rendering with CSS classes
- Event delegation for option selections
- LocalStorage for persistence (optional enhancement)

### Key Implementation Details
- CSS custom properties for theming
- CSS animations for floating elements (performance)
- JavaScript for step management and state
- CSS Grid/Flexbox for layouts
- Intersection Observer for scroll effects (if needed)
