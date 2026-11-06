# Releases

Downloadable builds of my projects: Android apps and a Linux desktop game.
Each project has its own release with full notes, install steps and a SHA-256
checksum. This repository holds the builds only; there is no source code here.

| Project | Version | Platform | Download |
| --- | --- | --- | --- |
| [ZeroGrid](#zerogrid) | 1.0.0 | Android 7.0+ | [ZeroGrid-1.0.0-release.apk](https://github.com/MeeLn/releases/releases/download/zerogrid-v1.0.0/ZeroGrid-1.0.0-release.apk) |
| [ALTKit](#altkit) | 0.6.1 | Android 8.0+ | [ALTKit-0.6.1-release.apk](https://github.com/MeeLn/releases/releases/download/altkit-v0.6.1/ALTKit-0.6.1-release.apk) |
| [AttendEase](#attendease) | 1.0.0 | Android 7.0+ | [AttendEase-1.0.0-release.apk](https://github.com/MeeLn/releases/releases/download/attendease-v1.0.0/AttendEase-1.0.0-release.apk) |
| [AttendEase Legacy](#attendease-legacy) | 1.0 | Android 5.0+ | [Legacy_AttendEase.apk](https://github.com/MeeLn/releases/releases/download/attendease-legacy-v1.0/Legacy_AttendEase.apk) |
| [DashLeapster](#dashleapster) | 1.0.0 | Linux x86_64 | [DashLeapster-linux-x86_64.tar.gz](https://github.com/MeeLn/releases/releases/download/dashleapster-v1.0.0/DashLeapster-linux-x86_64.tar.gz) |

All releases: [github.com/MeeLn/releases/releases](https://github.com/MeeLn/releases/releases)

---

## ZeroGrid

**Air-gapped file transfer.** Moves a file between two phones with no network at
all: the sender plays the file as a stream of QR codes, and the receiver reads
them with its camera. The release build requests no INTERNET permission, so
nothing leaves the two devices.

- Any file up to 256 MB, split into fountain-coded frames (LT, Robust Soliton):
  any large-enough set of frames rebuilds the file, in any order
- Three speeds: STABLE (15 fps), BALANCED (24 fps, default), FAST (30 fps)
- The rebuilt file is verified with SHA-256 before it is saved
- Offline audit on start (Wi-Fi, Bluetooth, mobile data, camera); 2× font scale
  and TalkBack support

| | |
| --- | --- |
| Release | [zerogrid-v1.0.0](https://github.com/MeeLn/releases/releases/tag/zerogrid-v1.0.0) |
| Package | `com.zerogrid.app` |
| Requires | Android 7.0+ (API 24), target SDK 36 |
| Permissions | Camera, Vibrate; read-only network/Wi-Fi state (offline audit), legacy Bluetooth (API ≤ 30 only) |
| SHA-256 | `6a0ed69ff20c6508a6267041b4113374259566081b511e5f162edc6f8db06a27` |
| Size | 68,862,311 bytes |

## ALTKit

**Android utility suite.** Scanner, network tools, notes, a live wallpaper studio
and everyday tools, behind an optional app lock, with a hidden Super User area.

- App lock: PIN, password, pattern, fingerprint/face; secrets stored only as
  salted PBKDF2 hashes, with a growing wait after repeated wrong tries
- QR/barcode scanner, Wi-Fi and Bluetooth tools, notes with folders and images
- Live wallpaper slideshow with fade, slide and zoom transitions
- Compass, flashlight brightness (Android 13+), sound meter, unit converter,
  in-app browser, file cleaner
- Tested at 2× font size with TalkBack; looping animations respect
  “Remove animations”

| | |
| --- | --- |
| Release | [altkit-v0.6.1](https://github.com/MeeLn/releases/releases/tag/altkit-v0.6.1) |
| Package | `com.altkit.app` |
| Requires | Android 8.0+ (API 26), target SDK 36 |
| Permissions | Camera, Microphone, Internet + network/Wi-Fi state, Nearby Wi-Fi/Bluetooth and Location (scanning only, flagged neverForLocation), Biometric, Set wallpaper, Write settings |
| SHA-256 | `a08a8b2b03b84e02f42f3907c71e9e5c09c5c8cf9122acc2e30f301e3837aeb4` |
| Size | 75,663,695 bytes |

## AttendEase

**Face-recognition attendance.** Class attendance on a single Android phone or
tablet: an admin sets up departments and courses and approves accounts, teachers
mark students present, and students check in with Face ID. Everything is stored
on the device; there is no server and no account outside the app.

- Role-based flows for admin, teacher and student
- On-device Face ID: CameraX + ML Kit face detection + MobileFaceNet
  embeddings (LiteRT / TensorFlow Lite)
- Duplicate attendance prevented per student, course and date
- SQLite storage; passwords as salted PBKDF2-SHA256 hashes

| | |
| --- | --- |
| Release | [attendease-v1.0.0](https://github.com/MeeLn/releases/releases/tag/attendease-v1.0.0) |
| Package | `com.attendease.app` |
| Requires | Android 7.0+ (API 24), target SDK 36 |
| Permissions | Camera (Face ID); network state |
| SHA-256 | `049dfdec79ba640186b605c2bd762537f1d36f00889e3df40663421b93aeb74a` |
| Size | 105,931,552 bytes |

## AttendEase Legacy

**The original native Android build** of AttendEase (Java + Gradle KTS),
preserved for reference before the Flutter rewrite. Archived: no further
updates, bug fixes or security patches. Use AttendEase 1.0.0 for real use; the
two have different package names, install side by side and don't share data.

| | |
| --- | --- |
| Release | [attendease-legacy-v1.0](https://github.com/MeeLn/releases/releases/tag/attendease-legacy-v1.0) |
| Package | `com.example.loginscreen` |
| Requires | Android 5.0+ (API 21), target SDK 34 |
| Permissions | Camera, read/write external storage, network state |
| SHA-256 | `97e51a893dda5dbce63fa5ef640b8c5688624d150da6e2c706100d02fd00d2d0` |
| Size | 101,731,779 bytes |

## DashLeapster

**A 2D endless runner** written in C++17 with SDL2. Guide a box through an
endless factory, avoid the red boxes and try to beat the saved high score.
Prebuilt for Linux x86_64: no compiler, CMake or source checkout needed.

```sh
tar xzf DashLeapster-linux-x86_64.tar.gz
cd DashLeapster
./dashleapster        # or ./install.sh for a desktop entry and a launcher
```

Needs the SDL runtime libraries (Debian, Ubuntu, Kali):

```sh
sudo apt install libsdl2-2.0-0 libsdl2-image-2.0-0 libsdl2-ttf-2.0-0 libsdl2-mixer-2.0-0
```

| | |
| --- | --- |
| Release | [dashleapster-v1.0.0](https://github.com/MeeLn/releases/releases/tag/dashleapster-v1.0.0) |
| Requires | x86_64, glibc 2.34+, libstdc++ with GLIBCXX_3.4.32 |
| Controls | Space jump · ↑ flip gravity · ↓ reset gravity · F11 fullscreen |
| SHA-256 | `8ea5c49bccf8f92f97b09273f574d59cd2235b2a174f06aff46666a1ea591caa` |
| Size | 25,086,433 bytes |

Linux only; a Windows package is not included.

---

## Installing an APK

1. Download the `.apk` on your phone (or copy it over).
2. Open it and allow installation from unknown sources when prompted.
3. Play Protect may warn because these builds are self-signed and not
   distributed through Google Play; choose **Install anyway**.

## Verifying a download

Compare the file's SHA-256 with the value listed above (and in its release notes):

```sh
sha256sum ZeroGrid-1.0.0-release.apk                       # Linux
shasum -a 256 ZeroGrid-1.0.0-release.apk                   # macOS
```

```powershell
Get-FileHash .\ZeroGrid-1.0.0-release.apk -Algorithm SHA256   # Windows
```

If the values don't match, don't install the file; download it again.

## License

© 2026 Milan Raut. All builds are provided as-is, without warranty. Bundled
open-source libraries keep their own licenses (see each app's in-app notices,
and each release's notes).
