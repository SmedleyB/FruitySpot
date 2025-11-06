# FruitySpot — Quick setup & usage

FruitySpot is a small client-side demo that uses the Spotify Web API / Web Playback SDK to authorize with Spotify and control playback from your browser.
The migration was done via AI with only very, very minor manual tweaks of the created html. It's probably far from perfect but it works!

Summary
- You must paste your Spotify Client ID into the HTML (see the code snippet below).
- You do NOT need to add a redirect_uri to the HTML — the app builds it dynamically from the browser origin (e.g. window.location.origin). Register that runtime origin in your Spotify Developer Dashboard (for example: http://localhost:8000).

Paste your Client ID
Open `index.html` and replace the CLIENT_ID placeholder with your Spotify Client ID:
```js
const CLIENT_ID = 'YOUR_SPOTIFY_CLIENT_ID_HERE';
```

Prerequisites
- Spotify Premium (required for playback via the Web Playback SDK)
- Spotify Developer account (create an app to get a Client ID)
- Python 3.x (to serve files locally for development)

Register redirect origin
- In the Spotify Developer Dashboard, add the runtime origin you will use as a Redirect URI:
  - For local testing: `http://localhost:8000` (or `http://127.0.0.1:8000`)
  - The redirect URI used at runtime must exactly match one registered in the dashboard (scheme, host, port, trailing slash).

Download & run
- Clone or download the repo:
  ```
  git clone https://github.com/SmedleyB/FruitySpot.git
  cd FruitySpot
  ```
- Serve the folder locally:
  - macOS / Linux:
    ```
    python3 -m http.server 8000
    ```
  - Windows:
    ```
    py -3 -m http.server 8000
    ```
- Open: http://localhost:8000/index.html

Using the webpage (index.html)
1. Open the page in your browser (served as above).
2. Click the "Sign In" button to sign in with Spotify — you'll be redirected to Spotify and then back to the app.
3. After approval the app receives an access token and will show account/playback info.
4. Click on the album art in the lower right corner to access hidden buttons allowing you to connect to Spotify and load playlists by pasting their URLs. (Note that not all buttons are functional, but what does work is enough to replicate the jukebox experience.)
5. Select tracks by clicking on the song name or entering in track number via keyboard.
6. Looks best in fullscreen @ 1920x1080!
7. For a nice clean look, load a playlist of 100 songs by 50 distinct artists and ordered by artist name. You can use AI to help generate such a playlist.
