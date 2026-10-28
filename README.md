# Questie-335 for Playerbots Portable

Quest maps, tooltips and tracking for **WoW 3.3.5a, build 12340**
(Interface `30300`), with group bot quest progress for
[Playerbots Portable](https://github.com/Syntax555/mod-playerbots-portable).
This maintained fork uses the `335` branch.

## Install or update

1. Download [Questie-335-latest.zip](https://github.com/Syntax555/Questie/releases/latest/download/Questie-335-latest.zip)
   from this fork's [Latest release](https://github.com/Syntax555/Questie/releases/latest).
2. Extract it to a writable folder outside WoW, then close WoW completely.
3. Run `Install-Questie.cmd` and select your client's `Interface\AddOns` folder.
   Internet access and Windows PowerShell 5.1 or later are required; no
   administrator rights are needed.
4. Start WoW and enable Questie-335. Open settings with `/questie`; enable
   **Show party quest objectives** for markers from other party members' quests.

The ZIP contains an **installer, not the addon**. It downloads its exact fork
commit from GitHub, verifies every addon file against SHA-256 hashes and
installs `Interface/AddOns/Questie-335/Questie-335.toc`. It backs up an existing
`Questie-335` folder and preserves account and character SavedVariables in
`WTF/`. Use the same steps for updates; do not mix files or nest another folder.
The installed `SOURCE_REVISION.txt` and `SOURCE_MANIFEST.json` identify the source.

For a noninteractive installation, run this in the extracted installer folder:

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File .\Install-Questie.ps1 -AddOnsPath 'C:\Games\WoW\Interface\AddOns'
```

## mod-playerbots-portable fork

Upstream Questie-335 provides the Playerbots quest-progress integration,
connected group discovery, character GUID validation and Questie's key binding
header. This fork packages that native implementation for Playerbots Portable.

Use the matching [Playerbots Portable server](https://github.com/Syntax555/mod-playerbots-portable/releases/latest),
which includes the MultiBot Bridge. Its snapshots include the bot's GUID, which
must match the current group member. Native compatibility with older bridges
that omit GUIDs is retained; explicitly malformed or mismatched GUIDs are
rejected. No additional module, compiler or server setting is required. MultiBot is
optional for controls; the separate `mod-questie-bridge` is not required for bot
quest progress.

Invite bots normally. Discovery, snapshots and updates start automatically,
including after `/reload`. Questie shows each authorized group bot's own active
quest counters in its existing tooltips and party objectives. Real players
continue to use ordinary QuestieComms. The tracker remains your own quest log;
party-only objective markers support groups of at most five.

Questie's AzerothCore database can differ from Individual Progression or custom
quest data. Unknown objectives cannot supply map locations absent from that
database. Source fixtures and installer checks do not establish complete live
client coverage: objective pins, tooltips, turn-in, abandonment and departure
cleanup still need in-game validation. See the
[integration guide](https://github.com/Syntax555/mod-playerbots-portable/blob/main/docs/questie-playerbots.md).

## Source and contributions

Changes belong on this fork's `335` branch. Its
[Latest workflow](https://github.com/Syntax555/Questie/blob/335/.github/workflows/latest.yml)
checks Lua syntax and installation before publishing the rolling installer.
The server's [manifest](https://github.com/Syntax555/mod-playerbots-portable/blob/main/versions.lock.json)
pins its tested fork commit; Latest may be newer. Follow the
[contributing guide](https://github.com/Syntax555/mod-playerbots-portable/blob/main/CONTRIBUTING.md)
for source updates and checks. Report fork integration problems in
[this issue tracker](https://github.com/Syntax555/Questie/issues), with the
installed revision, client build, reproduction and complete first Lua error
(`/console scriptErrors 1`).

## Provenance and notices

Based on [Aldori15/Questie](https://github.com/Aldori15/Questie/tree/335),
continuing widxwer's 3.3.5a port of the original Questie team's addon. The last
imported upstream revision is
[`4c7df0caf0c8`](https://github.com/Aldori15/Questie/commit/4c7df0caf0c86ddacf8ae31cb7489189c6d811ce);
its [README](https://github.com/Aldori15/Questie/blob/4c7df0caf0c86ddacf8ae31cb7489189c6d811ce/README.md)
describes the general Questie features and optional upstream server bridge.

There is no general root license declaration for Questie at this revision.
Libraries retain their [own notices](https://github.com/Syntax555/Questie/blob/335/Libs/LICENSE.txt);
[icon terms](https://github.com/Syntax555/Questie/blob/335/Icons/LICENSE.md)
cover some icons from shagu/pfQuest and identify the remaining uncertainty.
Preserve file and component notices. The installer's
[MIT license](https://github.com/Syntax555/Questie/blob/335/.github/installer/LICENSE)
covers its tooling only; the installer ZIP contains no addon files.
