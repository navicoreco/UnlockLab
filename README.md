# UnlockLab

**Read-only Android diagnostics for technicians and repair shops.**

Plug in a phone, see exactly what's going on inside it — model, firmware,
bootloader state, partitions — without ever touching, flashing, or
unlocking it.

<!-- Swap this for a real screenshot once you have one — a picture of the
     dashboard sells this faster than any paragraph below. -->
<!-- ![UnlockLab dashboard](docs/screenshot.png) -->

## Why read-only

Most free tools in this space are abandoned scripts, or they quietly
double as unlock/bypass tools you can't put on a shop machine or hand to
a client without a second thought. UnlockLab can't flash a device, can't
unlock a bootloader, can't touch device security in any way beyond what
the device owner has already exposed through Developer Options and
standard `fastboot` commands. That's not a missing feature — it's the
whole point. Diagnose with confidence, not a tool that could make things
worse.

## Features

- **Instant device ID** — connect any Android phone over USB, see it
  identified immediately (model, manufacturer, connection state).
- **Live dashboard** — ADB and fastboot status for every connected
  device, refreshing automatically.
- **ADB diagnostics** — full build/hardware property inspection, plus a
  shell tool for running diagnostic commands directly against the device.
- **Fastboot / bootloader inspection** — locked or unlocked, secure boot
  state, active slot, full raw variable dump.
- **Firmware report** — Android version, security patch date, build
  fingerprint, baseband version, in one curated view.
- **Partition table viewer** — a device's actual partition layout by
  name and size.
- **Qualcomm EDL detection** — passively detects Emergency Download
  mode (identification only — no Sahara/Firehose protocol handling, no
  communication with a device in this mode).
- **Dark & light mode**, built for hours on a bench, not a screenshot.

## Download

Grab the latest build from [Releases](../../releases). Windows and Linux
(`.AppImage` / `.deb`) are available today; macOS is on the way.

## Free & Pro

UnlockLab is free to use. A Pro license (via [unlocklab.com](#)) unlocks
the deeper diagnostic layer — full raw property/variable dumps, partition
inspection, EDL detection, and saved command presets — for technicians who
want the complete toolkit. Sign up gets you a free trial to try Pro before
you commit.

## Building from source

Requires Node.js and [pnpm](https://pnpm.io).

```bash
pnpm install
pnpm dev              # run in dev mode
```

```bash
pnpm build:linux       # -> dist/*.AppImage, dist/*.deb
pnpm build:win         # -> dist/*-setup.exe
pnpm build:mac         # -> dist/*.dmg (must run on real macOS to be signed)
```

## Tech stack

Electron, React, TypeScript, Vite, Zustand — wraps the standard Android
`adb`/`fastboot` tools rather than replacing them.

## Scope

UnlockLab does not and will not add bootloader unlocking, FRP bypass,
firmware flashing, IMEI writing, or Firehose/Sahara protocol handling.
If that's what you're looking for, this isn't the right tool — and that's
by design, not an oversight.

## License

See [LICENSE](./LICENSE).

## Contributing

Issues and pull requests welcome. If you're planning something larger
than a small fix, open an issue first to talk it through.
