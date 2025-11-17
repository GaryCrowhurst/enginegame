# 🎯 Match Challenge Mode - Creator Guide

## What is Match Challenge Mode?

A new interactive game mode where players **match descriptions to images and names** instead of flipping cards.

Perfect for:
- ✅ Visual identification training
- ✅ Diagnostic procedure matching
- ✅ Quick comprehension checks
- ✅ Faster-paced learning
- ✅ Test-style questioning

---

## How Match Challenge Works (Player Perspective)

1. **Source Card Displays** (left side):
   - Shows: Name, emoji, image (if available), and description
   - This is the "question" the player sees

2. **Match Options** (right side):
   - Shows 3 button options
   - Player clicks the correct match
   - 1 correct answer + 2 wrong answers

3. **Feedback**:
   - ✅ Correct = green background, score increases
   - ❌ Wrong = red background, stays available to try again

4. **Progress**:
   - Score shows how many correct matches found
   - All pairs must be matched to complete

---

## Content Structure for Match Challenge

Match Challenge works like regular matching but displays differently:

### Key Concept: One Card is the "Source"

For each pair, **one card becomes the source/question**:

```json
{
  "id": "component1-image",
  "matchId": "component1",
  "emoji": "🔧",
  "title": "What component is this?",
  "type": "Name",
  "content": "A mechanical part that...",
  "image_url": "images/component1-photo.jpg"
}
```

The matching pair provides the answer options:

```json
{
  "id": "component1-function",
  "matchId": "component1",
  "emoji": "📖",
  "title": "INTAKE VALVE",
  "type": "Function",
  "content": "Controls air-fuel mixture entry",
  "image_url": "images/component1-diagram.jpg"
}
```

---

## Example: Engine Components (Level 1)

### Source Cards:

**Card 1 (Source):**
```json
{
  "id": "piston-image",
  "matchId": "piston",
  "emoji": "📸",
  "title": "What is this component?",
  "type": "Photo",
  "content": "A cylindrical part that moves up and down inside the cylinder",
  "image_url": "images/piston-photo.jpg"
}
```

**Card 2 (Source):**
```json
{
  "id": "spark-image",
  "matchId": "spark",
  "emoji": "📸",
  "title": "What is this component?",
  "type": "Photo",
  "content": "A small electrical device that creates sparks",
  "image_url": "images/spark-plug-photo.jpg"
}
```

### Answer Cards:

**Card 1 (Answer to Piston):**
```json
{
  "id": "piston-name",
  "matchId": "piston",
  "emoji": "🔧",
  "title": "PISTON",
  "type": "Component",
  "content": "Moves up and down to compress and push the air-fuel mixture",
  "image_url": "images/piston-diagram.jpg"
}
```

**Card 2 (Answer to Spark):**
```json
{
  "id": "spark-name",
  "matchId": "spark",
  "emoji": "⚡",
  "title": "SPARK PLUG",
  "type": "Component",
  "content": "Ignites the compressed air-fuel mixture",
  "image_url": "images/spark-plug-diagram.jpg"
}
```

---

## Best Practices for Match Challenge Content

### 1. **Make Source Cards Clear Questions**
```json
// ✅ GOOD - Clear question format
{
  "id": "valve-question",
  "matchId": "intake-valve",
  "title": "Which component is shown?",
  "type": "Photo",
  "content": "Red cylindrical valve visible in engine...",
  "image_url": "images/intake-valve-photo.jpg"
}

// ❌ AVOID - Ambiguous
{
  "id": "valve-photo",
  "matchId": "intake-valve",
  "title": "Intake Valve",
  "content": "A valve",
  "image_url": "images/intake-valve-photo.jpg"
}
```

### 2. **Provide Good Wrong Answers**
Choose wrong answers that are:
- Similar difficulty level
- Related to same topic
- Plausible but clearly wrong
- Encourage careful reading

```json
// Answer options algorithm picks:
// 1. Correct: Intake Valve
// 2. Wrong: Exhaust Valve (similar component)
// 3. Wrong: Spark Plug (same engine topic)
```

