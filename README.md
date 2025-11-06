
# FruitySpot — Quick setup

FruitySpot is a small client-side demo that uses the Spotify Web API / Web Playback SDK to recreate a Fruitbox jukebox skin in a web browser and pulls songs from a Spotify playslist.

Important: you must paste your Spotify Client ID into the HTML. You do NOT need to paste or define a redirect_uri in the HTML — the app builds that dynamically from the browser location (e.g. window.location.origin).

Quick edit
1. Open the main HTML (e.g. `index.html`) and replace the CLIENT_ID placeholder with your Spotify Client ID:
```js
const CLIENT_ID = 'YOUR_SPOTIFY_CLIENT_ID_HERE';
```
2. Do NOT add a hard-coded redirect URI in the HTML. Register the runtime origin you will use (for example `http://localhost:8000`) in your Spotify Developer Dashboard — the app uses the current origin as the redirect URI.

Serve locally (for testing)
- From the project folder:
  - macOS / Linux:
    ```
    python3 -m http.server 8000
    ```
  - Windows:
    ```
    py -3 -m http.server 8000
    ```
Open http://localhost:8000 (or your chosen port).

Prereqs
- Spotify Premium (required for playback)
- Spotify Developer account (create an app to get a Client ID)
- Python 3.x (to serve files locally)

That's it — paste your Client ID, register your local origin in the Spotify Dashboard, and run the local server.
