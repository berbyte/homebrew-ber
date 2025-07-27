# Homebrew Tap for Sinkzone

This repository contains the Homebrew formula for [Sinkzone](https://github.com/berbyte/sinkzone), a DNS-based productivity tool that helps you stay focused by blocking distracting websites during focus sessions.

## Installation

```bash
brew tap berbyte/sinkzone
brew install sinkzone
```

## Quick Start

1. **Install Sinkzone:**
   ```bash
   brew tap berbyte/sinkzone
   brew install sinkzone
   ```

2. **Start the DNS resolver (requires root):**
   ```bash
   sudo sinkzone resolver
   ```

3. **Open the TUI in another terminal:**
   ```bash
   sinkzone
   ```

4. **Enable focus mode:**
   - Press `f` in the TUI, or
   - Run: `sinkzone focus 1h`

## Usage

### Commands

- `sinkzone` - Start the TUI interface
- `sudo sinkzone resolver` - Start the DNS resolver (requires root)
- `sinkzone focus 1h` - Enable focus mode for 1 hour
- `sinkzone status` - Check focus mode status
- `sinkzone disable-focus` - Disable focus mode immediately

### TUI Navigation

- **Tabs**: Use `←`/`→` to switch between tabs
- **Focus Mode**: Press `f` to enable focus mode for 1 hour
- **Monitoring**: View and manage blocked/allowed domains
- **Settings**: Configure upstream DNS resolvers
- **Quit**: Press `q` to exit

## Configuration

Configuration files are stored in `~/.sinkzone/`:

- `sinkzone.yaml` - Main configuration file (upstream DNS resolvers)
- `sinkzone.db` - SQLite database for DNS queries and allowlist
- `state.json` - Focus mode state

## Service Management

### Linux (systemd)

```bash
# Enable and start the service
sudo systemctl enable sinkzone-resolver
sudo systemctl start sinkzone-resolver

# Check status
sudo systemctl status sinkzone-resolver

# Stop the service
sudo systemctl stop sinkzone-resolver
```

### macOS (launchd)

```bash
# Enable and start the service
sudo launchctl load /Library/LaunchDaemons/com.berbyte.sinkzone.resolver.plist

# Stop the service
sudo launchctl unload /Library/LaunchDaemons/com.berbyte.sinkzone.resolver.plist

# Check logs
tail -f /var/log/sinkzone-resolver.log
```

## Features

- **DNS-based blocking**: Blocks distracting websites at the DNS level
- **Focus mode**: Temporarily block non-allowlisted domains
- **Allowlist management**: Manage domains that should always be allowed
- **Real-time monitoring**: View DNS queries and their status
- **TUI interface**: Beautiful terminal user interface
- **Service support**: Run as a system service on Linux/macOS

## Development

This tap is automatically updated by GitHub Actions when new releases are published. 