### 3. **Use Images Effectively**
- **Source card image**: The item to identify
- **Answer card images**: Supporting visuals

```json
{
  "id": "battery-source",
  "matchId": "battery",
  "title": "Identify this component",
  "image_url": "images/battery-physical.jpg"  // Real photo
}

{
  "id": "battery-answer",
  "matchId": "battery",
  "title": "BATTERY",
  "image_url": "images/battery-diagram.jpg"   // Schematic
}
```

### 4. **Appropriate Difficulty Escalation**

**Level 1:**
```json
// Easy to identify - clear photos
{
  "title": "What is this tool?",
  "image_url": "images/wrench-clear.jpg"
}
```

**Level 2:**
```json
// Harder to identify - close-ups, specific parts
{
  "title": "Identify this component in situ",
  "image_url": "images/valve-closeup-engine.jpg"
}
```

**Level 3:**
```json
// Expert level - diagnostic scenarios
{
  "title": "What diagnostic procedure is shown?",
  "image_url": "images/multimeter-fault-reading.jpg"
}
```

---

## Pair Structure for Match Challenge

Each matchId creates ONE challenge question:

```
matchId: "intake-valve"
    ├── Card 1 (Source): Shows photo → "Identify this"
    └── Card 2 (Answer): Shows name → "Intake Valve"

matchId: "compression-stroke"
    ├── Card 1 (Source): Shows diagram → "What stroke?"
    └── Card 2 (Answer): Shows definition → "Compression..."
```

The game randomly selects which card to show as the source.

---

## Template for Match Challenge Content

```json
{
  "topicId": "my-topic",
  "levels": {
    "level1": {
      "name": "Level 1 - Matching",
      "pairCount": 4,
      "cards": [
        {
          "id": "item1-visual",
          "matchId": "item1",
          "emoji": "📸",
          "title": "Identify Component",
          "type": "Photo",
          "content": "Shows a mechanical part used in the system",
          "image_url": "images/item1-photo.jpg"
        },
        {
          "id": "item1-name",
          "matchId": "item1",
          "emoji": "🔧",
          "title": "COMPONENT NAME",
          "type": "Component",
          "content": "Technical name and function description",
          "image_url": "images/item1-diagram.jpg"
        },
        {
          "id": "item2-visual",
          "matchId": "item2",
          "emoji": "📸",
          "title": "Identify Component",
          "type": "Photo",
          "content": "Another mechanical part shown in operation",
          "image_url": "images/item2-photo.jpg"
        },
        {
          "id": "item2-name",
          "matchId": "item2",
          "emoji": "🔧",
          "title": "COMPONENT NAME",
          "type": "Component",
          "content": "Technical name and function description",
          "image_url": "images/item2-diagram.jpg"
        }
      ]
    }
  }
}
```

---

## Image Requirements for Match Challenge

### Visual Quality:
- **Resolution**: 300-500px (shows at ~80-100px size)
- **Format**: JPG (70-80% quality), PNG, GIF
- **Content**: Clear, well-lit photos or diagrams

### Organization:
```
images/
├── intake-valve-photo.jpg      (Real world photo)
├── intake-valve-diagram.jpg    (Technical diagram)
├── piston-assembly.jpg         (Component photo)
├── crankshaft-diagram.jpg      (Schematic)
└── engine-cross-section.jpg    (System diagram)
```

### File Naming Convention:
```
[component-name]-[view-type].jpg

Examples:
- intake-valve-photo.jpg
- intake-valve-diagram.jpg
- intake-valve-cutaway.jpg
- piston-assembly.jpg
- piston-cross-section.jpg
```

---

## Tips for Better Match Challenge Content

### ✅ DO:
- ✅ Use clear, high-quality images
- ✅ Make source cards unambiguous questions
- ✅ Include descriptions with images
- ✅ Test matching logic before deploying
- ✅ Use appropriate difficulty progression
- ✅ Mix photo and diagram styles

