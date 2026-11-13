# Security

## Reporting a vulnerability

Please do not post a vulnerability in public: not in an issue, a Discord channel or a stream chat.

Use the COMMS page on [radioraxxla.com](https://www.radioraxxla.com/), or send a direct message to a Radio Raxxla
admin in the Radio Raxxla Discord, and say only that you have a security report; leave the detail for the reply.
The **Security** tab of [EDSQT-releases](https://github.com/RadioRaxxla/EDSQT-releases/security) (**Report a vulnerability**)
is a private route as well, and goes to the maintainer only.

You can expect an acknowledgement within a few days. A fix ships as a normal numbered release, with the cause
described in `CHANGELOG.md`.

Only the latest version is supported. EDSQT tells you when a newer build is ready, and updating keeps your settings
and your pairing.

---

## Code signing

EDSQT is not code signed yet. Windows shows *"Windows protected your PC"* for any unsigned program it has not seen
downloaded often. It is a reputation check, not a detection: **More info, then Run anyway**. The warning fades as
more people install a build and returns with each new release.

---

## What the app does on your PC

- **It reads the game's files and writes nothing to them.** The journal, `Status.json` and your bindings in your
  Saved Games and game settings folders are opened read-only.
- **Its own data** is kept in `%APPDATA%\EDSQT` (settings and the pairing) and `%LOCALAPPDATA%\RadioRaxxla\EDSQT`
  (the window's data), not in the program folder.
- **It listens on your own PC only.** The window and the stream page for OBS are served on `127.0.0.1`, which
  nothing outside your PC can reach. Every other connection is an outbound HTTPS request that the app starts.
- **Updates are installed only when you choose.** A newer build is downloaded in the background and kept only if:
  - the version file carries a valid signature (the app holds the public key; the private key stays on the build
    machine), and names EDSQT;
  - the download's size and SHA-256 match the signed version file, checked again just before it runs.
  It runs only when you press Install. The signature is separate from Windows code signing, which EDSQT does not
  have yet (above).
- **Discord.** Rich Presence talks only to the Discord app on your own PC. Voice nets and posts are done by the
  EDSQT bot in your squadron's own Discord server; EDSQT on your PC never holds a bot token.
- **Frontier sign-in**, used to import the game's squadron roster, happens on your PC. The sign-in is used once and
  is never sent to Radio Raxxla.
- **Credentials.** The pairing with your squadron is stored in `settings.json` in `%APPDATA%\EDSQT`. Do not attach
  it to a bug report. A key you add for another service is kept on your PC and sent only to that service.

## What leaves your PC

Only to your own squadron, through the Radio Raxxla service, and only once you have paired:

- **Your Card** and session summaries. Every part is shared by default, with a switch for each on the Card page.
- **What you are doing and where** (system and station) while the game is running, with a switch to stop it.
  Never in streamer mode.
- **What you do in the squadron**: answers to Ready Checks, pings and orders, op sign-ups, task progress.

Never: credits, carrier finance, your FID, bank transfers, or squadron and squadron-leader chat. Settings has
**Forget me**, which deletes your card, history and links from the squadron's records.

Nothing is sent before you pair. Solo use sends nothing.
