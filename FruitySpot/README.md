# FruitySpot — Quick setup, usage and notes from developer


<img width="1280" height="720" alt="indieglo" src="https://github.com/user-attachments/assets/6b4e572e-c7b9-4fb2-930f-363043d3bcd1" />


FruitySpot is a small client-side web app that uses the Spotify Web API / Web Playback SDK to authorize with Spotify and control local playback from your browser. It leverages the assets from the Fruitbox v2 JaysIndieglo skin (https://github.com/chundermike/rpi-fruitbox-v2) and tries to recreate some of Fruitbox's functionaility via html while integrating with Spotify to source and stream tracks.
The migration was done via AI with only very, very minor manual tweaks of the created html. It's probably far from perfect but it works!

Summary
- You must paste your Spotify Client ID into the HTML (see the code snippet below).
- You do NOT need to add a redirect_uri to the HTML — the app builds it dynamically from the browser origin (e.g. window.location.origin). Register that runtime origin in your Spotify Developer Dashboard (for example: http://localhost:8000).

Paste your Client ID
Open `index.html` and replace the CLIENT_ID placeholder with your Spotify Client ID:
```js
const CLIENT_ID = 'REPLACE_WITH_SPOTIFY_API_CLIENT_ID';
```

Prerequisites
- Spotify Premium (required for playback via the Web Playback SDK)
- Spotify Developer account (create an app to get a Client ID)
- Python 3.x (or some sort of web server to serve files locally for development)

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
- From a command prompt/terminal, cd to where you placed the html file and its supporting assets and serve the folder locally:
  - macOS / Linux:
    ```
    python3 -m http.server 8000
    ```
  - Windows:
    ```
    py -3 -m http.server 8000
    ```
- Open in a browser: http://localhost:8000/index.html

Using the webpage (index.html)

1. The Spotify app needs to be running on your device or desktop (it may actually need to be playing a song, too).
2. Open the page in your browser (served as above).
3. Click the "Sign In" button to sign in with Spotify — you'll be redirected to Spotify and then back to the app.
4. After approval the app receives an access token and will show account/playback info.
5. Click on the album art in the lower right corner to access hidden buttons allowing you to connect to Spotify and load playlists by pasting their URLs. You can click on the album art again to re-hide the buttons. (Note that not all buttons are functional, but what does work is enough to replicate the jukebox experience.)
6. Select tracks by clicking on the song name or entering in track number via keyboard.
7. Looks best in fullscreen @ 1920x1080!
8. For a nice clean look, load a playlist of 100 songs by 50 distinct artists and ordered by artist name. You can use AI to help generate such a playlist.

Other Notes:

1. You can load a playlist with more than 100 songs and next/previous page buttons will appear allowing you to swap between pages. You can also use the left/right arrow keys on your keyboard to navigate between pages when pagination is active. Those buttons aren't very attractive and ideally some animation would be added when swapping pages.
2. Writing 2 artists per title strip is not formatted well and is sometimes hard to read. I haven't spent time enhancing that - the original goal was to mimic a 100-track vintage jukebox where title strips only contain a single artist.
3. Swapping betwen Spotify playback devices in the menu seems to kind of work? I haven't tested that funtionality too much,
4. The queue sometimes exhibits weird behavior. The queue is designed so that it will read in and display whatever's in your local Spotify app's queue - both "Next in queue" and "Next from queue". Adding songs from the web page should add songs to the bottom of "Next in queue". There's also a bug in the Spotify APIs that sometimes causes the queue to list the same song multiple times even though it's in your queue only once (or perhaps not at all?). But adding songs should still queue and playback correctly despite what you see in the webpage's queue list.
5. Feel free to open bugs or enhancements, but at this point the page is meeting my goals and AI often takes 2 steps back and 1 forward at this stage when making changes.
