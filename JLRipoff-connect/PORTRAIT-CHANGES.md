# Portrait Version Changes Summary

This document summarizes the specific changes made to create the portrait/vertical versions.

## Files Created

1. **index-portrait.html** (83 KB) - Portrait version with full visual effects
2. **index-lite-portrait.html** (81 KB) - Portrait version optimized for older hardware
3. **README-PORTRAIT.md** - Comprehensive documentation for portrait versions

## Key Layout Changes

### 1. Grid Layout
**Before (Horizontal):**
```css
grid-template-columns: 1fr 1fr;
grid-template-rows: 1fr 1fr;
```
- 2x2 grid showing 4 albums per page

**After (Portrait):**
```css
grid-template-columns: 1fr;
grid-template-rows: 1fr 1fr;
```
- 1x2 grid showing 2 albums per page

### 2. Album Cell Structure
**Before (Horizontal):**
```css
.album-cell {
  flex-direction: row;  /* Side by side */
}
```
- Track list on left, album art on right

**After (Portrait):**
```css
.album-cell {
  flex-direction: column;  /* Stacked */
}
```
- Album art on top, track list below

### 3. Album Art Sizing
**Before (Horizontal):**
```css
.album-cov {
  flex: 0 1 350px;
  width: 35vw;
  max-width: 440px;
}
```

**After (Portrait):**
```css
.album-cov {
  flex: 0 0 auto;
  width: 100%;
  height: 300px;
}
```

### 4. Track List Layout
**Before (Horizontal):**
```css
.album-list {
  flex: 1 1 60%;
  max-width: 46vw;
  border-radius: 16px 0 0 16px;
  border-right: 2.5px solid #19efe411;
}
```

**After (Portrait):**
```css
.album-list {
  flex: 1 1 auto;
  border-radius: 0 0 16px 16px;
  border-top: 2.5px solid #19efe411;
}
```

### 5. Track Name Wrapping
**Before (Horizontal):**
```css
.track-row {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.track-title {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  max-width: 88%;
}
```

**After (Portrait):**
```css
.track-row {
  white-space: normal;
  overflow: visible;
  align-items: flex-start;
  padding-top: 4px;
  padding-bottom: 4px;
}

.track-title {
  white-space: normal;
  word-wrap: break-word;
  overflow-wrap: break-word;
  flex: 1;
  line-height: 1.3;
}
```

### 6. Track Number Alignment
**Before (Horizontal):**
```css
.tracknum {
  vertical-align: middle;
  display: inline-block;
}
```

**After (Portrait):**
```css
.tracknum {
  vertical-align: top;
  display: inline-block;
  flex-shrink: 0;
  align-self: flex-start;
}
```

### 7. Button Sizing
**Before (Horizontal):**
```css
.cornerpanel .btn {
  min-width: 70px;
  min-height: 32px;
  padding: 7px 22px;
  font-size: 1em;
  border-radius: 10px;
}
```

**After (Portrait):**
```css
.cornerpanel .btn {
  min-width: 55px;
  min-height: 28px;
  padding: 5px 14px;
  font-size: 0.88em;
  border-radius: 8px;
}
```
- 21% smaller min-width (70px → 55px)
- 12.5% smaller min-height (32px → 28px)
- 12% smaller font size (1em → 0.88em)

### 8. Viewport Constraints
**Before (Horizontal):**
```css
html, body {
  min-width: 1080px;
  width: 100vw;
}
```

**After (Portrait):**
```css
html, body {
  width: 1080px;
  max-width: 1080px;
  min-height: 1920px;
}
```

## JavaScript Changes

### Grid Creation Function
**Before (Horizontal):**
```javascript
function createGrid(pageIdx) {
  const offset = pageIdx * 4;
  for (let y = 0; y < 2; y++) for (let x = 0; x < 2; x++) {
    const i = offset + y*2+x;
    // ... create cells
    cell.appendChild(leftpanel);  // Track list first
    cell.appendChild(cov);        // Album art second
  }
}

function totalPages() { 
  return Math.ceil(albums.length/4); 
}
```

**After (Portrait):**
```javascript
function createGrid(pageIdx) {
  const offset = pageIdx * 2;
  for (let y = 0; y < 2; y++) {
    const i = offset + y;
    // ... create cells
    cell.appendChild(cov);        // Album art first
    cell.appendChild(leftpanel);  // Track list second
  }
}

function totalPages() { 
  return Math.ceil(albums.length/2); 
}
```

## Visual Impact

### Horizontal Layout (1080 width)
```
┌────────────────────────────────────────┐
│  Header                                │
├──────────────┬──────────────────────────┤
│              │              │           │
│ Track List 1 │  Art 1       │           │
│              │              │           │
├──────────────┴──────────────┤           │
│              │              │           │
│ Track List 2 │  Art 2       │           │
│              │              │           │
└──────────────┴──────────────────────────┘
│  Buttons (Play controls, Keypad, etc.) │
└────────────────────────────────────────┘
```

### Portrait Layout (1080x1920)
```
┌────────────────────────┐
│  Header                │
├────────────────────────┤
│                        │
│      Album Art 1       │
│                        │
├────────────────────────┤
│                        │
│    Track List 1        │
│  (with wrapping)       │
│                        │
├────────────────────────┤
│                        │
│      Album Art 2       │
│                        │
├────────────────────────┤
│                        │
│    Track List 2        │
│  (with wrapping)       │
│                        │
└────────────────────────┘
│  Buttons (smaller)     │
└────────────────────────┘
```

## Benefits of Portrait Layout

1. **More Vertical Space**: Taller displays allow longer track lists to be visible
2. **Larger Album Art**: Art can be wider without competing with track list
3. **Readable Track Names**: Wrapping prevents truncation of long titles
4. **Touch-Friendly**: Vertical scrolling is more natural on touchscreens
5. **Jukebox Aesthetic**: Traditional jukeboxes often had vertical orientations

## Performance Impact

Portrait versions have the **same performance characteristics** as their horizontal counterparts:
- `index-portrait.html` = same GPU load as `index.html`
- `index-lite-portrait.html` = same optimizations as `index-lite.html`

The layout changes (wrapping text, different flex direction) have **negligible performance impact** compared to the visual effects optimization.

## File Size Comparison

| File | Size | Notes |
|------|------|-------|
| index.html | 83 KB | Horizontal, full effects |
| index-lite.html | 81 KB | Horizontal, optimized |
| index-portrait.html | 83 KB | Portrait, full effects |
| index-lite-portrait.html | 81 KB | Portrait, optimized |

Portrait versions are the same size as horizontal versions (CSS changes are minimal).

## Compatibility

All portrait features work on the same browsers and systems as horizontal versions:
- Modern Chrome, Firefox, Edge, Safari
- Touch events for mobile/tablet browsers
- Keyboard navigation unchanged
- All Spotify API functionality identical

---

**Result**: Portrait versions provide an optimized vertical experience with wrapping track names, compact buttons, and reorganized layout perfect for 1080x1920 displays.
