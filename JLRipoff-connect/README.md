# JLRipoff (Spotify Connect version)


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
Since this is the Connect version, it does require a local Spotify device (run Spotify on your desktop, for example) and does support lossless.
<br>
<br>
Reference FruitySpot readme (https://github.com/SmedleyB/FruitySpot/blob/main/FruitySpot/README.md) for general usage.
<br>
<br>
You must edit these 2 lines as needed in index.html before running:


```
const CLIENT_ID = 'REPLACE_WITH_SPOTIFY_API_CLIENT_ID';
const redirectUri = "http://localhost:8000/";
```
<br>
<br>
<br>

## Seeing what's actually queued on your Spotify device

We added a simple way for you to peek at the queue that Spotify will actually play on your device. This is useful because the web app has its own "local" view of what you've loaded here, but Spotify keeps the definitive queue on your phone, PC, or other device.

What to expect
- Two queues:
  - App queue (the default you see in the page that pops up after inactivity or pressing "z"): this shows the tracks you loaded into the app and the order the app would like to play them, and can expand well beyond 20 tracks.
  - Spotify device queue (the secret link): this shows what Spotify itself has queued up on the device that's currently playing. This is the list Spotify will actually follow when it plays the next tracks.
- How to open the Spotify queue: click the small "QUEUED" number in the top-right of the screen. It's a little hidden on purpose — think of it as a quick peek into what your Spotify player is lined up to play next.
- Limit: Spotify only returns up to 20 upcoming tracks from the device queue. If you have more than 20 songs queued on Spotify, you will only see the first 20 items here. If you need to view more, open the Spotify app on your device.

Why there are two queues
- The app helps you build and manage a playlist-like "set" in the page (easy browsing, selecting, and grouping).
- The Spotify API does not offer fine queue management control. If it ever does in the future, we will definitely take advantage of it.
- Spotify’s queue is what the Spotify player will actually execute. Other Spotify clients (your phone, another browser, or someone sharing your account) can add or change items in that queue outside this app. Showing the Spotify device queue helps avoid confusion when the app’s list and Spotify’s list don't match.

What the special styling means
- Items that come from outside the app’s current set (for example, something you added from the Spotify mobile app) are shown with a subtle "not-in-set" highlight so you can tell which tracks were added elsewhere.

Quick troubleshooting
- "No active device" message: open Spotify on your phone/PC/tablet and play something so a device becomes active, then click the QUEUED number again.
- Missing items (more than 20): remember the 20-item limit — use the Spotify app to view the full queue.
- New items not appearing instantly: there can be a short delay before recently added songs show up here. Re-open the QUEUED view if things seem out of sync.
- Want to edit the queue (reorder/remove)? Spotify’s API doesn’t let us edit the server-side queue from the web app. To rearrange or remove queued songs, please use the Spotify app (or add them to a playlist managed in the app).


