# Auto-Update Scripts

A collection of system update automation scripts for Linux systems.

## Scripts

### 1. `update-cursor`
A Bash script that automatically checks for and installs updates for the Cursor AI-powered code editor.

**Features:**
- Checks current installed version against latest available version
- Downloads updates from the official Cursor repository
- Backs up existing installation before updating
- Creates/updates desktop entry for application launcher
- Supports automated version checking with `--check` flag
- Safe rollback on installation failure

**Usage:**
```bash
# Interactive update check and installation
./update-cursor

# Check for updates only (non-interactive)
./update-cursor --check
```

**Configuration:**
- Install location: `$HOME/.local/cursor.app`
- Downloads tracked from: GitHub repository (oslook/cursor-ai-downloads)
- Temporary files: `/tmp/cursor-update-$$`

### 2. `upnow`
A comprehensive system package manager updater for CachyOS/Arch Linux systems that updates multiple package managers in one command.

**Supported Package Managers:**
- **System**: pacman (system packages)
- **AUR**: yay (Arch User Repository)
- **Universal**: snap, flatpak
- **Development**: npm, brew, rustup, bun, uv
- **Database**: SurrealDB

**Features:**
- Color-coded status messages
- Automatic detection of installed package managers
- Error handling and status reporting
- System reboot recommendations when needed
- Individual package manager updates

**Usage:**
```bash
# Update all package managers
./upnow all

# List available update targets
./upnow list

# Update specific package manager
./upnow pacman
./upnow yay
./upnow snap
# etc.
```

## Installation

1. Clone or download scripts to desired location
2. Make scripts executable:
```bash
chmod +x update-cursor upnow
```

3. (Optional) Add directory to PATH for system-wide access:
```bash
echo 'export PATH="$HOME/.local/auto-updates-scripts:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

## Requirements

### update-cursor
- curl
- Basic POSIX utilities (grep, sed, sort)
- Linux x86_64 architecture

### upnow
- sudo privileges for system package updates
- Individual package managers installed as needed
- CachyOS/Arch Linux base system (for pacman/yay)

## Notes

- Both scripts use colored output for better readability
- Scripts include error handling and safe fallback mechanisms
- `update-cursor` maintains backups for easy rollback
- `upnow` skips package managers that aren't installed

## License

Scripts provided as-is for personal use.