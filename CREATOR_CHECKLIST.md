# ✅ Content Creator Checklist

Use this checklist when adding new topics to ensure everything is correct.

---

## Pre-Creation Planning

- [ ] Decide on topic name and ID (e.g., "fuel-systems")
- [ ] Choose emoji icon (e.g., ⛽)
- [ ] Decide which levels to create (Entry/L1/L2/L3)
- [ ] Plan number of pairs per level (Entry 4-8, L1 8, L2 10, L3 12-20)
- [ ] Gather reference materials
- [ ] Outline key concepts for each level

---

## Step 1: Update topics.json

### File Location
`/topics.json`

### Checklist
- [ ] File opens in editor without errors
- [ ] Found the "topics" array
- [ ] Created new topic object
- [ ] Added required fields:
  - [ ] `id`: Unique identifier (lowercase, hyphens only)
  - [ ] `name`: Display name (proper capitalization)
  - [ ] `icon`: Single emoji
  - [ ] `description`: 1-2 sentences
  - [ ] `levels`: Array of levels like `["level1", "level2", "level3"]`
- [ ] No trailing commas
- [ ] JSON validates at jsonlint.com
- [ ] Saved file

### Example to Copy
```json
{
  "id": "your-topic-id",
  "name": "Your Topic Name",
  "icon": "🔧",
  "description": "Brief description of the topic",
  "levels": ["level1", "level2", "level3"]
}
```

---

## Step 2: Create Card Data File

### File Location
`/cards/{topic-id}.json` (replace {topic-id} with your topic ID)

### Process
- [ ] Copy `/cards/TEMPLATE.json`
- [ ] Rename to match topic ID: `{topic-id}.json`
- [ ] Replace `TEMPLATE.JSON` in the file with your topic ID
- [ ] Keep structure identical to template

### File Validation
- [ ] File name matches topic ID exactly
- [ ] File saved in `/cards/` folder
- [ ] Opens without syntax errors
- [ ] Validates at jsonlint.com

---

## Step 3: Create Entry Level (if applicable)

**Only if creating Entry Level 3 content**

### Structure Check
- [ ] Has `"entry"` level section
- [ ] `pairCount` set to 4
- [ ] Has exactly 8 card objects (4 pairs)
- [ ] Each pair has matching `matchId`

### Content Check
- [ ] Level name describes it as "Entry Level 3"
- [ ] Description mentions "introduction" or "basics"
- [ ] Language is simple and accessible
- [ ] Uses clear, common terminology

### Card Quality
- [ ] All 4 pairs are related concepts
- [ ] Emojis are large and clear
- [ ] Titles are 1-2 words
- [ ] Content is concise (20-40 chars)
- [ ] Content uses simple language

---

## Step 4: Create Level 1

### Structure Check
- [ ] Has `"level1"` level section
- [ ] `pairCount` set to 8
- [ ] Has exactly 16 card objects (8 pairs)
- [ ] Each pair has unique, matching `matchId`
- [ ] No duplicate `matchId` values

### Content Check
- [ ] Level name describes it as "Level 1"
- [ ] Description mentions "foundation" or "basic"
- [ ] Introduces main components/systems
- [ ] Builds on concepts from Entry level (if exists)

### Card Quality
- [ ] All 8 pairs are distinct concepts
- [ ] Emojis are relevant and varied
- [ ] Titles are component/system names (3-4 words max)
- [ ] Content explains "what" and "how"
- [ ] All pairs have clear relationship

### Class Values
- [ ] Using valid class: `component`, `valve`, `stroke-intake`, `stroke-compression`, `stroke-power`, `stroke-exhaust`
- [ ] Related cards use same class where appropriate
- [ ] Consistent styling throughout level

---

## Step 5: Create Level 2

### Structure Check
- [ ] Has `"level2"` level section
- [ ] `pairCount` set to 10
- [ ] Has exactly 20 card objects (10 pairs)
- [ ] No duplicate `matchId` values

### Content Check
- [ ] Level name describes it as "Level 2"
- [ ] Description mentions "intermediate" or "systems"
- [ ] Introduces system interactions
- [ ] Includes some diagnostic concepts
- [ ] More technical than Level 1

### Card Quality
- [ ] 10 distinct pairs
- [ ] Includes mixture of components and systems
- [ ] More detailed explanations
- [ ] Answers "why" questions
- [ ] Introduction of technical terms

### Testing Difficulty
- [ ] 20 cards should take 5-10 minutes to match
- [ ] Not too easy, not frustrating
- [ ] Progressive difficulty curve

---

## Step 6: Create Level 3

### Structure Check
- [ ] Has `"level3"` level section
- [ ] `pairCount` set to 12-14
- [ ] Has exactly 24-28 card objects
- [ ] No duplicate `matchId` values

### Content Check
- [ ] Level name describes it as "Level 3"
- [ ] Description mentions "advanced" or "expert"
- [ ] Expert-level terminology
- [ ] Advanced diagnostic concepts
- [ ] Performance tuning information

### Card Quality
- [ ] 12-14 distinct pairs
- [ ] Technical language appropriate
- [ ] Complex system interactions
- [ ] Real-world application focus
- [ ] Industry-standard terminology

### Testing Difficulty
- [ ] 24-28 cards should take 10-20 minutes
- [ ] Challenging but achievable
- [ ] Requires subject knowledge

---

## JSON Validation Checklist

- [ ] No syntax errors (red lines)
- [ ] All braces match: `{` with `}`
- [ ] All brackets match: `[` with `]`
- [ ] All quotes match: `"` with `"`
- [ ] No trailing commas after last item
- [ ] All string values in quotes
- [ ] All required fields present
- [ ] No extra or misspelled fields
- [ ] Validated at jsonlint.com

