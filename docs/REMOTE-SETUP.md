# Remote Setup Guide

Mac Virtual Display creates and manages the device-matched display on the Mac. It is not a streaming client or VPN. A complete remote workflow uses separate companion apps:

| Role | Recommended app |
|---|---|
| Mac display management | Mac Virtual Display |
| Streaming host | [Sunshine](https://github.com/LizardByte/Sunshine) |
| Galaxy Fold / Android client | [Artemis](https://github.com/ClassicOldSong/moonlight-android) |
| iPad client | [Moonlight](https://moonlight-stream.org/) |
| Remote network outside the home | [Tailscale](https://tailscale.com/download) |

Sunshine and Tailscale are optional integrations. Mac Virtual Display does not install them, sign into them, or control the Tailscale account.

## Before connecting

1. Install and configure Sunshine on the Mac if you want to stream the display.
2. Install Artemis on the Galaxy Fold or Android device, or Moonlight on iPad.
3. For access outside the local network, connect the Mac and client to the same Tailscale network.
4. Connect the host Mac by Ethernet whenever possible. This removes one wireless link from the streaming path.

## Connection order

1. Open Mac Virtual Display and select the profile that matches the client.
2. Turn on the virtual display.
3. If Sunshine integration is enabled, let Mac Virtual Display start or coordinate Sunshine and select the managed display.
4. Connect from Artemis or Moonlight.
5. When finished, turn off the managed display to restore the previous Mac display layout.

Create the managed display before connecting the streaming client. Virtual display identifiers can change whenever a display is recreated; Sunshine integration handles the current managed display for you.

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