### ❌ DON'T:
- ❌ Use blurry or low-contrast images
- ❌ Make questions too cryptic
- ❌ Use vague descriptions
- ❌ Mix unrelated concepts in wrong answers
- ❌ Repeat images across different topics
- ❌ Include color hints (no highlighting)

---

## Migration: Converting Existing Topics

### From Regular Mode to Match Challenge:

1. **Take your existing card pairs:**
```json
// Existing pair
{
  "id": "intake-name",
  "matchId": "intake",
  "title": "INTAKE STROKE",
  "content": "Piston DOWN"
}
```

2. **Enhance with images:**
```json
// Add visual element
{
  "id": "intake-visual",
  "matchId": "intake",
  "emoji": "📸",
  "title": "Identify this stroke",
  "content": "Piston moving downward, valves opening",
  "image_url": "images/intake-stroke.jpg"
}
```

3. **Keep original as answer:**
```json
// Remains the definition
{
  "id": "intake-name",
  "matchId": "intake",
  "title": "INTAKE STROKE",
  "content": "Piston DOWN - Fuel mixture enters",
  "image_url": "images/intake-diagram.jpg"
}
```

4. **Result:**
   - Match Challenge shows: Photo + question
   - Player matches to: Name + definition
   - Works in all game modes!

---

## Testing Your Match Challenge Content

### Quick Checklist:
- [ ] All cards have valid JSON syntax
- [ ] All `matchId` values have exactly 2 cards
- [ ] All `image_url` files exist
- [ ] Images are readable at small size
- [ ] Questions are clear and unambiguous
- [ ] Wrong answer options are different enough
- [ ] Content flows logically by difficulty
- [ ] Tested in browser at all zoom levels

### Test Procedure:
1. Open `index.html`
2. Select topic
3. Select level
4. Select difficulty
5. Click **🎯 Match Challenge**
6. Verify: Source card displays with image
7. Verify: Options appear below
8. Verify: Clicking correct = green
9. Verify: Clicking wrong = red
10. Verify: All pairs complete = victory

---

## Sharing Match Challenge Content

When creating new topics with Match Challenge:

1. **Create standard card pairs** (name/description)
2. **Add images** to half the cards
3. **Mark as Match Challenge ready** in documentation
4. **Provide image pack** separately if needed
5. **Include setup guide** for other creators

---

## Examples by Subject

### 4-Stroke Engine:
- Source: Photo of each stroke
- Answer: Stroke name + description

### Electrical Systems:
- Source: Component photo
- Answer: Component name + function

### Braking Systems:
- Source: Brake type diagram
- Answer: System name + how it works

### Fuel Systems:
- Source: Injector/pump photo
- Answer: Component + operation

### Suspension:
- Source: Spring/damper photo
- Answer: Component type + purpose

---

## FAQ

**Q: Can I use Match Challenge without images?**  
A: Yes! Content displays fine without images. Add them gradually.

**Q: Do both cards in a pair need images?**  
A: No - one source card typically has image, answer card supports it but isn't required.

**Q: Can I use photos from the internet?**  
A: Check licensing! Use royalty-free sites:
- Pixabay.com
- Unsplash.com
- Wikimedia Commons
- Manufacturer datasheets

**Q: How do I get good component photos?**  
A: Options:
1. Take photos yourself in workshop
2. Use photos from YouTube videos (educational use)
3. Use manufacturer diagrams
4. Create digital illustrations

**Q: Can I mix image types?**  
A: Yes! Mix real photos, diagrams, screenshots, scans for variety.

**Q: Does every topic need Match Challenge?**  
A: No - use where images add value. Regular matching great for pure vocabulary.

---

## Questions?

See:
- `NEW_FEATURES.md` - Complete features overview
- `QUICK_START.md` - Content creation basics
- `CONTENT_GUIDE.md` - Topic planning
- `CREATOR_CHECKLIST.md` - Quality assurance

---

**Last Updated:** November 17, 2025  
**Status:** ✅ Ready for Use

