# Source Admin Tool

A cross-platform server administration tool for Valve Source Engine and GoldSrc game servers. Alternative to HLSW.

[![CI](https://github.com/scai/admintool/actions/workflows/build.yml/badge.svg)](https://github.com/scai/admintool/actions/workflows/build.yml)

## Features

- **RCON Console** — Send commands to your servers with full RCON protocol support, command history, and customizable command templates
- **Server Browser** — Browse servers via the Steam Web API with filtering by game, name, and map; or search within your own server list
- **Server Monitoring** — Auto-refreshing server info, player lists, and rules/cvars at configurable intervals
- **Player Info** — View connected players with name, score, and playtime
- **Rules/CVars** — Inspect server rules and configuration variables
- **Log Listener** — Receive real-time server logs over UDP with automatic UPnP port mapping for NAT traversal
- **GeoIP** — Country flag display for each server using MaxMind GeoLite2
- **Dark Theme** — Built-in dark theme toggle
- **Groups** — Organize servers into named groups for easier management
- **Server Aliases & Notes** — Add custom display names and notes to servers
- **Encrypted Credentials** — RCON passwords and Steam API keys are stored encrypted

## Supported Games

| Game | AppID |
|------|-------|
| Counter-Strike 2 | 730 |
| Counter-Strike: GO | 4465480 |
| Team Fortress 2 | 440 |
| Left 4 Dead 2 | 550 |
| Counter-Strike: Source | 240 |
| Garry's Mod | 4000 |
| Rust | 252490 |
| ARK: Survival Evolved | 346110 |
| Day of Defeat: Source | 300 |
| Half-Life 2: Deathmatch | 320 |
| Insurgency | 222880 |
| No More Room in Hell | 224260 |
| Black Mesa | 362890 |
| Counter-Strike 1.6 | 10 |
| Half-Life Deathmatch | 70 |
| Day of Defeat | 30 |
| Team Fortress Classic | 20 |

Any Source Engine or GoldSrc server can be added manually by IP:port.

## Building

**Requirements:** CMake 3.16+, C++17 compiler, Qt 6 (Core, Gui, Network, Widgets)

```bash
cmake -B build -DCMAKE_BUILD_TYPE=Release
cmake --build build --config Release
```

### Platform-specific deployment

**macOS:**
```bash
macdeployqt build/SourceAdminTool.app
codesign --force --deep --sign - build/SourceAdminTool.app
```

**Windows:**
```bash
windeployqt build/Release/SourceAdminTool.exe
```

**Linux:**
```bash
# Binary and resources are output to package/
```

### Dependencies

Third-party libraries are bundled in `thirdparty/` with pre-built static libraries for each platform:

- [miniupnpc](https://github.com/miniupnp/miniupnp) (v2.2.3) — UPnP port mapping for log receiving through NAT
- [libmaxminddb](https://github.com/maxmind/libmaxminddb) (v1.6.0) — GeoIP country lookups

On Linux and Windows, system packages can also be used (installed via apt/vcpkg).

## Protocols

- **A2S Queries** — UDP server queries ([A2S_INFO](https://developer.valvesoftware.com/wiki/Server_queries#A2S_INFO), A2S_PLAYER, A2S_RULES) with challenge-response handling
- **Source RCON** — TCP remote console protocol with authentication and command queuing

## CI/CD

GitHub Actions builds on Ubuntu, Windows, and macOS using Qt 6.9. Each push to `master` creates a dev pre-release with artifacts for all platforms.

## Third-Party Data

This product includes GeoLite2 data created by MaxMind, available from [maxmind.com](https://www.maxmind.com).

## References

- [Valve Developer Wiki](https://developer.valvesoftware.com/wiki/Main_Page)

## Thanks

- [psychonic](https://github.com/psychonic)
