<!-- publish.yml writes this file at each nightly (scripts/nightly-notes.py, readme): change it there -->
# ScarletNX nightly builds

Builds of [ScarletNX](https://github.com/scarletnx/ScarletNX), published by its [publish workflow](https://github.com/scarletnx/ScarletNX/blob/main/.github/workflows/publish.yml):

- **Nightlies**, `nightly-<day>-<commit>`: one a day, of `main` as the first scheduled build of the day (UTC) that built everywhere. Every nightly stays here, and [the latest](https://github.com/scarletnx/nightly/releases/latest) is always the newest. When a day has none, the newest says at its top which build failed.
- **Pull requests**, `pr-<number>`: an open pull request's builds, replaced at each push to it. They are deleted when it closes without a merge, or once merged, when a nightly has its change. They are prereleases, not reviewed releases.

The build of the newest push to `main` is not here: it is [scarletnx/ScarletNX](https://github.com/scarletnx/ScarletNX/releases)'s one prerelease, `main-<commit>`, each package added as its job ends and the whole replaced by the next push's.

Each release's notes say which file is for which system, what changed and where its source is. This repository
holds only the releases: the code is in [scarletnx/ScarletNX](https://github.com/scarletnx/ScarletNX).

## Which file is mine

Every release lists the same files. The newest nightly's links never change, so a bookmark stays current.

| System | File | After downloading |
| --- | --- | --- |
| Linux, x86-64 | `ScarletNX-linux-x86_64.AppImage` | `chmod +x` it and run it |
| Linux, ARM64 | `ScarletNX-linux-aarch64.AppImage` | `chmod +x` it and run it |
| Linux, PowerPC64 LE | `ScarletNX-linux-ppc64le.AppImage` | `chmod +x` it and run it. Present only when its job built |
| Linux, PowerPC64 BE | `ScarletNX-linux-ppc64.AppImage` | `chmod +x` it and run it. Present only when its job built |
| Linux, RISC-V 64 | `ScarletNX-linux-riscv64.AppImage` | `chmod +x` it and run it. Present only when its job built |
| Linux, LoongArch64 | `ScarletNX-linux-loongarch64.AppImage` | `chmod +x` it and run it. Present only when its job built |
| Windows, x86-64 | `ScarletNX-windows-x86_64.zip` | Unzip it and run `bin\scarletnx.exe` |
| Windows, ARM64 | `ScarletNX-windows-aarch64.zip` | Unzip it and run `bin\scarletnx.exe`. Present only when its job built |
| Android, ARM64, x86-64 | `ScarletNX-android-universal.apk` | Install it. [The Android app](https://github.com/scarletnx/ScarletNX/blob/main/docs/hosts/android-app.md) has the first run |
| macOS, ARM64 | `ScarletNX-macos-arm64.zip` | Unzip it, then *Open* from the Finder's menu, as the app is signed ad hoc. Present only when its job built |
| iOS, ARM64 | `ScarletNX-ios-arm64.ipa` | Sideload it. Present only when its job built |

Games hardly run on macOS or iOS yet, so those two are for people testing the builds themselves ([macOS and iOS](https://github.com/scarletnx/ScarletNX/blob/main/docs/hosts/apple.md)). Each AppImage has a `.zsync` file beside it, which AppImage's update tools use to download only what changed. Games need a Vulkan 1.3 driver.

## First run

Started with no arguments, the program opens the launcher. **Install Keys** installs your `prod.keys`, and **Load Switch NSP/XCI/NRO** takes a dump you made from your own console. Keys and games are never part of a release. [Usage](https://github.com/scarletnx/ScarletNX/blob/main/docs/user/usage.md) covers the command line and the folders.

## Trying a pull request's build

Open the pull request's release, `pr-<number>`, and take the file for your system from the table above. A pull request's build is made from its latest push and is replaced at the next one, so check the commit named in the notes against the one you mean to test. A pull request from a fork has no build until someone on the team labels it `publish builds`.

When you report what you saw, say which build it was (the nightly's tag, or the pull request's number and its commit) and add your system, processor, graphics card and driver version. The [testing guide](https://github.com/scarletnx/ScarletNX/blob/main/docs/user/testing.md) has the form.

## Problems

A game that does not run as it should goes to the [Game report](https://github.com/scarletnx/ScarletNX/issues/new?template=game-report.yml) form, with the log attached. A fault in a build's packaging, or a file missing from a release, goes to [scarletnx/ScarletNX](https://github.com/scarletnx/ScarletNX/issues) as an issue starting with `[ci]`, since the workflow that builds and publishes the files lives there.
