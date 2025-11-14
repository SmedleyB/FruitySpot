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
You must edit these 2 lines as needed in index.html before running:


```
const CLIENT_ID = 'REPLACE_WITH_SPOTIFY_API_CLIENT_ID';
const redirectUri = "http://localhost:8000/";
```



