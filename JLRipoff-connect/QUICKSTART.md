# Quick Start Guide - Performance-Optimized Version

This guide will help you get started with the performance-optimized version of JLRipoff-connect.

## Step 1: Determine Which Version You Need

### Use `index-lite.html` (Performance Version) if:
- ✅ You have Intel HD 4000-5000 series graphics
- ✅ You have older AMD integrated graphics (pre-Vega)
- ✅ You experience lag or stuttering with the original version
- ✅ Your device runs hot or fans spin up when using the app
- ✅ You're using a low-power device (older tablet, mini PC, etc.)

### Use `index.html` (Original Version) if:
- ✅ You have a dedicated graphics card (GTX 1050 or newer)
- ✅ You have modern integrated graphics (Intel Iris Xe, AMD Vega, Apple M1, etc.)
- ✅ Performance is smooth and you want maximum visual quality
- ✅ You don't experience any performance issues

### Not Sure? Try This Test:
1. Open the original `index.html`
2. Load a playlist and navigate through album pages
3. Press 'Z' to open the queue modal and let it auto-scroll
4. If you see choppy scrolling, lag, or frame drops → Use `index-lite.html`
5. If everything is smooth → Stick with `index.html`

## Step 2: Configure Your Spotify API Credentials

Both versions require the same setup:

1. Open your chosen file (`index.html` or `index-lite.html`) in a text editor
2. Find these lines near the top of the `<script>` section:
   ```javascript
   const clientId = "REPLACE_WITH_SPOTIFY_API_CLIENT_ID";
   const redirectUri = "http://localhost:8000/";
   ```
3. Replace `REPLACE_WITH_SPOTIFY_API_CLIENT_ID` with your Spotify Client ID
4. Adjust the `redirectUri` if you're using a different port or domain
5. Save the file

> **Note:** You need a Spotify Developer account and registered app to get a Client ID.
> See the main FruitySpot README for detailed instructions.

## Step 3: Run a Local Web Server

The app requires a web server to run (can't just open the HTML file directly).

### Option A: Python (easiest if you have Python installed)
```bash
# Navigate to the JLRipoff-connect directory
cd /path/to/FruitySpot/JLRipoff-connect

# Python 3
python -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000
```

### Option B: Node.js
```bash
# Install http-server globally (one time)
npm install -g http-server

# Run in the JLRipoff-connect directory
http-server -p 8000
```

### Option C: Live Server (VS Code Extension)
1. Install "Live Server" extension in VS Code
2. Right-click on your chosen HTML file
3. Select "Open with Live Server"

## Step 4: Open in Your Browser

1. Open your web browser
2. Navigate to: `http://localhost:8000/index-lite.html` (or `index.html`)
3. Click the "Login" button to authenticate with Spotify

## Step 5: Start Using the App

1. **Select a Device:** Click the "Device" button to choose your Spotify playback device
2. **Load a Playlist:** Click "Playlist" to load a Spotify playlist
3. **Browse Albums:** Use arrow keys or `<` `>` buttons to navigate
4. **Queue Songs:** Type the 4-digit code (e.g., `0101` for album 01, track 01)
5. **View Queue:** Press 'Z' or wait for inactivity to see the queue modal

## Switching Between Versions

You can easily switch between versions at any time:

1. Both files share the same configuration (edit one, copy to the other)
2. Just change the URL from `/index.html` to `/index-lite.html` (or vice versa)
3. Your Spotify authentication will work with both
4. All features are identical - only visual performance differs

## Performance Tips for Best Results

### For Both Versions:
- Close other browser tabs to free up resources
- Keep your Spotify app updated on your playback device
- Use a modern browser (Chrome, Edge, or Firefox recommended)

### For Lite Version Users:
- Consider reducing browser zoom to 90% for larger displays
- Close background applications to free up GPU resources
- If your system supports it, enable hardware acceleration in browser settings

### For Original Version Users:
- Enable GPU hardware acceleration in your browser for best performance
- Consider using fullscreen mode for immersive experience

## Troubleshooting

### Choppy Scrolling in Queue Modal
- **Solution:** Switch to `index-lite.html`
- The lite version has much simpler animations and effects

### Lag When Switching Album Pages
- **Solution:** Switch to `index-lite.html`
- The lite version has optimized transitions

### "No Active Device" Error
- **Solution:** Open Spotify on your phone, PC, or tablet and start playing something
- The app needs an active Spotify Connect device to work

### Playlist Won't Load
- **Solution:** Check your Spotify API credentials
- Make sure your Client ID is correct and the app is registered

### Visual Differences Between Versions
- **This is normal!** The lite version intentionally has simpler visuals
- Colors, layout, and functionality are identical
- The lite version just has less "glow" and "depth"

## Getting Help

- Check the main README files for detailed setup instructions
- Review OPTIMIZATION-DETAILS.md for technical information about the optimizations
- Review README-PERFORMANCE.md for more information about performance differences

## Enjoy!

You're all set! Enjoy your JLRipoff jukebox experience optimized for your hardware. 🎵
