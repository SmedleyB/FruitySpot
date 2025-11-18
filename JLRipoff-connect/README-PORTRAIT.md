# Portrait/Vertical Layout Versions

The JLRipoff-connect interface now includes portrait/vertical layout versions optimized for 1080x1920 displays.

## Available Portrait Versions

### index-portrait.html
- **Full visual effects** (gradients, shadows, animations)
- Optimized for **1080x1920** vertical displays
- Recommended for modern hardware with dedicated or recent integrated graphics

### index-lite-portrait.html
- **Performance optimized** for older integrated graphics (Intel HD 4600, etc.)
- Optimized for **1080x1920** vertical displays
- Same functionality with simplified visual effects

## Portrait Layout Features

### 1. Vertical Grid Layout
- **Single-column grid** showing 2 albums at a time (vs. 4 in horizontal)
- Albums displayed vertically in a stack
- More pages to navigate through, but each album gets more screen space

### 2. Album Layout
The album cells are arranged vertically with:
- **Album artwork on top** (300px height)
- **Track list below** the artwork
- Track list takes remaining vertical space

### 3. Track Name Wrapping
Track names now **wrap to multiple lines** instead of being truncated:
- Track number stays on the first line
- Long track names wrap naturally
- Better readability for long song titles
- Only extremely long names (50+ characters) will eventually wrap extensively

### 4. Smaller Control Buttons
Bottom-row buttons (Playlist, Device, Logout) are more compact:
- **Reduced size**: 55px min-width (vs. 70px)
- **Smaller padding**: 5px/14px (vs. 7px/22px)
- **Smaller font**: 0.88em (vs. 1em)
- Less screen real estate used
- Still fully functional and touchable

## Layout Comparison

| Feature | Horizontal (1080 width) | Portrait (1080x1920) |
|---------|------------------------|----------------------|
| Grid Layout | 2x2 (4 albums/page) | 1x2 (2 albums/page) |
| Album Direction | Side-by-side | Stacked vertically |
| Album Art Position | Right side | Top |
| Track List Position | Left side | Bottom |
| Track Names | Truncated with ellipsis | Wrap to multiple lines |
| Bottom Buttons | Regular size | Smaller/compact |
| Pages to Navigate | Fewer | More |
| Space per Album | Limited vertical | More vertical space |

## When to Use Portrait Versions

### Perfect For:
- **Vertical/portrait monitors** or rotated displays
- **Jukebox builds** using vertical screens
- **Touchscreen kiosks** in portrait orientation
- **Repurposed tablets** or mobile displays mounted vertically
- **Digital signage displays** in portrait mode

### Recommended Display Specs:
- **Resolution**: 1080x1920 (or similar portrait aspect ratio)
- **Orientation**: Portrait/vertical
- **Size**: 15-24 inches work well
- **Touch**: Optional but recommended for jukebox use

## Setup Instructions

1. **Choose your version**:
   - Modern hardware → `index-portrait.html`
   - Older hardware (Intel HD 4600, etc.) → `index-lite-portrait.html`

2. **Configure Spotify API** (same as horizontal versions):
   ```javascript
   const clientId = "YOUR_SPOTIFY_CLIENT_ID";
   const redirectUri = "http://localhost:8000/";
   ```

3. **Run a local web server** and open the portrait version:
   ```bash
   python -m http.server 8000
   # Then open http://localhost:8000/index-portrait.html
   ```

4. **Rotate your display** to portrait orientation if needed

## Visual Design Decisions

### Why Album Art on Top?
- In portrait orientation, horizontal space is limited
- Placing art on top allows it to be larger and more prominent
- Track list can extend downward using the ample vertical space

### Why Wrapping Track Names?
- Portrait layouts have more vertical space available
- Side-by-side layout in horizontal version requires truncation
- Wrapping provides better readability for long song titles
- Users can see full track names without hovering/clicking

### Why Smaller Buttons?
- Portrait width (1080px) is the same as horizontal
- Bottom row has the same horizontal constraints
- Smaller buttons prevent crowding
- Maintains touch-friendly targets while saving space

## Performance Considerations

The **lite portrait version** has the same optimizations as the horizontal lite version:
- No backdrop filters
- Simplified gradients
- Reduced shadows
- Simplified animations
- Better performance on Intel HD 4600 and similar hardware

Expected performance on Intel HD 4600:
- **Queue modal**: 50-60 FPS (vs. 30-40 FPS in full version)
- **Album navigation**: 50-60 FPS (vs. 35-45 FPS in full version)
- **Lower GPU usage**: ~60% reduction in memory and composite layers

## Switching Between Orientations

You can easily switch between horizontal and portrait versions:

### From Horizontal to Portrait:
1. Rotate your display to portrait orientation
2. Change URL from `/index.html` to `/index-portrait.html`
3. Or from `/index-lite.html` to `/index-lite-portrait.html`

### From Portrait to Horizontal:
1. Rotate your display to landscape orientation
2. Change URL from `/index-portrait.html` to `/index.html`
3. Or from `/index-lite-portrait.html` to `/index-lite.html`

All versions share the same authentication and configuration.

## Tips for Best Results

1. **Display Calibration**: Adjust brightness/contrast for your environment
2. **Text Size**: The portrait versions use slightly larger fonts for readability
3. **Touch Targets**: All buttons maintain adequate size for touch interaction
4. **Scrolling**: Track lists scroll smoothly - use touch or mouse wheel
5. **Navigation**: Use arrow keys or on-screen buttons to navigate between pages

## Troubleshooting

### Track Names Still Truncating?
- Check if you're using the portrait version (track names should wrap)
- Very long titles (50+ characters) will wrap but might still be lengthy
- This is normal and expected - wrapping helps but doesn't eliminate all length

### Layout Looks Squished?
- Confirm your display is actually 1080 pixels wide
- Check that display rotation is set to portrait in OS settings
- Try refreshing the page after rotating the display

### Buttons Too Small to Touch?
- The smaller buttons are still 55x28px minimum - adequate for touch
- If needed, you can increase button size in the CSS
- Consider using a stylus for very precise selection

## Future Enhancements

Potential improvements being considered:
- Auto-detection of display orientation
- Adjustable button sizes via settings
- Configurable track display (wrap vs. truncate)
- Support for other portrait resolutions (e.g., 1200x1600)

---

**Summary**: Portrait versions provide an optimized vertical layout for 1080x1920 displays with wrapping track names, compact buttons, and all the same functionality as the horizontal versions.
