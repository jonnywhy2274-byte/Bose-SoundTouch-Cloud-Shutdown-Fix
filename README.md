# Bose SoundTouch Cloud Shutdown Fix: Controller Pro, Controller Cloud & Controller Cube

On May 6, 2026, Bose permanently shut down the cloud servers powering the SoundTouch ecosystem. This repository serves as the official documentation and resource hub for the **Controller Pro** ecosystem—a complete local software, instant cloud bridge, and turnkey hardware suite designed to permanently rescue orphaned Bose SoundTouch speakers.

---

## 🏗️ The 3-Pillar Ecosystem

Whether you want a fast standalone Wi-Fi remote with direct internet radio out of the box, an instant 60-second cloud bridge with zero extra hardware, or a 100% offline local server with zero ongoing fees, the ecosystem is structured into three clear tiers:

### 1. 📱 Controller Pro (Standalone Mobile App — v9.2.3)
The universal command center for iOS, iPadOS, and Android (£3.49 / $4.49 one-time purchase, zero subscriptions). Used completely on its own without any server or extra hardware, **Controller Pro** acts as a fast, 100% local Wi-Fi remote featuring:
- **NEW Direct Wi-Fi Internet Radio (No Bluetooth Needed!):** Unlocks the speaker's internal UPnP AVTransport renderer on port 8091 to stream thousands of live global radio stations directly from your router over Wi-Fi—meaning zero Bluetooth audio compression, zero phone battery drain, and full Wi-Fi radio restored even to 1st-Generation (Series I) SoundTouch 20, 30, and Wave systems that lack Bluetooth hardware.
- **Smart Hybrid Audio Fallback:** Automatically detects protected broadcaster stream formats within 2 seconds and seamlessly bridges audio via AirPlay or Bluetooth so you never hit a dead station.
- **6 In-App Presets & Unlimited Favourites:** Save open web radio stations and local media directly to the 6 preset buttons on the app dashboard, plus store unlimited station Favourites.
- **Multi-Room Zone Mixer & One-Touch Scenes:** Group speakers on the fly, sync master volumes, control existing Left/Right stereo pairs, and deploy whole-house audio scenes with a single tap.
- **Surround Sound Calibration Desk:** Dedicated local acoustic mixer for SoundTouch 300 soundbars and Lifestyle home cinema systems to fine-tune center channel, rear surrounds, bass module, and treble.
- **Expanded 1,000-Item NAS / DLNA Browser & Source Control:** Browse up to 1,000 tracks or folders per directory on previously mounted NAS drives (Synology, FRITZ!Box, Plex) and switch seamlessly between AUX, TV/HDMI, Spotify Connect, AirPlay, and Bluetooth.
- **Privacy-First & 10 Native Languages:** Zero telemetry or ad trackers, with instant in-app switching across English, German, French, Spanish, Italian, Portuguese, Tagalog, Chinese, Japanese, and Arabic (RTL).

