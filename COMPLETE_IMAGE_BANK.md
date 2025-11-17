# 📸 How to Complete Your Image Bank with Web URLs

## ✅ Quick Answer

**You do NOT need to upload images.** You can use direct web URLs from sites like:
- **Wikimedia Commons** (CC0 license) ← BEST
- **Pixabay** (CC0)
- **Pexels** (CC0)
- **Unsplash** (CC0)

---

## 🎯 How It Works

### Current Setup (Example):
```json
"battery": {
  "image_id": "battery",
  "url": "https://upload.wikimedia.org/wikipedia/commons/thumb/f/f9/Car_battery.jpg"
}
```

### Card References It:
```json
{
  "id": "battery-terminal",
  "image_id": "battery",  ← System looks up URL automatically
  "title": "BATTERY"
}
```

### Player Sees:
- Image loads from Wikimedia, displays on their card
- No upload needed, no local files needed
- Works instantly on any device

---

## 🔍 Finding Images - Step by Step

### **For 4-Stroke Engine:**

**Search 1: Four-Stroke Engine Diagram**
1. Go to: https://commons.wikimedia.org/wiki/Main_Page
2. Search box: `four stroke engine`
3. Find the labeled diagram (PNG, high quality)
4. Right-click image → **Copy image link**
5. Example result: `https://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/Four-Stroke-Engine.png/440px-Four-Stroke-Engine.png`

**Search 2: Spark Plug**
1. Search: `spark plug`
2. Look for clear photo showing electrode gap
3. Copy link
4. Example: `https://upload.wikimedia.org/wikipedia/commons/...`

**Search 3: Piston**
1. Search: `piston engine`
2. Find assembly photo
3. Copy link

**Search 4: Crankshaft**
1. Search: `crankshaft`
2. Select labeled diagram or photo
3. Copy link

### **For Electrical Systems:**

| Component | Search Term | Example Link |
|-----------|-------------|--------------|
| Battery | `car battery 12v` | `https://upload.wikimedia.org/wikipedia/commons/thumb/f/f9/Car_battery_-_AS_seen_in_the_mirror.jpg/800px-Car_battery_-_AS_seen_in_the_mirror.jpg` |
| Alternator | `alternator engine` | Search wikimedia for "alternator" |
| Starter Motor | `starter motor car` | Search wikimedia for "starter motor" |
| Multimeter | `digital multimeter` | `https://upload.wikimedia.org/wikipedia/commons/thumb/f/f8/Multimeter_Hd.jpg/440px-Multimeter_Hd.jpg` |
| Fuse Box | `fuse box car` | Search wikimedia for "fuse box" |

### **For Braking Systems:**

| Component | Search Term | Resource |
|-----------|-------------|----------|
| Disc Brake | `disc brake assembly` | `https://upload.wikimedia.org/wikipedia/commons/thumb/6/6e/Disc_brake_component_names_en.png/440px-Disc_brake_component_names_en.png` |
| Brake Pads | `brake pads` | Wikimedia Commons |
| Brake Rotor | `brake disc ventilated` | Wikimedia Commons |
| Master Cylinder | `brake master cylinder` | Wikimedia Commons |
| ABS Module | `ABS control module` | Wikimedia Commons |

---

## 📝 Copy-Paste URLs (Ready to Use)

Here are **tested working URLs** you can paste directly:

### 4-Stroke Engine:
```
Four-Stroke Diagram:
https://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/Four-Stroke-Engine.png/440px-Four-Stroke-Engine.png

Piston:
https://upload.wikimedia.org/wikipedia/commons/thumb/1/1c/Kolben.svg/440px-Kolben.svg.png

Engine Block:
https://upload.wikimedia.org/wikipedia/commons/thumb/2/26/4StrokeEngine_Ortho_3D_Small.png/440px-4StrokeEngine_Ortho_3D_Small.png
```

### Electrical Systems:
```
Car Battery:
https://upload.wikimedia.org/wikipedia/commons/thumb/f/f9/Car_battery_-_AS_seen_in_the_mirror.jpg/800px-Car_battery_-_AS_seen_in_the_mirror.jpg

Multimeter:
https://upload.wikimedia.org/wikipedia/commons/thumb/f/f8/Multimeter_Hd.jpg/440px-Multimeter_Hd.jpg

Alternator:
https://upload.wikimedia.org/wikipedia/commons/thumb/5/5e/Alternateur_V4_02.jpg/440px-Alternateur_V4_02.jpg
```