### Common JSON Errors
- [ ] Missing closing brace
- [ ] Trailing comma after last array item
- [ ] Unmatched quotes
- [ ] Single quotes instead of double quotes
- [ ] Missing colons after property names
- [ ] Comments in JSON (not allowed)

---

## Content Quality Checklist

### Title Quality
- [ ] 1-4 words maximum
- [ ] Capitalized properly (ALL CAPS for parts)
- [ ] Descriptive of card content
- [ ] Consistent style throughout

### Content Quality
- [ ] Clear and concise
- [ ] Uses bullets with `\n` for line breaks
- [ ] 2-3 key points per card
- [ ] Simple language (Year 9 reading level)
- [ ] No typos or grammar errors
- [ ] Consistent formatting

### Pair Relationships
- [ ] Card 1 = Name/Concept
- [ ] Card 2 = Function/Description
- [ ] Cards clearly match related content
- [ ] No confusion possible

### Emoji Usage
- [ ] One emoji per card
- [ ] Relevant to content
- [ ] Variety of emojis (not repeating)
- [ ] Clear and recognizable
- [ ] Consistent with topic

---

## Testing in Browser

### Initial Load
- [ ] Open index.html
- [ ] No console errors (F12)
- [ ] Page loads cleanly
- [ ] All graphics render

### Topic Selection
- [ ] Your topic appears in grid
- [ ] Topic icon displays
- [ ] Topic name shows
- [ ] Description visible

### Level Selection
- [ ] All your levels appear as buttons
- [ ] Level names display correctly
- [ ] Selected level is highlighted

### Game Difficulty
- [ ] Easy mode loads correct card count
- [ ] Medium mode loads correct card count
- [ ] Hard mode loads correct card count

### Game Play
- [ ] Cards appear in grid
- [ ] Cards flip smoothly
- [ ] Emojis display correctly
- [ ] Text is readable
- [ ] Matching pairs work correctly
- [ ] Non-matching pairs flip back

### Victory Screen
- [ ] Victory message appears
- [ ] Correct winner announced
- [ ] Score displays accurately
- [ ] Play Again works
- [ ] Menu button returns home

### Responsive Testing
- [ ] Works on desktop (1920px+)
- [ ] Works on tablet (768px)
- [ ] Works on mobile (375px)
- [ ] Cards still readable
- [ ] Touch/click working

---

## Browser Compatibility Testing

Test on:
- [ ] Chrome (latest)
- [ ] Firefox (latest)
- [ ] Safari (latest)
- [ ] Mobile Chrome
- [ ] Mobile Safari

---

## Final Deployment Checklist

Before sharing:
- [ ] All JSON files validate
- [ ] All images/emojis load
- [ ] All game modes work
- [ ] All levels accessible
- [ ] All difficulties playable
- [ ] Mobile responsive
- [ ] No console errors
- [ ] Documentation complete
- [ ] README updated if needed
- [ ] Ready to share!

---

## Documentation Updates

When adding new topic, update:
- [ ] `topics.json` (already done)
- [ ] `README.md` - Add topic to list
- [ ] `CONTENT_GUIDE.md` - Mark as done
- [ ] `PROJECT_SUMMARY.md` - Update status table

### How to Update README.md
1. Find the "Current Topics" section
2. Add your topic to the table
3. Check boxes for completed levels
4. Mark status as "DONE"

---

## Common Mistakes to Avoid

❌ **Don't:**
- Use same `matchId` for different pairs
- Forget commas between objects
- Mix single and double quotes
- Add comments in JSON
- Make titles too long
- Use inconsistent emoji styles
- Leave cards blank
- Skip JSON validation
- Test only on one browser
- Forget to update documentation

✅ **Do:**
- Validate JSON before testing
- Test all game modes
- Use consistent formatting
- Match difficulty progression
- Include varied emojis
- Write clear, simple content
- Test on multiple devices
- Update all documentation
- Get peer review if possible
- Keep backup of files

---

## Quick Reference: Field Reference

### Topics.json Fields
```
id          - Unique identifier (lowercase, hyphens)
name        - Display name (Proper Case)
icon        - Single emoji
description - 1-2 sentences
levels      - Array: ["entry", "level1", "level2", "level3"]
```

### Card Fields
```
id        - Unique card ID (lowercase, hyphens)
matchId   - Pairs matching cards (same for pair)
class     - CSS class for styling
emoji     - Single emoji (large on card)
title     - Card title (1-4 words)
type      - Card category (Component, System, etc.)
content   - Card description (use \n for lines)
```

### Valid Class Values
```
component           - Yellow/orange cards
valve              - Purple cards
stroke-intake      - Red cards
stroke-compression - Orange cards
stroke-power       - Green cards
stroke-exhaust     - Blue cards
```

---

## Help & Support

### If stuck:
1. Check QUICK_START.md
2. Review CONTENT_GUIDE.md
3. Compare to working example (electrical-systems.json)
4. Validate JSON at jsonlint.com
5. Check browser console (F12) for errors

### Example Reference Files
- `4-stroke-engine.json` - Complete, all levels
- `electrical-systems.json` - Advanced content
- `braking-systems.json` - Good practices
- `TEMPLATE.json` - Starting point

---

## Sign-Off

Content Creator Name: ________________  
Topic Created: ________________  
Date: ________________  
All Tests Passed: [ ] Yes [ ] No  
Ready for Deployment: [ ] Yes [ ] No  

---

**Version:** 1.0  
**Last Updated:** November 2025
