# outbreak-launcher
Windows launcher project for the Outbreak Final Edition Minecraft modpack.
# Outbreak Launcher

Outbreak Launcher is an independent Windows desktop launcher project for the "Outbreak Final Edition" Minecraft Java Edition modpack. It provides a themed interface with customizable media and a gallery intended to reflect the player's in-game progress.

## Development status

This project is under active development. The desktop interface and local gallery foundation have been implemented. The actual Minecraft installation and game launch engine are not yet integrated.

Microsoft sign-in integration has been implemented in the prototype, but it has not yet completed end-to-end testing with a registered application and a real account. Minecraft API access approval is being sought. This page describes the project; it is not a finished release announcement.

## Features

- Windows desktop interface with a left-hand menu and randomized artwork on the right.
- Custom OGG background music loaded from a local folder.
- An optional introduction video that can be skipped with Escape.
- Gallery sections for characters, achievements, and creatures.
- Separate local player profiles and a JSON progress interface for future integration with the modpack.
- Microsoft account management and an independent local/offline profile mode in the prototype.

The current modpack target is Minecraft Java Edition 1.21.1 with NeoForge 21.1.230. 
## Purpose of Microsoft and Minecraft authentication

The intended online authentication flow is:

1. The player signs in on Microsoft's official website using the device authorization flow.
2. The launcher obtains the corresponding Xbox identity and Minecraft session.
3. The launcher checks Minecraft Java Edition entitlement and retrieves the player's Minecraft profile, including their name and UUID.
4. A future game launch integration will use the authenticated session to launch the game for eligible players.

The requested Microsoft scopes are `XboxLive.signin` and `offline_access`. The latter allows session renewal; it is separate from the launcher's local/offline profile feature.

Local/offline profiles do not create a Microsoft or Minecraft authenticated session and do not provide access to servers that require official account authentication.

## Account data

The launcher does not ask for or collect Microsoft account passwords. Sign-in takes place on Microsoft's website in the player's browser.

The current implementation stores saved authentication credentials locally using Electron safeStorage with Windows-provided encryption. It does not fall back to saving plaintext credentials when encryption is unavailable. Players can remove their saved login from the account management interface.

Gallery progress is stored locally and separately for each player profile. The prototype has no project-operated account backend or cloud progress service.

## About the project

Outbreak Launcher is an independent project and is not an official Minecraft or Microsoft product. Minecraft and Microsoft names belong to their respective owners.
