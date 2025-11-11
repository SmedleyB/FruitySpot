# Nickel Player


<img width="1280" height="720" alt="np" src="https://github.com/user-attachments/assets/0fa73d2a-9490-47f3-9eb1-31c042ccba29" />


I asked Google Gemini to make a web-based Spotify front end that resembles a classic jukebox and this is what it created and refined over many iterations. I guess Gemini is a vaporwave aestetic fan.

Overall functionaility and usage is the same as FruitySpot, and you can follow the same setup instructions detailed in the FruitySpot readme @ https://github.com/SmedleyB/FruitySpot/blob/main/README.md. Just serve up the NickelPlayer folder and files instead.

### Nickel Player specific notes:

1. There are seperate versions for horizontal and vert layouts. I tested on 1920x1080 and 1200x1600 but higher resolutions should render attractively, too.
2. No pre-editing of the .html is needed. The page will prompt for Spotify client ID and playlist link.
3. Multiple pages are NOT supported. The horizontal version will load only the first 100 tracks from the playlist and vertical the first 96.
4. If you try to enter the track numbers very quickly via keyboard, it may add the same track more than once to the queue. Wait a couple seconds between typing selections.
5. The track number entry via keyboard does not timeout but you can backspace out what you typed.
6. Nickel Player does not interact with the Spotify queue in the same way as FruitySpot. Nickel Player does not display existing songs from the Spotify app's queue, rather it shows only those added via the web page and should remove them from the displayed queue once played.
