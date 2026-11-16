# Until Morning — Poker Tournament Timer

[RU](README.md) · **ENG**

[Download](https://github.com/MrPrograMax/poker-tournament-timer/releases/latest) · [Development guide](docs/development.md) · [Report a bug](https://github.com/MrPrograMax/poker-tournament-timer/issues)

A poker tournament timer and home game manager for Windows, macOS and Linux.

Set up a tournament or cash game, seat your players, and track the timer, blinds and prize pool on a shared screen. Until Morning runs on your computer, opens in your browser, and saves games locally.

**A pilot release for complete home games on a single device.** Used in a real home game and checked with automated tests and [randomized stress runs](docs/stress-test-2026-11-09.md). We continue improving it based on player feedback. The application interface is currently in Russian; this README is available in English and Russian.

[Quick start](#quick-start) · [Features](#features)

## Quick start

Choose your platform and download the ready-to-run app. **No Go, Docker or Node.js installation required.**

| Platform | Download | Start |
| --- | --- | --- |
| Windows · Intel / AMD | [Download .exe](https://github.com/MrPrograMax/poker-tournament-timer/releases/download/v1.0.0/until-morning-v1.0.0-windows-amd64.exe) | Open the downloaded file |
| macOS · Intel and Apple Silicon | [Download universal .pkg](https://github.com/MrPrograMax/poker-tournament-timer/releases/download/v1.0.0/until-morning-v1.0.0-macos-universal.pkg) | Install, then open Until Morning from Applications |
| Linux · Intel / AMD | [Download .run](https://github.com/MrPrograMax/poker-tournament-timer/releases/download/v1.0.0/until-morning-v1.0.0-linux-amd64.run) | Make the file executable and run it |

For ARM devices: [Windows ARM64](https://github.com/MrPrograMax/poker-tournament-timer/releases/download/v1.0.0/until-morning-v1.0.0-windows-arm64.exe) · [Linux ARM64](https://github.com/MrPrograMax/poker-tournament-timer/releases/download/v1.0.0/until-morning-v1.0.0-linux-arm64.run). The Mac installer supports both architectures.

Your browser opens automatically. If it does not, visit [localhost:8080](http://localhost:8080) to set up your game. Builds are not yet signed by a trusted publisher, so your operating system may ask you to allow the first launch. On macOS, after trying to open the installer, the option is available in **System Settings → Privacy & Security**.

<details>
<summary>Run on Linux from the terminal</summary>

In the directory containing the downloaded file:

```sh
chmod +x until-morning-v1.0.0-linux-amd64.run
./until-morning-v1.0.0-linux-amd64.run
```

For ARM, replace `amd64` with `arm64` in the filename.

</details>

On Windows and Linux, keep the program window open during the game; press **Ctrl+C** to stop it. On macOS, no terminal is needed; use **Until Morning → Quit (⌘Q)** to stop the app. Closing the browser tab does not stop the server.

Games and the archive are stored in a persistent user data directory and survive moving or updating the app. **When switching from an older ZIP release, transfer your saves** using the [save migration guide](docs/development.md#сохранения) (in Russian), which lists paths for each platform and explains automatic migration.

<details>
<summary>Other ways to run: portable ZIP and source code</summary>

Portable ZIPs are available in the [release assets](https://github.com/MrPrograMax/poker-tournament-timer/releases/latest). Extract the entire archive, then use `start.cmd` on Windows, `start.command` on macOS, or `start.sh` on Linux. This option stores games in the adjacent `data` directory: keep the whole folder when updating.

To run from source, install [Go 1.24+](https://go.dev/dl/) and run `go run ./cmd/until-morning` from the repository root. To disable automatic browser opening: `go run ./cmd/until-morning -open-browser=false`.

Project layout, build instructions and tests are documented in the [development guide](docs/development.md) (in Russian).

</details>

## Features

- **Tournaments and cash games:** configure stacks, blinds and entry fees; track extra entries and results.
- **Blind structure:** generate a schedule, edit levels and breaks, add levels, and extend the current level during play.
- **Seating:** up to 200 players across multiple tables, automatic seat selection, and suggestions from saved names and nicknames.
- **Shared display:** a large countdown, current and next blinds, pause controls, sound alerts and fullscreen mode.
- **Prizes and bounties:** percentage-based payouts, fixed bounties, and progressive knockout (PKO) with a configurable split.
- **Player management:** search by name or nickname, filter by table or elimination status, register late entries, re-entries and add-ons. Elimination frees the seat while preserving the player's history and ability to re-enter.
- **Multi-table tournaments (MTT):** suggested table merges and balancing with minimal player moves, a seating preview, a final table for remaining players, and undo. Rotate the table diagram without changing seat numbers.
- **Freezeout stage:** start manually or after a selected break, adjust add-on terms, and allow re-entry with the organizer's confirmation.
- **Results:** standings, payouts and player statistics, including knockouts, re-entries and add-ons; entry and top-up tracking for cash games. Unresolved places remain unset when a game ends early.
- **JSON export:** separate player names (`name`) and nicknames (`nick`), contributions, re-entries, add-ons, knockouts and payouts. Exports use `schemaVersion: 2`; missing names or nicknames are `null`, with no generated player labels. Amounts are in rubles; unresolved results are `null`. Internal IDs and the event log are excluded.
- **Game archive:** completed games and the previous game when starting a new one are saved on the device. Review payouts, statistics, blind structures and events without changing the current game. Undoing completion updates the archive.
- **Action history:** an event log, sequential undo, and persistence of the current game and available undo steps across restarts.

Until Morning tracks money but does not process payments. Live control from another device is not yet implemented.

Found a bug or have an idea? [Open an issue](https://github.com/MrPrograMax/poker-tournament-timer/issues) with the steps, expected behavior, operating system and app version. If the project helps your home games, a GitHub star is appreciated.

To support further development, you can [support the author via T-Bank](https://t.tb.ru/pm_short/4zP0U0E06Pf).
