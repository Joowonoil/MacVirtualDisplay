# Remote Setup Guide

Mac Virtual Display creates and manages the device-matched display on the Mac. It is not a streaming client or VPN. Complete the steps below once to build the full remote workflow.

## 1. Install the companion apps

### On the Mac

| App | Purpose | Download |
|---|---|---|
| Mac Virtual Display | Creates and restores the device-matched Mac display | [Official download](https://ramterstudio.com/mac-virtual-display/) |
| Sunshine | Captures, encodes, and streams the managed display | [Apple silicon DMG](https://github.com/LizardByte/Sunshine/releases/latest/download/Sunshine-macOS-arm64.dmg) · [All releases](https://github.com/LizardByte/Sunshine/releases) |
| Tailscale | Provides a private route to the Mac outside the home | [Download for macOS](https://tailscale.com/download/mac) |

### On Galaxy Fold or Android

| App | Purpose | Download |
|---|---|---|
| Artemis | Displays the stream and sends touch, keyboard, and pointer input | [Stable nonRoot game APK](https://github.com/ClassicOldSong/moonlight-android/releases/latest/download/artemis-nonRoot_game-release.apk) · [Release notes](https://github.com/ClassicOldSong/moonlight-android/releases/latest) |
| Tailscale | Connects the Android device to the same private network as the Mac | [Google Play](https://play.google.com/store/apps/details?id=com.tailscale.ipn) |

Use the **`artemis-nonRoot_game-release.apk`** build on a normal, non-rooted Galaxy device. Android may ask you to allow installation from the browser or file manager used to open the APK.

### On iPad

| App | Purpose | Download |
|---|---|---|
| Moonlight | Displays the stream and sends input from iPadOS | [App Store](https://apps.apple.com/app/moonlight-game-streaming/id1000551566) |
| Tailscale | Connects the iPad to the same private network as the Mac | [Download for iOS](https://tailscale.com/download/ios) |

Tailscale is optional when both devices can already reach each other on the same local network. It is recommended for access outside the home. Mac Virtual Display only reads Tailscale connection status; it does not install Tailscale, sign in, or control the VPN.

## 2. Prepare Sunshine on the Mac

1. Install and open Sunshine.
2. Allow the macOS permissions Sunshine requests, including **Screen Recording** and the input/accessibility permission needed for remote control.
3. Open the Sunshine Web UI at [`https://localhost:47990`](https://localhost:47990) on the Mac.
4. Create the Sunshine Web UI username and password when prompted.
5. Leave Sunshine available while completing the first client pairing.

The local Sunshine page uses HTTPS and may show a browser certificate warning because it is hosted by the Mac itself. Confirm that the address is exactly `localhost:47990` before proceeding.

## 3. Prepare the network

For local-only use, keep the Mac and client on a network where they can reach each other and use the Mac's local IP address.

For access outside the home:

1. Sign in to Tailscale on the Mac and client with the same account, or otherwise place both devices in the same tailnet.
2. Confirm that both devices show as connected.
3. Copy the Mac's Tailscale IPv4 address, normally in the `100.x.x.x` range.
4. Enter only that IP address in Artemis or Moonlight. Do not add `https://` or a port number.

Connect the host Mac by Ethernet whenever possible. This removes one wireless link from the streaming path and usually improves stability.

## 4. Create and pair the remote display

1. Open Mac Virtual Display and select the profile that matches the client.
2. Enable **Sunshine integration** if you want the app to coordinate Sunshine and select the managed display automatically.
3. Click **Turn On** and wait for the device-matched display to become active.
4. In Artemis or Moonlight, choose **Add PC manually** when the Mac is not discovered automatically.
5. Enter the Mac's Tailscale IP for remote use, or its local IP for local-only use.
6. Select the Mac. The client displays a four-digit PIN.
7. On the Mac, open Sunshine's Web UI, go to **PIN**, enter the code and a recognizable device name, then submit it.
8. Return to the client and open **Desktop**.

Create the managed display before connecting the streaming client. Virtual display identifiers can change whenever a display is recreated; Sunshine integration resolves the current display for you.

## Everyday connection order

1. Open Mac Virtual Display and select the profile that matches the client.
2. Turn on the virtual display.
3. If Sunshine integration is enabled, let Mac Virtual Display start or coordinate Sunshine and select the managed display.
4. Connect from Artemis or Moonlight.
5. When finished, turn off the managed display to restore the previous Mac display layout.

## Tested Galaxy Z Fold8 preset

The following Artemis preset was used successfully with the Fold profile:

| Artemis setting | Value |
|---|---|
| Video resolution | Custom `2448 × 1848` |
| Frame rate | `120 FPS` |
| Video bitrate | `65 Mbps` |
| Video codec | Prefer HEVC |
| Video frame pacing | Balanced |
| Video scale mode | Fit |
| Full screen | On |
| HDR | Off |
| Audio | Stereo |
| Play audio on PC | Off |
| Use Virtual Display | Off |
| Resolution Scale Factor | 100% |
| Auto Invert Resolution | Off |

`Use Virtual Display` is intended for compatible host-side virtual-display integrations. Leave it off when Mac Virtual Display has already created the Fold display on macOS.

Network conditions vary. If streaming is unstable, lower the bitrate first while keeping the native resolution and refresh rate.

## Touch and keyboard input on Galaxy Fold

Artemis trackpad-style input is convenient for desktop work:

- One-finger movement: move the pointer
- Tap: click
- Two-finger movement: scroll
- Two-finger tap: right-click
- Three-finger tap: show or hide the Android software keyboard

For text input, keep the Fold software keyboard in its English layout. Switch the input source on the Mac when typing Korean or another language. This lets the Mac input method compose the text from ordinary key events.

Directly sending precomposed Korean text from the Android keyboard may not work correctly with the macOS Sunshine host.

## Local and remote networking

Tailscale is not required when both devices can reach each other on the same local network. It is recommended for access from outside the home instead of exposing Sunshine through public port forwarding.

Keeping Tailscale available can also provide a consistent host address when a wired Mac and wireless client are not discovered automatically on the same router.

For a more stable stream:

- Connect the Mac to the router by Ethernet when possible.
- Use a strong Wi-Fi connection on the client.
- Check that Tailscale has a direct path when latency is unexpectedly high.
- Reduce bitrate before lowering resolution or frame rate.

## Clamshell workflow

Use this order before leaving the Mac unattended:

1. Connect the Mac to power and Ethernet.
2. Keep the physical display available while turning on the Fold or iPad profile.
3. Confirm that the managed display is active and Sunshine is streaming it.
4. Then turn off the physical monitor or leave the Mac in its tested clamshell arrangement.

If the Mac is closed and the physical monitor is unavailable, do not remotely turn off the only active managed display. Restore a physical display or open the Mac before removing it.

Clamshell and long-term headless behavior can vary by Mac model and macOS version. Test the complete state locally before relying on it away from home.

## Troubleshooting

### The stream opens on the wrong display

Turn the profile off and on again, then reconnect. If Sunshine integration is enabled, Mac Virtual Display will coordinate the current managed display. Display identifiers are not permanent across recreation.

### Artemis shows 60 FPS after selecting 120 FPS

Check Android or Samsung performance and game-optimization settings. Device-level optimization can limit an app to 60 Hz.

### Keyboard input does not reach the Mac

Open the Android software keyboard with a three-finger tap, select its English layout, and change the language on the Mac instead of sending composed text from Android.

### The connection is unstable

Confirm the host Mac is wired, check the client Wi-Fi or mobile connection, and reduce the Artemis bitrate from `65 Mbps` until the stream is stable.
