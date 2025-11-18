# Complete Version Guide

This document provides a complete overview of all JLRipoff-connect versions and helps you choose the right one.

## Version Matrix

| File | Layout | Optimization | Display | Best For |
|------|--------|--------------|---------|----------|
| **index.html** | Horizontal (2x2 grid) | Full effects | Landscape | Modern hardware, desktop monitors |
| **index-lite.html** | Horizontal (2x2 grid) | Performance | Landscape | Intel HD 4600, older systems |
| **index-portrait.html** | Vertical (1x2 grid) | Full effects | Portrait (1080x1920) | Modern hardware, vertical displays |
| **index-lite-portrait.html** | Vertical (1x2 grid) | Performance | Portrait (1080x1920) | Older hardware, vertical displays |

## Quick Selection Guide

### Choose by Display Orientation

**Landscape/Horizontal Display?**
→ Use `index.html` or `index-lite.html`

**Portrait/Vertical Display?**
→ Use `index-portrait.html` or `index-lite-portrait.html`

### Choose by Hardware Performance

**Modern GPU (GTX 1050+, Intel Iris Xe, etc.)?**
→ Use regular version (`index.html` or `index-portrait.html`)

**Older GPU (Intel HD 4600, AMD pre-Vega, etc.)?**
→ Use lite version (`index-lite.html` or `index-lite-portrait.html`)

## Feature Comparison

### Horizontal Versions (index.html / index-lite.html)

**Layout:**
- 2×2 grid (4 albums per page)
- Albums displayed side-by-side
- Track list on left, album art on right
- Optimized for 1080px+ width displays

**Features:**
- Track names truncated with ellipsis (...)
- Standard button sizes (70px min-width)
- Compact page navigation (fewer pages)
- Traditional jukebox aesthetic

**Best For:**
- Desktop monitors (1920×1080, 2560×1440, etc.)
- Landscape-oriented displays
- Traditional horizontal setups
- Most common use case

### Portrait Versions (index-portrait.html / index-lite-portrait.html)

**Layout:**
- 1×2 grid (2 albums per page)
- Albums stacked vertically
- Album art on top, track list below
- Optimized for 1080×1920 displays

**Features:**
- Track names wrap to multiple lines
- Smaller button sizes (55px min-width, -21%)
- More pages but more space per album
- Vertical-friendly navigation

**Best For:**
- Rotated monitors in portrait mode
- Vertical touchscreen displays
- Tablet/kiosk setups in portrait
- Jukebox builds with vertical screens

## Performance Optimization Details

### Full Effect Versions (index.html / index-portrait.html)

**Visual Features:**
- Complex gradient backgrounds
- Multi-layer box-shadows with glow
- Backdrop blur filters
- CSS filter effects (brightness, saturate)
- Text shadows throughout
- Pulsing album art animations

**Performance:**
- GPU memory: ~200MB
- Paint operations: ~300 per frame
- Composite layers: ~45
- Target: 60 FPS on modern hardware

### Lite Versions (index-lite.html / index-lite-portrait.html)

**Optimizations:**
- Solid color backgrounds (no gradients)
- Single-layer shadows, smaller blur
- No backdrop filters
- No CSS filter effects
- Minimal text shadows
- Disabled animations

**Performance:**
- GPU memory: ~80MB (-60%)
- Paint operations: ~100 per frame (-65%)
- Composite layers: ~18 (-60%)
- Target: 50-60 FPS on Intel HD 4600

## Common Features (All Versions)

### Functionality
✅ Full Spotify Connect integration
✅ Playlist loading and management
✅ Device selection and control
✅ Queue viewing and management
✅ Playback controls (play, pause, next, prev)
✅ Keypad navigation (0-9, <, >, X)
✅ Keyboard shortcuts (arrow keys, Z for queue)
✅ Auto-refresh token management
✅ Inactivity queue display

### UI Elements
✅ Header with status display
✅ Album grid with navigation
✅ Bottom control panel
✅ Modal dialogs for playlists/devices
✅ Queue scroll modal
✅ Message notifications

## File Size

| File | Size | Percentage of Original |
|------|------|------------------------|
| index.html | 83 KB | 100% (baseline) |
| index-lite.html | 81 KB | 97.6% |
| index-portrait.html | 83 KB | 100% |
| index-lite-portrait.html | 81 KB | 97.6% |

*Performance optimizations reduce file size by ~2.4% due to simplified CSS*

## Documentation Reference

### Setup & Usage
- **QUICKSTART.md** - Getting started guide for all versions
- **README.md** - Main documentation with overview

### Performance Optimization
- **README-PERFORMANCE.md** - Performance version guide
- **OPTIMIZATION-DETAILS.md** - Technical optimization details
- **SUMMARY.md** - Optimization work summary

### Portrait Layout
- **README-PORTRAIT.md** - Portrait version guide
- **PORTRAIT-CHANGES.md** - Technical layout changes

## Configuration

All versions use identical configuration:

```javascript
const clientId = "YOUR_SPOTIFY_CLIENT_ID";
const redirectUri = "http://localhost:8000/";
```

Simply edit these values in your chosen HTML file.

## Migration Between Versions

### Switching Versions
1. All versions use the same Spotify authentication
2. No data is lost when switching
3. Configuration is per-file, so copy if needed
4. Just change the URL in your browser

### Examples:
- Landscape to portrait: `index.html` → `index-portrait.html`
- Optimize for performance: `index.html` → `index-lite.html`
- Both at once: `index.html` → `index-lite-portrait.html`

## Hardware Recommendations

### Minimum Requirements
- **CPU**: Any modern processor (2 cores+)
- **RAM**: 2GB minimum, 4GB recommended
- **Browser**: Chrome 90+, Firefox 88+, Edge 90+

### Display Requirements

**Horizontal Versions:**
- Min width: 1080px
- Min height: 720px recommended
- Aspect ratio: 16:9 or wider

**Portrait Versions:**
- Width: 1080px
- Height: 1920px recommended
- Aspect ratio: 9:16 or similar

### GPU Requirements

**Full Effect Versions:**
- Intel Iris Xe or newer
- GTX 1050 or newer
- AMD Vega or newer
- Apple M1 or newer
- Any modern dedicated GPU

**Lite Versions:**
- Intel HD 4000-5000 series
- Older AMD integrated graphics
- Lower-power mobile GPUs
- Budget systems
- Older dedicated GPUs

## Troubleshooting

### Performance Issues
**Problem**: Lag, stuttering, low FPS
**Solution**: Switch to lite version for your layout

### Display Issues
**Problem**: Layout looks wrong
**Solution**: Verify display resolution matches version (1080 width for all)

### Track Names
**Problem**: Want wrapping but using horizontal
**Solution**: Switch to portrait version

**Problem**: Don't want wrapping in portrait
**Solution**: Use horizontal version or modify CSS

### Button Size
**Problem**: Buttons too small in portrait
**Solution**: Modify `.cornerpanel .btn` CSS to increase size

## Summary

Choose your version based on:

1. **Display orientation** (horizontal vs. portrait)
2. **Hardware capabilities** (modern vs. older)
3. **Visual preference** (effects vs. performance)
4. **Use case** (desktop vs. jukebox vs. kiosk)

All versions provide the same great jukebox experience with full Spotify integration!