### Braking Systems:
```
Disc Brake:
https://upload.wikimedia.org/wikipedia/commons/thumb/6/6e/Disc_brake_component_names_en.png/440px-Disc_brake_component_names_en.png

Brake Pads:
https://upload.wikimedia.org/wikipedia/commons/thumb/3/3c/Brake_pads.jpg/440px-Brake_pads.jpg

Brake Rotor:
https://upload.wikimedia.org/wikipedia/commons/thumb/e/e0/Brake_rotor.jpg/440px-Brake_rotor.jpg
```

---

## 🔧 How to Update Your File

### Step 1: Open `images-bank.json`
Already open in your editor ✓

### Step 2: Find an Entry to Update
Example - find this:
```json
"spark-plug": {
  "id": "spark-plug",
  "name": "Spark Plug",
  "url": "images/4-stroke/spark-plug.jpg",
```

### Step 3: Replace the URL
Change from:
```
"url": "images/4-stroke/spark-plug.jpg"
```

To:
```
"url": "https://upload.wikimedia.org/wikipedia/commons/thumb/[the-url-you-found]"
```

### Step 4: Save File (Ctrl+S)
Done! That image now loads from the web.

### Step 5: Repeat for All 95 Entries

---

## ⚡ Quick Update Strategy

### Option A: Do It All at Once (2-3 hours)
1. Open images-bank.json
2. Go through each category
3. Find and paste URLs for all 95 images
4. Save

### Option B: Do It Gradually (Recommended)
1. Update the 3 most-used images (battery, spark-plug, disc-brake)
2. Test the game
3. Add 10 more
4. Continue as needed

### Option C: Complete Critical Ones First
1. 4-Stroke Engine (12 images) - foundational
2. Electrical (10 images) - most used
3. Braking (10 images) - critical
4. Tools (6 images)
5. Diagrams (6 images)

---

## ✅ Testing Your URLs

### Before Adding to Bank:

1. **Copy the URL**
```
https://upload.wikimedia.org/wikipedia/commons/thumb/...
```

2. **Open in New Tab**
   - Paste URL in browser address bar
   - Press Enter
   - Should see the image display

3. **Confirm it's Good**
   - ✓ Image visible
   - ✓ Clear and readable
   - ✓ Appropriate size
   - ✓ No watermarks (if possible)

4. **If 404 Error**
   - Search again, find different image
   - Or try different site (Pixabay, Pexels)

5. **Add to Bank**
   - Replace the placeholder URL with confirmed link
   - Save file

---

## 🎨 Good vs Bad Images

### ✅ GOOD Images:
- Clear and readable
- 400x300+ pixels minimum
- High contrast (easy to see details)
- No watermarks
- Appropriate to subject
- CC0 or CC-BY licensed

### ❌ AVOID:
- Blurry or pixelated
- Too small (<200px)
- Heavy watermarks
- Generic/wrong subject
- Copyrighted (check license)
- Broken links (404s)

---

## 📊 File Structure After Updates

```json
{
  "metadata": { ... },
  "images": {
    "4-stroke-engine": {
      "intake-stroke": {
        "id": "intake-stroke",
        "name": "Intake Stroke",
        "url": "https://upload.wikimedia.org/wikipedia/commons/...",  ← WEB URL
        "description": "...",
        "type": "diagram",
        "size": "400x300",
        "topic": "4-stroke-engine",
        "levels": ["entry", "level1", "level2"]
      }
    }
  }
}
```

---

## 🚀 Once Your URLs Are Entered

### Your Game Will:
1. **Load image bank** when app starts
2. **Read URLs** from each image entry
3. **Display images** in cards automatically
4. **Show images** in Match Challenge mode
5. **Resize** to fit card layout

### No Additional Setup Needed!

---

## 🔗 Useful Resources

### Image Search:
- **Wikimedia Commons**: https://commons.wikimedia.org
- **Pixabay**: https://pixabay.com
- **Pexels**: https://pexels.com
- **Unsplash**: https://unsplash.com
- **TinEye**: https://tineye.com (reverse search)

### License Check:
- **Creative Commons Search**: https://search.creativecommons.org
- **Check Wikimedia License**: Look at image page, check permissions tab

### Image Tools:
- **URL Test**: Just paste URL in browser
- **Screenshot Tool**: For YouTube videos or web pages
- **Image Optimizer**: https://tinypng.com (compress large files)

