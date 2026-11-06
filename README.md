# Klicky for Scoop

[Klicky](https://klicky.muneer320.tech/) adds mechanical keyboard sounds to your desktop. This project-owned bucket packages its complete portable Windows build, including all ten sound packs. Requires **Windows 11 x64** and an existing [Scoop installation](https://scoop.sh/).

## Install and start

```powershell
scoop bucket add klicky https://github.com/Muneer320/scoop-bucket
scoop install klicky/klicky
klicky service start
```

Or open **Klicky** from Start. Its tray menu controls sounds, volume and pause. To enable login startup, run `klicky service enable`. Installation itself does not start keyboard monitoring. Global installation is not supported.

Use **one installation method**. If Klicky is already installed with its setup EXE, WinGet or another portable bundle, remove that installation with its own uninstaller first. Preserve settings to carry your preferences across. Do not point two package managers at the same directory.

## Update

```powershell
klicky service stop
scoop update
scoop update klicky
klicky service start
```

Scoop refuses to update running apps before invoking package hooks. Stopping first is required; do not disable that protection. The package moves its owned login shortcut to the new version and preserves settings and sound packs. Your selected Windows Startup approval still controls whether login startup runs.

## Remove

```powershell
scoop uninstall klicky
```

The hook stops only this bundle and removes only its owned login shortcut. A separate Klicky installation is left alone. Settings and custom packs remain in `%LOCALAPPDATA%\Klicky`.

`scoop uninstall klicky --purge` also removes Scoop's small integration-state folder. It does **not** remove `%LOCALAPPDATA%\Klicky`, which can be shared with another installation. After removing every Klicky installation, you can delete that folder yourself if you want to erase saved settings and custom packs.

## Trust and maintenance

Downloads come from immutable [Klicky releases](https://github.com/Muneer320/klicky/releases), with SHA-256 verification. The Windows binaries are unsigned. If Windows Security detects a threat, stop and follow the [troubleshooting guide](https://github.com/Muneer320/klicky/blob/master/docs/TROUBLESHOOTING.md#windows); do not turn off protection.

CI exercises install, same-version update, offline sound discovery, configuration persistence, paused process removal, startup cleanup and preservation of another bundle. It does not measure physical audio latency. Version updates are reviewed before publication; `checkver` and `autoupdate` describe stable release URLs without automatically publishing manifests.

[Source and issues](https://github.com/Muneer320/klicky) · [User guide](https://klicky.muneer320.tech/guide.html) · [Package issue tracker](https://github.com/Muneer320/scoop-bucket/issues)
