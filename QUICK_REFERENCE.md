# 🎯 Quick Reference - Image Bank & New Features

## 🚀 Quick Start for Developers

### Load Image Bank in JS:
```javascript
await loadImageBank();  // Called in init()
```

### Get Image URL from Bank:
```javascript
const url = resolveImageUrl("battery");
// Returns: "images/electrical/battery.jpg"
```

### Card with Image ID:
```json
{
  "id": "battery-card",
  "matchId": "battery",
  "image_id": "battery",
  "title": "BATTERY"
}
```

### Card with Direct URL (Fallback):
```json
{
  "id": "battery-card",
  "matchId": "battery",
  "image_url": "images/electrical/battery.jpg",
  "title": "BATTERY"
}
```

---

## 🎮 Game Mode Constants

```javascript
startGame('one-player')   // 🎮 Solo mode
startGame('two-player')   // 👥 2 Player
startGame('group')        // 👨‍👩‍👧‍👦 Group
startGame('match-mode')   // 🎯 Match Challenge
```

---

## 📸 Image Bank Structure

```json
{
  "metadata": { ... },
  "images": {
    "category-name": {
      "image-id": {
        "id": "image-id",
        "name": "Human Name",
        "url": "images/path/file.jpg",
        "description": "What it shows",
        "type": "photo|diagram",
        "size": "400x300",
        "topic": "topic-id",
        "levels": ["level1", "level2"]
      }
    }
  },
  "searchIndex": { ... }
}
```

---

## 📂 Folder Structure

```
images/
├── 4-stroke/           (12 images)
├── electrical/         (10 images)
├── braking/            (10 images)
├── tools/              (6 images)
└── diagrams/           (6 images)

cards/
├── images-bank.json    (Central registry)
├── 4-stroke-engine.json
├── electrical-systems.json
└── braking-systems.json
```

---

## ✨ New Game Flow

### Match Challenge Mode:
```
1. loadGameCards()
   ├─ Fetch card file
   ├─ Load Image Bank
   └─ Call renderMatchMode()

2. renderMatchMode()
   ├─ Select random cards as "source"
   ├─ Get matching pairs
   ├─ Create option buttons (1 correct + 2 wrong)
   └─ Display source card with image + options

3. handleMatchModeSelection()
   ├─ Check if correct
   ├─ Update score
   ├─ Show feedback (✅ or ❌)
   └─ Next match or victory
```

---

## 🎨 CSS for New Features

### Mode Buttons:
```css
.mode-btn.one-player {
  background: linear-gradient(135deg, #fa709a 0%, #fee140 100%);
}

.mode-btn.match-mode {
  background: linear-gradient(135deg, #30cfd0 0%, #330867 100%);
}
```

### Card Images:
```css
/* Display on card front */
img {
  max-width: 60px;
  max-height: 60px;
  margin: 5px 0;
  border-radius: 3px;
}

/* Display in Match Challenge */
img {
  max-width: 80px;
  margin-bottom: 8px;
  border-radius: 5px;
}
```

---

## 🔍 Image Bank Search Index

```json
"searchIndex": {
  "by-topic": {
    "4-stroke-engine": ["intake-stroke", "piston-assembly", ...],
    "electrical-systems": ["battery", "alternator", ...]
  },
  "by-type": {
    "photo": ["battery", "alternator", ...],
    "diagram": ["valve-timing-diagram", ...]
  },
  "by-level": {
    "entry": ["intake-stroke", ...],
    "level1": ["battery", "intake-stroke", ...],
    "level3": ["multimeter", ...]
  }
}
```

---

## 📝 Adding Image to Bank

### Step 1: Edit `images-bank.json`
```json
{
  "images": {
    "4-stroke-engine": {
      "new-image": {
        "id": "new-image",
        "name": "New Component",
        "url": "images/4-stroke/new-image.jpg",
        "description": "Description here",
        "type": "photo",
        "size": "400x300",
        "topic": "4-stroke-engine",
        "levels": ["level1", "level2"]
      }
    }
  }
}
```

