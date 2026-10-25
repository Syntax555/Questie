# Questie installer

This installer adds Questie for the
[mod-playerbots-portable](https://github.com/Syntax555/mod-playerbots-portable) server to WoW 3.3.5a build 12340. It
installs the commit of [Syntax555/Questie](https://github.com/Syntax555/Questie) that this
ZIP was built from. Internet access and Windows PowerShell 5.1 or later are
required.

1. Extract this ZIP to a writable folder outside your WoW installation.
2. Close WoW completely. Run `Install-Questie.cmd`.
3. Enter your client's `Interface\AddOns` folder when prompted.
4. Enable Questie in the character selection screen. Enable **Show party quest objectives** in Questie to display other group members' quest markers.

The installer downloads the source archive of that commit directly from
GitHub and checks every file of `Questie-335` against the SHA-256 hashes in
`ADDON_FILES.json` before installing it. An existing `Questie-335` folder is
backed up; account and character SavedVariables are preserved.

For a noninteractive installation:

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File .\Install-Questie.ps1 -AddOnsPath 'C:\Games\WoW\Interface\AddOns'
```

`SOURCE_MANIFEST.json` records the repository and commit. The addon, its
guides, graphics and libraries are not redistributed in this ZIP; their
original terms and notices remain applicable. The included MIT license covers
the installer tooling only.

Automated source and installation checks do not replace an in-game test. See
the [integration guide](https://github.com/Syntax555/mod-playerbots-portable/blob/main/docs/questie-playerbots.md) for supported behaviour and the
remaining live validation.
