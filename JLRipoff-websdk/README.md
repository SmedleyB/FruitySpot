# JLRipoff (Spotify Web SDK version)


<img width="1920" height="1080" alt="Screenshot 2025-11-14 at 9 28 18 AM" src="https://github.com/user-attachments/assets/1a9cfc6a-daa8-4d04-9f0d-de4ef7528e9b" />
<img width="1544" height="860" alt="Screenshot 2025-11-14 at 9 30 33 AM" src="https://github.com/user-attachments/assets/ee746096-6373-4afb-8a00-daeecfab0724" />
<br>
<br>
<br>
Have you seen JukeLab (https://www.jukelab.com/)?<br>
It's a very cool jukebox-inspired Spotify frontend. I told AI to create something like it and then worked through about 100 iterations tweaking that.
<br>
<br>
JLRipoff lets you pick a Spotify playlist against which it will read the first 100 entries, find all the distinct albums represented, and then build a paginated CD-Jukebox style display of those albums.
<br>
Only the first 25 tracks are listed on each album so we can maintain readability and avoid ugliness.<br>An attractive queue display will pop up after inactivity (you can also hit "z" to invoke the queue immediately).
<br>
Since this is the Web SDK version, it does not require a local Spotify device and instead does all playback through the browser. But streaming through the browser via Web SDK also means no lossless output.
<br>
<br>
Reference FruitySpot readme (https://github.com/SmedleyB/FruitySpot/blob/main/FruitySpot/README.md) for general usage.
<br>
<br>
## Available Versions

This folder contains **four** versions of JLRipoff to suit different needs:

### Standard Versions
- **index.html** - Full desktop layout (1×3 grid) with all visual effects and animations
- **index-portrait.html** - Portrait-optimized layout (2×2 grid) with vertical album cards, touch-friendly footer, and configurable cover art sizing

### Lite (Performance-Optimized) Versions
- **index-lite.html** - Desktop layout optimized for lower-end devices (simplified visuals, better performance)
- **index-lite-portrait.html** - Portrait layout with performance optimizations

**Key differences:**
- **Portrait versions** use a 2×2 grid (4 albums per page) with vertical album cards (cover art on top, tracks below). The footer has a two-row design with larger buttons for better touch targeting. Cover art height is configurable via CSS variable `--cover-height` (default 240px).
- **Lite versions** have simplified gradients, shadows, and removed visual effects (backdrop-filter, text-shadow, blur) for better rendering performance on lower-end devices.

You must edit these 2 lines as needed in your chosen version before running:


```
const CLIENT_ID = 'REPLACE_WITH_SPOTIFY_API_CLIENT_ID';
const redirectUri = "http://localhost:8000/";
```



