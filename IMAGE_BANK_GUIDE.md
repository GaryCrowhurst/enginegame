# 📸 Image Bank System Guide

## Overview

The Image Bank system provides a **centralized, single-file manager** for all images across all topics. Instead of storing image URLs directly in each card file, you reference images by their **ID**, and the system looks them up in a central bank.

### Benefits:
- ✅ **Single point of management** - Change image URLs in one place
- ✅ **Shared images** - Reuse same image across multiple topics
- ✅ **Easier migration** - Move image files without updating every card
- ✅ **Better organization** - Search index shows all available images
- ✅ **Metadata tracking** - Know which level/topic uses each image
- ✅ **Scalability** - Manage 100s of images efficiently

---

## How It Works

### 1. Central Image Bank (`images-bank.json`)
Contains all image references organized by category:

```json
{
  "images": {
    "4-stroke-engine": {
      "piston-assembly": {
        "id": "piston-assembly",
        "url": "images/4-stroke/piston-assembly.jpg",
        "description": "...",
        "type": "photo",
        "topic": "4-stroke-engine",
        "levels": ["level1", "level2"]
      }
    },
    "electrical-systems": { ... },
    "shared-tools": { ... }
  }
}
```

### 2. Card Files Reference by Image ID
Instead of storing full URLs:

```json
// OLD WAY (deprecated)
{
  "id": "piston-card",
  "matchId": "piston",
  "image_url": "images/4-stroke/piston-assembly.jpg",  // Direct URL
  "title": "PISTON"
}

// NEW WAY (using image bank)
{
  "id": "piston-card",
  "matchId": "piston",
  "image_id": "piston-assembly",  // References the bank
  "title": "PISTON"
}
```

### 3. Application Resolution
When rendering a card, the app:
1. Checks if card has `image_id` field
2. Looks up the ID in `images-bank.json`
3. Retrieves the actual URL
4. Displays the image

```
Card: { "image_id": "piston-assembly" }
    ↓
Lookup in Bank: "piston-assembly"
    ↓
Get URL: "images/4-stroke/piston-assembly.jpg"
    ↓
Display Image
```

---

## File Structure

### Directory Organization:
```
enginegame/
├── cards/
│   ├── images-bank.json          ← Central image registry
│   ├── 4-stroke-engine.json      ← Uses image IDs
│   ├── electrical-systems.json   ← Uses image IDs
│   └── braking-systems.json      ← Uses image IDs
└── images/                        ← Actual image files
    ├── 4-stroke/
    │   ├── piston-assembly.jpg
    │   ├── crankshaft.jpg
    │   └── spark-plug.jpg
    ├── electrical/
    │   ├── battery.jpg
    │   ├── alternator.jpg
    │   └── multimeter.jpg
    ├── braking/
    │   ├── disc-brake.jpg
    │   ├── abs-module.jpg
    │   └── brake-hose.jpg
    ├── tools/
    │   ├── wrench.jpg
    │   ├── socket-set.jpg
    │   └── torque-wrench.jpg
    └── diagrams/
        ├── engine-cross-section.jpg
        ├── fuel-system.jpg
        └── braking-circuit.jpg
```

---

## Using the Image Bank

### Step 1: Add Image to Bank
Edit `cards/images-bank.json` and add an entry:

```json
{
  "images": {
    "4-stroke-engine": {
      "new-component": {
        "id": "new-component",
        "name": "Component Name",
        "url": "images/4-stroke/new-component.jpg",
        "description": "What this image shows",
        "type": "photo",
        "size": "400x300",
        "topic": "4-stroke-engine",
        "levels": ["level1", "level2"]
      }
    }
  }
}
```

### Step 2: Upload Image File
Place your image in the appropriate folder:
```
images/4-stroke/new-component.jpg
```

### Step 3: Reference in Cards
Update your card file to use the image ID:

```json
{
  "id": "component-name",
  "matchId": "component",
  "emoji": "🔧",
  "title": "COMPONENT",
  "type": "Component",
  "content": "Description",
  "image_id": "new-component"  ← References the bank
}
```

---

## Image Bank Entry Structure

Every image entry should have:

```json
{
  "id": "unique-identifier",           // Must be unique across entire bank
  "name": "Human Readable Name",       // For documentation
  "url": "images/category/file.jpg",   // Relative path from web root
  "description": "What's shown...",    // Helps others find it
  "type": "photo|diagram|chart",       // Image type
  "size": "400x300",                   // Approximate dimensions
  "topic": "topic-id",                 // Primary topic
  "levels": ["entry", "level1"]        // Which curriculum levels
}
```