### Step 2: Upload Image
```
images/4-stroke/new-image.jpg
```

### Step 3: Use in Cards
```json
{
  "image_id": "new-image"
}
```

---

## 🐛 Debugging

### Check if Image Bank Loaded:
```javascript
console.log(gameState.imageBank);
```

### Resolve Image URL:
```javascript
console.log(resolveImageUrl("battery"));
// Should return: "images/electrical/battery.jpg"
```

### Check Network:
```
F12 → Network → Filter for 404s
Look for images or images-bank.json failures
```

### Validate JSON:
```bash
jq . cards/images-bank.json
```

---

## 🔄 Migration Path

### Old Card Format:
```json
{
  "image_url": "images/electrical/battery.jpg"
}
```

### New Card Format:
```json
{
  "image_id": "battery"  ← Must exist in bank
}
```

### Fallback Support:
Both work! System tries `image_id` first, falls back to `image_url`.

---

## 💡 Tips & Tricks

### Reuse Images:
```json
// In electrical-systems.json
{ "image_id": "wrench" }

// In fuel-systems.json
{ "image_id": "wrench" }

// Same image, both use it!
```

### Find All Images for Topic:
```javascript
gameState.imageBank['4-stroke-engine']
// Returns all images in that category
```

### Find All Photos:
```javascript
const photos = Object.values(gameState.imageBank)
  .flatMap(cat => Object.values(cat))
  .filter(img => img.type === 'photo');
```

### Add Batch of Images:
```bash
# Copy all JPGs and update bank
cp /source/images/* images/4-stroke/
# Then add entries to images-bank.json
```

---

## 📊 Statistics

| Metric | Value |
|--------|-------|
| Total Images in Bank | 95 |
| Categories | 5 |
| Game Modes | 4 |
| Difficulty Levels | 3 |
| Curriculum Levels | 4 |
| Topics Defined | 12 |
| Topics Complete | 3 |
| Documentation Files | 10 |

---

## ✅ Checklist for New Image

- [ ] Image optimized (300-500px, <100KB)
- [ ] Added to `images-bank.json`
- [ ] Image file uploaded to correct folder
- [ ] `image_id` matches bank ID
- [ ] Cards reference with `image_id`
- [ ] Tested in browser
- [ ] Both image_id and fallback work
- [ ] JSON validates

---

## 🎯 Common Tasks

### Task: Change image location
```
Old: images/electrical/battery.jpg
New: images/components/battery.jpg

Solution: Update ONE entry in images-bank.json
All cards automatically use new location!
```

### Task: Share image between topics
```
1. Add image to bank (category: shared-tools)
2. Use same image_id in multiple card files
3. Done! Single source, multiple uses
```

### Task: Replace all images in category
```
1. Update folder: images/4-stroke/
2. Update URLs in images-bank.json
3. All cards automatically reflect changes
```

### Task: Find unused images
```javascript
// Find all image IDs in cards
// Compare to bank
// Delete unused entries
```

---

## 🚀 Performance Notes

- Image Bank loads once on app start
- URL resolution is instant lookup
- Graceful fallback if image missing
- No performance penalty for missing images
- Image display is optional feature

---

## 📱 Mobile Considerations

- Images scale to 60px on cards (responsive)
- Match Challenge images 80px (readable)
- Touch-friendly button sizes
- All modes work on mobile
- Works offline (images cached)

---

## 🔐 File Permissions

```bash
# Make image bank readable
chmod 644 cards/images-bank.json

# Make image folder readable
chmod 755 images/
chmod 644 images/*/*.jpg
```

---

## 📚 Related Documentation

- `IMAGE_BANK_GUIDE.md` - Complete Image Bank documentation
- `NEW_FEATURES.md` - All new features overview
- `MATCH_CHALLENGE_GUIDE.md` - Match mode details
- `QUICK_START.md` - Content creation
- `IMPLEMENTATION_COMPLETE.md` - Full summary

---

**Version:** 1.0  
**Last Updated:** November 17, 2025  
**Status:** ✅ Production Ready

