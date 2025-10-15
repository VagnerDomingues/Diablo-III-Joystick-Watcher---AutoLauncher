# Diablo III Joystick Watcher - Automatic Launcher

## Overview

This is a **Quality of Life (QoL)** enhancement for the AutoHotkey joystick-to-keyboard setup created by **[bennybroseph](https://github.com/bennybroseph/AutoHotKey_Scripts)**.

The original project allows you to play Diablo III (and similar games) with an Xbox controller by mapping controller inputs to keyboard commands. This enhancement automates the process of launching and managing the joystick emulation program alongside Diablo III.

## What This Does

Instead of manually:
1. Starting the "Joystick to Keyboard Emulation.exe"
2. Launching Diablo III through Battle.net
3. Remembering to close the joystick program when done

This solution provides:
- **One-click launcher**: A desktop shortcut that handles everything
- **Automatic joystick management**: Starts the joystick emulation when Diablo III launches
- **Smart monitoring**: Keeps watching while Battle.net is open, even if you restart Diablo III
- **Automatic cleanup**: Stops the joystick emulation when you close Diablo III or Battle.net

## Prerequisites

1. **Download and configure** the original AutoHotkey Scripts from:
   - https://github.com/bennybroseph/AutoHotKey_Scripts
   
2. **Complete the configuration** of "Joystick to Keyboard Emulation.exe" using the Configuration Form application included in the download

3. **Have Diablo III** installed via Battle.net

## Installation

### Step 1: Locate Your AutoHotkey Folder

Navigate to your AutoHotkey installation folder. The structure should look like:
```
<versionFolder>/
  └── AutoHotkey/
      ├── config.ini
      ├── Joystick to Keyboard Emulation.exe  (already configured by ConfigurationForm.exe)
      └── (other files)
```

### Step 2: Add the Watcher Files

Place the following files **as siblings** to "Joystick to Keyboard Emulation.exe":

- `joystick_diablo_watcher.bat`
- `joystick_diablo_new_shortcut.bat`

Your folder should now look like:
```
<versionFolder>/
  └── AutoHotkey/
      ├── config.ini
      ├── Joystick to Keyboard Emulation.exe
      ├── joystick_diablo_watcher.bat          ← NEW
      ├── joystick_diablo_new_shortcut.bat     ← NEW
      └── (other files)
```

### Step 3: Create the Desktop Shortcut

1. **Double-click** `joystick_diablo_new_shortcut.bat`
2. A shortcut named **"Diablo III Joystick.lnk"** will be created on your Desktop
3. The shortcut will have the joystick icon

## Usage

### Starting Diablo III

1. **Double-click** the "Diablo III Joystick" shortcut on your Desktop
2. The watcher starts in the background (hidden)
3. The Diablo III Launcher opens
4. Click "Play" to start Diablo III
5. The joystick emulation automatically starts when Diablo III launches

### Playing

- Play Diablo III normally with your controller
- The joystick emulation runs in the background

### Stopping

**Option 1: Close Diablo III**
- Close Diablo III (the game will quit)
- The joystick emulation stops automatically
- The watcher continues running in the background
- You can click "Play" again, and the joystick emulation will restart automatically

**Option 2: Close Battle.net**
- Close the Battle.net launcher
- The joystick emulation stops
- The watcher exits
- Everything is cleaned up

## How It Works

### Components

1. **joystick_diablo_new_shortcut.bat**
   - Creates the desktop shortcut with the joystick icon
   - Generates a VBS launcher script
   - Only needs to be run once (or when you want to recreate the shortcut)

2. **joystick_diablo_watcher.bat**
   - Monitors for Battle.net and Diablo III processes
   - Automatically starts "Joystick to Keyboard Emulation.exe" when Diablo III launches
   - Stops the joystick emulation when Diablo III closes
   - Exits when Battle.net closes

3. **joystick_diablo_launcher.vbs** (generated automatically)
   - Launches both the watcher and Diablo III Launcher
   - Runs the watcher in a hidden window

### Workflow

```
Desktop Shortcut
    ↓
Launches VBS Launcher
    ↓
    ├─→ Starts Watcher (hidden)
    │       ↓
    │   Waits for Battle.net
    │       ↓
    │   Waits for Diablo III
    │       ↓
    │   Starts Joystick Emulation
    │       ↓
    │   Monitors both processes
    │
    └─→ Opens Diablo III Launcher
```

## Troubleshooting

### The shortcut doesn't have an icon
- Make sure "Joystick to Keyboard Emulation.exe" exists in the same folder as the batch files
- Re-run `joystick_diablo_new_shortcut.bat`

### The joystick emulation doesn't start
- Check that "Joystick to Keyboard Emulation.exe" is properly configured
- Try running it manually first to ensure it works
- Make sure Battle.net is running before starting Diablo III

### The watcher doesn't exit
- Close Battle.net to exit the watcher
- You can also manually end the cmd.exe process from Task Manager

### Desktop shortcut goes to wrong location
- The script automatically detects your Desktop folder (including OneDrive)
- If issues persist, check the DESKTOP variable in the batch file

## Credits

- **Original AutoHotkey Scripts**: [bennybroseph](https://github.com/bennybroseph/AutoHotKey_Scripts)
- **Original AutoHotkey Setup Video Tutorial**: https://youtu.be/xgfTRkbmkJE
- **myself**: For this quality of Life improvement
- **Claude Code**: For this outstanding readme file and guidance through the process.

## License

This enhancement follows the same license as the original AutoHotkey Scripts project.

---

**Enjoy playing Diablo III with your controller! 🎮**
