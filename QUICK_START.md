# 🚀 Quick Start Guide - Adding New Topics

## 30-Minute Setup

### What You Need
- Text editor (VS Code, Notepad++, etc.)
- The template file in `cards/TEMPLATE.json`
- Your topic content

### Step 1: Plan Your Content (5 min)

Decide on:
- Topic name & ID (e.g., `fuel-systems`)
- Emoji icon (e.g., ⛽)
- Number of pairs per level (6, 8, 10, 12, etc.)
- Key concepts to teach

### Step 2: Update topics.json (2 min)

Open `/topics.json` and add your topic:

```json
{
  "id": "fuel-systems",
  "name": "Fuel Systems",
  "icon": "⛽",
  "description": "Petrol and diesel fuel delivery",
  "levels": ["level1", "level2", "level3"]
}
```

**Available levels:**
- `"entry"` - For Entry Level 3 courses
- `"level1"` - Foundation technical
- `"level2"` - Intermediate systems
- `"level3"` - Advanced expertise

### Step 3: Create Card File (20 min)

1. Copy `cards/TEMPLATE.json`
2. Rename to `cards/{your-topic-id}.json`
3. Replace `TEMPLATE.JSON` values with your content

**Key Rules:**
- Every pair needs 2 cards with same `matchId`
- Use `class` values: `component`, `stroke-intake`, `stroke-power`, `valve`, etc.
- Add newlines with `\n` in content
- Keep titles short (1-4 words)

### Step 4: Test Your Topic (3 min)

1. Open `index.html` in browser
2. Select your new topic
3. Test each difficulty level
4. Verify all pairs match correctly

## Real Example: Fuel Systems

### Topic Entry (topics.json):
```json
{
  "id": "fuel-systems",
  "name": "Fuel Systems",
  "icon": "⛽",
  "description": "Petrol and diesel fuel systems",
  "levels": ["level1", "level2", "level3"]
}
```

### Level 1 Cards (simplified):
```json
{
  "id": "fuel-pump-name",
  "matchId": "fuel-pump",
  "class": "component",
  "emoji": "⛽",
  "title": "FUEL PUMP",
  "type": "Component",
  "content": "Electric pump"
}
{
  "id": "fuel-pump-desc",
  "matchId": "fuel-pump",
  "class": "component",
  "emoji": "⚙️",
  "title": "Function",
  "type": "Component",
  "content": "Draws fuel from tank\nPushes to injectors\nMaintains pressure"
}
```

## Card Styling Classes

| Class | Color | Use For |
|-------|-------|---------|
| `component` | Yellow/Orange | Parts, systems, general |
| `stroke-intake` | Red | Intake stroke content |
| `stroke-compression` | Orange | Compression concepts |
| `stroke-power` | Green | Power/combustion |
| `stroke-exhaust` | Blue | Exhaust concepts |
| `valve` | Purple | Valve systems |

## Content Tips

✅ **Good Content:**
```
"Pumps fuel from tank\nMaintains pressure\nElectric operation"
```

❌ **Too Verbose:**
```
"The electric fuel pump is responsible for extracting fuel from the storage tank and delivering it to the fuel injection system while maintaining the required pressure for proper atomization"
```

## Emoji Suggestions by Topic

| Topic | Emoji |
|-------|-------|
| Engines | 🏎️ ⚙️ 💥 |
| Electrical | 🔋 ⚡ 🔌 |
| Brakes | 🛑 🔒 💫 |
| Fuel | ⛽ 💧 🔧 |
| Transmission | ⚙️ 🔄 📊 |
| Suspension | 🔧 🛠️ ↕️ |
| Exhaust | 💨 🌫️ 🔥 |
| Tools | 🔨 🔧 🔩 |
| Safety | ⚠️ 🛡️ 🔒 |

## Common Issues & Fixes

### Issue: Cards not matching
**Solution:** Check `matchId` is EXACTLY the same on both cards

### Issue: Topic doesn't appear
**Solution:** 
1. Verify ID in topics.json matches filename
2. Check JSON syntax (use validator)
3. Refresh browser cache

### Issue: Cards look wrong
**Solution:** Check `class` value matches one of the valid classes

### Issue: Text runs off card
**Solution:** Keep content under 50 characters, use `\n` for breaks

## JSON Validation

Before testing, paste your JSON into:
https://jsonlint.com/

Red errors = fix before using

## Full Topic Template

See `cards/TEMPLATE.json` for complete structure with all levels.

## Advanced: Custom Styling

To create custom card colors, edit `index.html` CSS:

```css
.card-front.custom-class {
  background: linear-gradient(135deg, #COLOR1 0%, #COLOR2 100%);
  border: 4px solid #BORDERCOLOR;
}
```

Then use `class: "custom-class"` in your cards.

## Questions?

Refer to example topics:
- `/cards/4-stroke-engine.json` - Complete example
- `/cards/electrical-systems.json` - Advanced example
- `/cards/braking-systems.json` - Another example

---

**Pro Tip:** Create one level at a time and test before moving to the next!
