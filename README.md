# Dodson Motorsport — Global Dealer Network Globe

Interactive 3D globe displaying Dodson Motorsport's worldwide dealer network of 250+ dealers, with tier-coloured dot pins, smart clustering, real-time day/night terminator, search, and filter controls.

## How to Run

Open `index.html` in any modern browser — no server required. Works locally via `file://`.

## File Structure

```
dodson-dealer-globe/
├── index.html         ← Main application (HTML + CSS + JS)
├── dealers.js         ← Dealer data array (250 dealers)
├── dodson-logo.png    ← Dodson logo
└── README.md
```

## Features

### Globe Display
- NASA night-lights Earth texture with atmosphere glow
- Real-time day/night terminator — warm sunlit side, cool darkened night side, calculated from actual sun position
- Intro zoom animation on first load
- Auto-rotation with pause on interaction

### Dealer Pins
- Dot-style sprite pins (always face camera, no edge-on invisibility)
- Tier-coloured with radial glow halo (Platinum, Gold, Blue, Teal)
- Subtle pulse animation
- Hover glow — hovered pin scales up and brightens
- Click to open detailed dealer info panel

### Smart Clustering
- Pins in dense regions (US East Coast, Western Europe) merge into numbered cluster markers
- Cluster threshold adapts to zoom level
- Click a cluster to see the list of dealers or zoom in

### Filter Panel
- Toggle with the "Filter Dealers" button or press `F`
- Filter by dealer tier (checkboxes)
- Filter by country (dropdown)
- Filter by platform (dropdown)
- "SHOWING // N" counter updates live
- Reset Filters button to clear all

### Search
- Live search by dealer name, city, or country
- Single result auto-flies the globe to that dealer and opens the info panel
- Multiple results filter the visible pins and update the count
- Clear button to reset

### Keyboard Shortcuts
| Key | Action |
|-----|--------|
| `/` | Focus search bar |
| `F` | Toggle filter panel |
| `Esc` | Close panels |
| `R` | Reset view (zoom, rotation, filters, search) |
| Arrow keys | Rotate globe |
| `+` / `-` | Zoom in / out |

### Mobile Responsive
- Touch drag to rotate, pinch to zoom
- Panels slide from the bottom on small screens
- Keyboard hints hidden on mobile

## Updating Dealer Data

Edit `dealers.js` — it exports a `const DEALERS = [...]` array. Each dealer object:

```js
{
  id: 1,
  name: "DEALER NAME",
  city: "Auckland, New Zealand",
  address: "Full street address",
  phone: "+64 9 123 4567",
  email: "email@dealer.com",
  website: "https://www.dealer.com",
  platforms: ["Nissan GT-R R35", "Porsche PDK"],
  tier: "Pro Dealer",
  lat: -36.8509,
  lng: 174.7645,
  region: "",
  instagram: ""
}
```

### Adding Coordinates

Dealers with `lat: null` or `lng: null` are excluded from the globe until geocoded. Use a geocoding service to convert city names to coordinates.

## Dealer Tier System

| Tier | Description | Pin Colour |
|------|------------|------------|
| Distributor | Regional/country distributors | Platinum/White |
| Pro Dealer | High-volume, multi-platform (4+) | Gold |
| Dealer Plus | Mid-tier engagement (2-3 platforms) | Electric Blue |
| Standard | Single-platform dealers | Muted Teal |

## Web Integration

Drop the folder into any web project and embed via iframe:

```html
<iframe src="dodson-dealer-globe/index.html" width="100%" height="600" frameborder="0"></iframe>
```

Or lift the JS/CSS directly into your site's codebase.

## Tech Stack

- Three.js r128 (CDN)
- Custom GLSL shaders (day/night terminator)
- Google Fonts (Rajdhani + Share Tech Mono)
- No build tools, no npm, no backend
