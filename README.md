# 🏎️ Motor Vehicle Learning Master

A modern, interactive educational game for learning automotive technology through matching card games. Perfect for City & Guilds, BTEC, and IMI motor vehicle courses.

## Features

✨ **Multiple Topics** - 12+ automotive topics
📊 **4 Difficulty Levels** - Entry, Level 1, Level 2, Level 3
🎮 **2 Game Modes** - 2 Player Battle or Group Pairs
📱 **Fully Responsive** - Works on desktop, tablet, and mobile
💪 **Easy to Extend** - JSON-based card system

## Current Topics

- 4-Stroke Engine Cycles
- Electrical Systems  
- Braking Systems
- Fuel Systems (coming soon)
- Suspension & Steering (coming soon)
- Transmission Systems (coming soon)
- Exhaust & Emissions (coming soon)
- Engine Diagnostics (coming soon)
- Hybrid & Electric Vehicles (coming soon)
- Motorsport Preparation (coming soon)
- Workshop Safety (coming soon)
- Tools & Equipment (coming soon)

## How to Add New Topics

### Step 1: Add Topic to `topics.json`

Edit `/topics.json` and add your topic to the topics array:

```json
{
  "id": "fuel-systems",
  "name": "Fuel Systems",
  "icon": "⛽",
  "description": "Petrol and diesel fuel systems",
  "levels": ["level1", "level2", "level3"]
}
```

**Fields:**
- `id`: Unique identifier (must match card file name)
- `name`: Display name
- `icon`: Emoji icon
- `description`: Brief description
- `levels`: Array of available levels ("entry", "level1", "level2", "level3")

### Step 2: Create Card Data File

Create a new JSON file in `/cards/` folder with your topic ID:
`/cards/{topic-id}.json`

Example structure:

```json
{
  "topicId": "fuel-systems",
  "levels": {
    "level1": {
      "name": "Level 1 - Basic Fuel Systems",
      "pairCount": 6,
      "description": "Introduction to fuel systems",
      "cards": [
        {
          "id": "fuel-tank-name",
          "matchId": "fuel-tank",
          "class": "component",
          "emoji": "🛢️",
          "title": "FUEL TANK",
          "type": "Component",
          "content": "Fuel storage"
        },
        {
          "id": "fuel-tank-desc",
          "matchId": "fuel-tank",
          "class": "component",
          "emoji": "💧",
          "title": "Function",
          "type": "Component",
          "content": "Stores fuel Provides volume Protects system"
        }
      ]
    },
    "level2": { /* ... */ },
    "level3": { /* ... */ }
  }
}
```

### Card Structure

Each card object requires:

- **id** (string): Unique card ID
- **matchId** (string): Pairs cards with the same matchId
- **class** (string): CSS class for styling (component, stroke-intake, stroke-compression, stroke-power, stroke-exhaust, valve)
- **emoji** (string): Display emoji
- **title** (string): Card title
- **type** (string): Card category
- **content** (string): Card description (use \n for line breaks)

### Matching Pairs

Cards with the **same matchId** will be treated as a matching pair:

```json
// First card of pair
{
  "id": "engine-name",
  "matchId": "engine",
  ...
}

// Second card of pair
{
  "id": "engine-desc",
  "matchId": "engine",
  ...
}
```

### CSS Classes for Cards

Use these classes to style different card types:

```
- component: Yellow/orange cards
- stroke-intake: Red cards
- stroke-compression: Orange cards
- stroke-power: Green cards
- stroke-exhaust: Blue cards
- valve: Purple cards
```

### Difficulty Levels

- **easy**: Shows first 8 cards (4 pairs)
- **medium**: Shows first 12 cards (6 pairs)
- **hard**: Shows all cards in the level

### Level Guidelines

**Entry Level 3 (entry):**
- 4-8 pairs
- Simple, foundational concepts
- Large emojis and simple text
- Basic terminology

**Level 1 (level1):**
- 8-10 pairs
- Foundation technical knowledge
- Component names and functions
- Basic system understanding

**Level 2 (level2):**
- 10-14 pairs
- Intermediate technical knowledge
- System interactions
- Diagnostic concepts
- Performance characteristics

**Level 3 (level3):**
- 14-20 pairs
- Advanced technical knowledge
- Complex diagnostics
- Performance tuning
- Expert-level terminology

## File Structure

```
enginegame/
├── index.html              # Main game file
├── topics.json             # Topic definitions
├── cards/
│   ├── 4-stroke-engine.json
│   ├── electrical-systems.json
│   ├── braking-systems.json
│   └── ... (add more topics here)
└── README.md               # This file
```

## How to Use

1. Open `index.html` in a modern web browser
2. Select a topic from the topic grid
3. Choose your difficulty level
4. Select 2-Player Battle or Group Pairs mode
5. Click cards to reveal them
6. Match pairs of related cards
7. Player with most matches wins!

## Browser Compatibility

- Chrome/Chromium
- Firefox
- Safari
- Edge
- Mobile browsers (iOS Safari, Chrome Mobile)

## Technical Details

- Pure vanilla JavaScript (no frameworks)
- CSS Grid for responsive layout
- Fetch API for loading JSON data
- CSS 3D transforms for card flip animation
- LocalStorage-ready (for future features)

## Tips for Content Creators

✅ **DO:**
- Match difficulty progression across levels
- Use consistent emoji for card types
- Keep titles short (1-2 words)
- Test cards at all difficulties
- Use clear, student-friendly language
- Include at least 6 pairs per level

❌ **DON'T:**
- Use complex terminology without context
- Make cards too text-heavy
- Mix unrelated topics
- Use the same matchId twice
- Forget to add topics to topics.json

## Example Topic: Suspension & Steering

### topics.json entry:
```json
{
  "id": "suspension-steering",
  "name": "Suspension & Steering",
  "icon": "🔧",
  "description": "Chassis and handling systems",
  "levels": ["level1", "level2", "level3"]
}
```

### Create `/cards/suspension-steering.json` with your content

## Future Enhancements

- 🎯 Leaderboard system
- 📊 Progress tracking
- 🏆 Achievement badges
- 🎨 Custom themes
- 🌍 Multi-language support
- 📱 PWA support
- 🔊 Sound effects
- ⏱️ Timed challenges

## License

Educational use only.

## Support

For issues or suggestions, please refer to the development team.

---

**Last Updated:** November 2025
**Version:** 2.0 (Multi-Topic Release)