---

## Search Index

The image bank includes a `searchIndex` for quick lookups:

```json
{
  "searchIndex": {
    "by-topic": {
      "4-stroke-engine": ["intake-stroke", "piston-assembly", "..."],
      "electrical-systems": ["battery", "alternator", "..."]
    },
    "by-type": {
      "photo": ["battery", "alternator", "..."],
      "diagram": ["valve-timing-diagram", "...]"
    },
    "by-level": {
      "level1": ["battery", "intake-stroke", "..."],
      "level3": ["multimeter", "obd-scanner", "..."]
    }
  }
}
```

Use this to:
- Find all images for a topic
- Find all photo vs diagram images
- Find age-appropriate images for a level

---

## Sharing Images Across Topics

### Example: Using tool images in multiple topics

**Image Bank Entry:**
```json
{
  "images": {
    "shared-tools": {
      "wrench": {
        "id": "wrench",
        "url": "images/tools/wrench.jpg",
        "topic": "tools-equipment",
        "levels": ["level1", "level2"]
      }
    }
  }
}
```

**Used in multiple card files:**
```json
// In 4-stroke-engine.json
{ "image_id": "wrench", ... }

// In fuel-systems.json
{ "image_id": "wrench", ... }

// In suspension-steering.json
{ "image_id": "wrench", ... }
```

**Benefit:** Update `images/tools/wrench.jpg` once, applies everywhere!

---

## Migrating Existing Cards

### Before (Direct URLs):
```json
{
  "id": "battery-card",
  "matchId": "battery",
  "image_url": "images/electrical/battery.jpg",
  "title": "BATTERY"
}
```

### After (Image Bank):
1. Add to image bank:
```json
"battery": {
  "id": "battery",
  "name": "Car Battery",
  "url": "images/electrical/battery.jpg",
  "topic": "electrical-systems",
  "levels": ["level1"]
}
```

2. Update card file:
```json
{
  "id": "battery-card",
  "matchId": "battery",
  "image_id": "battery",  // ← Changed
  "title": "BATTERY"
}
```

3. Remove `image_url` field (optional, but cleaner)

### Migration Script:
To batch migrate, you can use this sed command:
```bash
# Replace direct URLs with image IDs
sed -i 's/"image_url": "images\/electrical\/battery.jpg"/"image_id": "battery"/g' cards/electrical-systems.json
```

---

## Creating Custom Image Banks per Topic

### Option 1: Global Bank (Recommended)
One `images-bank.json` for all topics - great for sharing

### Option 2: Topic-Specific Banks
If you prefer separate files:

```json
// cards/images-bank-4-stroke.json
{
  "images": {
    "4-stroke-engine": { ... }
  }
}
```

Then update the `loadImageBank()` function:
```javascript
async function loadImageBank() {
  const banks = await Promise.all([
    fetch('cards/images-bank-4-stroke.json'),
    fetch('cards/images-bank-electrical.json'),
    fetch('cards/images-bank-braking.json')
  ]);
  
  // Merge all banks
  gameState.imageBank = {};
  for (const response of banks) {
    const data = await response.json();
    Object.assign(gameState.imageBank, data.images);
  }
}
```

---

## Image Optimization Tips

### Before Upload:
1. **Resize** - Typically 400x400px max
2. **Compress** - Use TinyPNG or similar (70-80% JPG quality)
3. **Optimize** - Remove metadata with ExifTool
4. **Format** - JPG for photos, PNG for diagrams

### File Naming:
```
4-stroke/
├── intake-stroke.jpg         (main noun-adjective)
├── intake-valve-diagram.jpg  (more descriptive)
├── piston-assembly.jpg       (part-component)
└── spark-plug-closeup.jpg    (component-view)

electrical/
├── battery.jpg
├── multimeter-display.jpg
└── can-bus-diagram.jpg
```

### Metadata to Include:
```json
{
  "id": "battery",
  "description": "12V lead-acid battery with terminals visible, typical car battery",
  "source": "Own photo | Wikipedia Commons | Pixabay",
  "license": "CC0 | CC-BY-4.0 | Purchased",
  "created": "2025-11-17",
  "photographer": "Name/Source"
}
```

---

