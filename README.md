# ScarletNX nightly builds

Builds of [ScarletNX](https://github.com/scarletnx/ScarletNX), published by its
[publish workflow](https://github.com/scarletnx/ScarletNX/blob/main/.github/workflows/publish.yml):

- **Nightlies**, `nightly-<date>-<commit>`: each push to `main` that builds everywhere. The newest 30 are kept, and
  [the latest](https://github.com/scarletnx/nightly/releases/latest) is always the newest.
- **Pull requests**, `pr-<number>`: the builds of an open pull request, replaced at each push to it and deleted when
  it closes. They are prereleases, not reviewed releases.

Each release's notes say which file is for which system, what changed and where its source is. This repository holds
only the releases: the code is in [scarletnx/ScarletNX](https://github.com/scarletnx/ScarletNX).

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
| Android | `ScarletNX-android-universal.apk` | Install it. [Android](https://github.com/scarletnx/ScarletNX/blob/main/docs/ANDROID.md) has the first run |
| macOS, Apple silicon | `ScarletNX-macos-arm64.zip` | Unzip it, then *Open* from the Finder's menu, as the app is signed ad hoc |
| iOS | `ScarletNX-ios-arm64.ipa` | Sideload it |

Games hardly run on macOS or iOS yet, so those two are for people testing the builds themselves
([macOS and iOS](https://github.com/scarletnx/ScarletNX/blob/main/docs/APPLE.md)).
On macOS one game reaches its title background, without the logo or the menu.
On iOS a game ran on an iPhone with JIT enabled through StikDebug, but that support is still in a
[pull request](https://github.com/scarletnx/ScarletNX/pull/602), so the nightly's IPA does not have it.
Each AppImage has a `.zsync` file beside it, which AppImage's update tools use to download only what changed.
Games need a Vulkan 1.3 driver.

## First run

Started with no arguments, the program opens the launcher. **Setup device keys** installs your `prod.keys`, and
**Load Switch NSP/XCI/NRO** takes a dump you made from your own console. Keys and games are never part of a release.
[Usage](https://github.com/scarletnx/ScarletNX/blob/main/docs/USAGE.md) covers the command line and the folders.

## Trying a pull request's build

Open the pull request's release, `pr-<number>`, and take the file for your system from the table above.
A pull request's build is made from its latest push and is replaced at the next one, so check the commit named in
the notes against the one you mean to test. A pull request from a fork has no build until someone on the team
labels it `publish builds`.

When you report what you saw, say which build it was (the nightly's date and commit, or the pull request number and its
commit) and add your system, processor, graphics card and driver version. The
[testing guide](https://github.com/scarletnx/ScarletNX/blob/main/docs/TESTING.md) has the form.

## Problems

A game that does not run as it should goes to the
[Game report](https://github.com/scarletnx/ScarletNX/issues/new?template=game-report.yml) form, with the log attached.
A fault in a build's packaging, or a file missing from a release, goes to
[scarletnx/ScarletNX](https://github.com/scarletnx/ScarletNX/issues) as an issue starting with `[ci]`, since the
workflow that builds and publishes the files lives there.