---

## 🐛 Troubleshooting

### Image Not Showing in Game?
```
✓ Check URL works in browser first
✓ Confirm image_id matches entry id
✓ Check for typos in URL
✓ Verify JSON syntax is valid (use jq)
```

### URL Returns 404?
```
✓ Try different image
✓ Search Wikimedia again
✓ Use Pixabay or Pexels instead
✓ Copy full URL (not shortened)
```

### JSON File Won't Validate?
```bash
# Check syntax
jq . cards/images-bank.json

# Look for errors and fix
```

### Images Load Slowly?
```
✓ Normal for first load
✓ Browser caches them after
✓ Consider using Pixabay (faster servers)
✓ Use image optimizer to reduce file size
```

---

## 💡 Pro Tips

### Tip 1: Use Wikimedia Collections
- Go to Collections tab
- Browse by topic (vehicles, engines, tools)
- Already vetted, good quality

### Tip 2: Get Direct Links
- Right-click image on Wikimedia
- Select "Open image in new tab"
- Copy full URL from address bar

### Tip 3: Test Batch Before Saving
- Update 5-10 URLs
- Save and test game
- Make sure images display
- Then continue with more

### Tip 4: Keep Backup
- Before massive changes
- Save a copy: `cp images-bank.json images-bank-backup.json`
- So you can revert if needed

### Tip 5: Mix Sources
- Wikimedia for diagrams
- Pixabay for photos
- Unsplash for generic components
- Different sources = better variety

---

## 📋 Checklist for Completion

### For Each Image Entry:
- [ ] Found appropriate image online
- [ ] Tested URL works (opens in browser)
- [ ] Image is clear and readable
- [ ] Image is 300px+ dimensions
- [ ] License allows usage (CC0/CC-BY)
- [ ] Replaced placeholder URL with actual URL
- [ ] JSON still validates (`jq . images-bank.json`)
- [ ] Game still loads without errors

### Final Validation:
- [ ] All 95 images have web URLs
- [ ] No broken links (test random sample)
- [ ] JSON file validates
- [ ] Game loads and displays images
- [ ] All 4 game modes work
- [ ] Images display in Match Challenge
- [ ] Ready for classroom use!

---

## 🎓 Example: Complete One Category

### 4-Stroke Engine (Do This First)

```json
{
  "4-stroke-engine": {
    "intake-stroke": {
      "id": "intake-stroke",
      "name": "Intake Stroke",
      "url": "https://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/Four-Stroke-Engine.png/440px-Four-Stroke-Engine.png",
      "description": "Piston moving down, intake valve open, fuel mixture entering",
      "type": "diagram",
      "size": "400x300",
      "topic": "4-stroke-engine",
      "levels": ["entry", "level1", "level2"]
    },
    "compression-stroke": {
      "id": "compression-stroke",
      "name": "Compression Stroke",
      "url": "https://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/Four-Stroke-Engine.png/440px-Four-Stroke-Engine.png",
      "description": "Both valves closed, piston moving up, mixture compressed",
      "type": "diagram",
      "size": "400x300",
      "topic": "4-stroke-engine",
      "levels": ["entry", "level1", "level2"]
    }
  }
}
```

All entries can reference the same diagram (or different ones if you find more).

---

## 📞 Need Help?

### Common Questions:

**Q: Can I use the same image for multiple entries?**
A: ✓ YES! Same image, different `image_id`

**Q: Do images need to stay in specific folders?**
A: ✗ NO! Web URLs work anywhere

**Q: What if an image disappears later?**
A: Find replacement, update URL, game works again

**Q: Can I mix web URLs and local files?**
A: ✓ YES! Some entries use `https://...`, others use `images/...`

**Q: How many images can I have?**
A: Unlimited! Just add more entries to the bank

**Q: Do students need internet?**
A: Only to load images first time (then cached)

---

## 🎯 Recommended Next Steps

1. **This Week**: Add URLs for 4-Stroke Engine + Electrical (22 images)
2. **Next Week**: Add Braking Systems (10 images)
3. **Then**: Tools (6) + Diagrams (6)
4. **Finally**: Test everything, ready to teach!

---

**Version**: 1.0  
**Status**: Ready to Start  
**Estimated Time**: 2-3 hours for all 95 images (or spread over days)  
**Difficulty**: Easy (copy-paste URLs)

