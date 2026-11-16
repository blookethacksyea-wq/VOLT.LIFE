# VOLT LIFE

A 3D e-moto bikelife game that runs in the browser, with online multiplayer, an in-game phone (Clipcam, VoltFeed, Flashtalk, Music) and police chases.

This repository is the whole game. `volt-life-server.mjs` is the game and its multiplayer server in one file: it serves the game page at `/` and the multiplayer connection at `/ws`. There is nothing to install and nothing to build.

## Files

| File | What it is |
| --- | --- |
| `volt-life-server.mjs` | The game and the server, in one file |
| `package.json` | Tells Node and Render how to start it (`npm start`) |

## Run it on your own computer

Needs Node 18 or newer.

```
node volt-life-server.mjs
```

Then open http://localhost:8787. Use `PORT=3000 node volt-life-server.mjs` for another port.

## Host it on Render

1. Create a **Web Service** from this GitHub repository.
2. Runtime **Node**. Build command: leave empty (or `npm install`, which does nothing here). Start command: `npm start`.
3. Open the web address Render gives you. That page is the game. Riders open the Online menu and choose **Join the Global world** to meet each other; the server address is filled in for them.

Render's free tier sleeps when nobody is using it, so the first visit after a quiet period takes a little while. Rooms and posted clips live in memory and reset when the server restarts. A rider's progress is saved in their own browser.

## Update the game

1. In this repository on GitHub choose **Add file → Upload files**, drop in the new `volt-life-server.mjs`, and commit.
2. On Render open the service and choose **Manual Deploy → Deploy latest commit**.

## Spotify in the Music app (optional)

Riders can sign in to Spotify inside the game and play music from the phone. This needs:

- A free **Spotify developer app** (https://developer.spotify.com/dashboard). Add this address as its **Redirect URI**, exactly, with the slash at the end: `https://YOUR-GAME-ADDRESS/`
- Every rider needs a **Spotify Premium** account. While the Spotify app is in development mode, Spotify only allows up to 5 riders that you add under the app's User Management.
- Spotify sign-in only works when the game is opened from its web address, not from a downloaded copy of the game.

Riders can paste the app's **Client ID** into the Music app the first time. To skip that step for everyone, add an environment variable on Render named `SPOTIFY_CLIENT_ID` with the Client ID as its value. The Client ID is not a secret. The game never uses or stores a client secret.

Spotify's developer rules do not allow games, so Spotify could switch an app off. SoundCloud works as an embedded SoundCloud player, and the "My music" tab (the game's own tracks and files riders add) needs no account.