**Download the Standalone App:**
- 🍎 **iOS / iPadOS:** [Download on the Apple App Store](https://apps.apple.com/gb/app/controller-pro-for-soundtouch/id6762059088)
- 🤖 **Android:** [Download on Google Play](https://play.google.com/store/apps/details?id=com.john.soundtouch&pcampaignid=web_share)

---

### 2. ☁️ Controller Cloud (60-Second Zero-Hardware Rescue — *Now Live!*)
Want your 6 physical preset buttons on top of the speaker working with your phone switched off—without plugging a box into your router or flashing a Raspberry Pi? **Controller Cloud** is a dedicated 24/7 hosted Marge & BMX bridge that links to your speakers over Wi-Fi in under 60 seconds:
- **All 6 Physical Preset Buttons Restored:** Press physical buttons 1–6 directly on your speaker or Bose remote to play saved radio stations and NAS music—even when your phone is off.
- **Native TuneIn Directory & Live HLS Transcoding:** Stream 100,000+ live stations and custom raw audio URLs (`.mp3`, `.aac`, `.m3u8` HLS) directly on the speaker hardware with full OLED display metadata, live `ffmpeg` HLS-to-MP3 transcoding, and on-the-fly SSL decryption.
- **Mount New NAS Drives & Create Stereo Pairs:** Pair and index brand-new SMB and UPnP/DLNA music libraries (`STORED_MUSIC`) and bond two SoundTouch 10 speakers into a true Left/Right stereo pair with L/R balance control.
- **Whole-Household Auto-Sync:** One household license supports unlimited SoundTouch speakers on your home network and automatically syncs presets, recents, and NAS drives across up to 8 phones and tablets.
- **Automatic Power-Cycle Recovery:** Switch your speakers off at the wall overnight—your physical presets and stations reconnect automatically every morning.

**Start Your Free Controller Cloud Trial:**
- ☁️ **Try Free for Up to 14 Days:** Includes a **14-day free trial** on Annual (£14.99/yr) or **7-day free trial** on Monthly (£1.69/mo). **[Start Your Free Trial via Lemon Squeezy](https://controllerpro.lemonsqueezy.com/checkout/buy/65f5903f-ad0e-4844-bfc6-7974c963f276)** | **[Compare on controllerpro.app](https://controllerpro.app)**

---

### 3. 🧊 Controller Cube (100% Offline Turnkey Hardware & DIY Master OS)
Prefer 100% local, offline operation with zero subscriptions forever? Running silently on your home LAN, the **Controller Cube** emulates the retired `marge` and `bmx` servers locally to unlock the exact same hardware-level features as Controller Cloud (Physical Presets 1–6, Native TuneIn with Live HLS `.m3u8` Transcoding & HTTPS Audio Proxy, Smart NAS Injector, and ST-10 Left/Right Stereo Pairing).

**Choose Your Offline Controller Cube Deployment:**
- 🛒 **Controller Cube OS (DIY Raspberry Pi, NanoPi, Docker & Home Assistant — £19.99 One-Time):** Flash our Master OS image (`.img.xz`) to your own Raspberry Pi 3B/4/5 or NanoPi NEO3 Plus, or run it natively inside Home Assistant / Docker with a single lifetime hardware-locked license key. **[Get Instant Digital Access via Lemon Squeezy](https://controllerpro.lemonsqueezy.com/checkout/buy/b4aff15b-e904-43e5-ada9-dd7320981eaa)**
- 🚀 **Controller Cube (Turnkey Aluminum Hardware Appliance — £85 One-Time):** Pre-flashed, plug-and-play industrial aluminum node that connects straight to your Wi-Fi router via Ethernet. **[Order on Indiegogo](https://www.indiegogo.com/projects/controllerpro/controller-pro-rescue-your-bose-soundtouch-system)** | **[Official Website (controllerpro.app)](https://controllerpro.app)**

---

## ⚡ 100% Wireless Zero-Touch Speaker Adoption (v9.2.3+)
USB thumb drives and manual SSH/Telnet terminal commands are officially retired.

**For Controller Cloud (60 Seconds · Zero Hardware):**
1. Open the **Controller Pro** app and go to **Settings (Gear Icon) > Ecosystem & Cloud Upgrades**.
2. Paste your **Controller Cloud License Key** into **Option 1: Controller Cloud** and tap **Activate** (your discovered speaker roster stays intact on screen automatically).
3. Tap the **Speaker Icon (top-left) > Network & Speakers**, and toggle ON **Auto-Link Speakers** (or tap **Link** next to each speaker).

**For Local Controller Cube / DIY Cube OS:**
1. Plug your **Controller Cube** into your router via Ethernet (or boot **Controller Cube OS** on your Pi / Home Assistant server).
2. Open the **Controller Pro** app on your phone or tablet.
3. Tap the **Speaker Icon (top-left) > Network & Speakers**, and toggle ON **Auto-Link Speakers** to bind your speakers over Wi-Fi in seconds.

---

## 📖 Documentation & Setup Guides
- 🌐 **Official Website & Capabilities Matrix:** [controllerpro.app](https://controllerpro.app)
- 💬 **Official Reddit Community & Support Hub:** [r/ControllerProandCube](https://www.reddit.com/r/ControllerProandCube/)
- 📖 **Primary User Manual:** [Google Sites Manual](https://sites.google.com/view/controller-pro-user-manual/home)
- 📖 **Controller Cube Manual Mirror:** [Controller Cube Web Manual](https://jonnywhy2274-byte.github.io/controller-pro-manual/)
- 🎥 **Video Tutorials & Demo:** [Official YouTube Playlist](https://www.youtube.com/playlist?list=PLGSxQe_HudUg)
- 🗂️ **Site Info for Directories (PAD Spec):** [Controller Pro PAD XML](https://controllerpro.app/controller-pro-pad.xml)

---
*Engineered in London by John Why. Zero telemetry. Built for the music.*