## Fallback Behavior

The system supports **graceful fallback**:

### Scenario 1: Image ID not found in bank
```javascript
Card has: { "image_id": "missing-id" }
Result: Image doesn't show, card displays fine without it
```

### Scenario 2: Both image_id and image_url present
```javascript
{
  "image_id": "battery",      // ← Tried first
  "image_url": "local-img.jpg" // ← Used if ID not found
}
```

### Scenario 3: No images at all
```javascript
Card displays with emoji, title, text - works perfectly
```

---

## API Reference

### JavaScript Functions:

#### `loadImageBank()`
Loads the central image bank on app startup
```javascript
await loadImageBank();
// Sets gameState.imageBank
```

#### `resolveImageUrl(imageId)`
Looks up image URL by ID
```javascript
const url = resolveImageUrl("battery");
// Returns: "images/electrical/battery.jpg"
// Returns: null if not found
```

---

## Example: Complete Workflow

### 1. Photographer takes battery image
```
battery.jpg (2MB, 3000x2400px)
```

### 2. Optimize for web
```
battery.jpg (85KB, 400x300px, 75% quality)
```

### 3. Upload to images/electrical/
```
images/electrical/battery.jpg
```

### 4. Add to images-bank.json
```json
"electrical-systems": {
  "battery": {
    "id": "battery",
    "name": "Car Battery",
    "url": "images/electrical/battery.jpg",
    "description": "12V lead-acid battery showing positive and negative terminals",
    "type": "photo",
    "size": "400x300",
    "topic": "electrical-systems",
    "levels": ["level1", "level2"]
  }
}
```

### 5. Create card JSON
```json
{
  "id": "battery-1",
  "matchId": "battery",
  "emoji": "🔋",
  "title": "BATTERY",
  "type": "Component",
  "content": "Stores electrical energy",
  "image_id": "battery"  // ← References bank
}
```

### 6. Use in multiple topics
```json
// electrical-systems.json
{ "image_id": "battery", "title": "BATTERY" }

// Can also use in tools-equipment.json
{ "image_id": "battery", "title": "Testing Battery" }

// And in starting-systems.json
{ "image_id": "battery", "title": "Battery Terminals" }
```

### 7. Change image later
Edit `images-bank.json`:
```json
"battery": {
  "url": "images/electrical/battery-v2.jpg"  // ← Changed
}
```

**All three card files automatically show new image!**

---

## Advantages vs Direct URLs

| Aspect | Direct URL | Image Bank |
|--------|-----------|-----------|
| Update image path | Update every card file | Update 1 entry |
| Shared images | Duplicate URLs | One entry, used many |
| Find all images | Manual search | Search index |
| Metadata | None | Complete |
| Documentation | Hard | Easy |
| Migration | Tedious | Systematic |

---

## JSON Validation

Ensure your image bank is valid:
```bash
jq . cards/images-bank.json
# If no errors, JSON is valid
```

Or use online validator: https://jsonlint.com/

---

## Troubleshooting

### Images Not Showing?

1. **Check browser console** (F12 → Console)
   - Look for 404 errors on image URLs

2. **Verify image_id is in bank**
   ```bash
   grep "image-id-here" cards/images-bank.json
   ```

3. **Check image file exists**
   ```bash
   ls -la images/category/file.jpg
   ```

4. **Verify URL path is relative**
   - Use: `images/electrical/battery.jpg`
   - Not: `/images/electrical/battery.jpg`
   - Not: `file:///var/www/images/...`

5. **Clear browser cache**
   - Ctrl+Shift+Delete → Clear cache

### Bank Not Loading?

1. Check network tab for 404 on `cards/images-bank.json`
2. Verify JSON syntax is valid
3. Check file permissions: `chmod 644 images-bank.json`
4. Restart browser/server

---

## Future Enhancements

Potential features to consider:
- [ ] Image upload utility (web interface)
- [ ] Automatic image optimization
- [ ] CDN integration for image hosting
- [ ] Image statistics (usage, size, downloads)
- [ ] Batch image operations
- [ ] AI alt-text generation

---

## Questions?

See:
- `NEW_FEATURES.md` - Overview of new image support
- `MATCH_CHALLENGE_GUIDE.md` - Using images in Match Challenge
- `QUICK_START.md` - Content creation basics

---

**Last Updated:** November 17, 2025  
**Status:** ✅ Production Ready  
**Version:** 1.0

