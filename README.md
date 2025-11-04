# A\86 Operating System v0.1

A modern DOS-like operating system with 16-bit and 32-bit support.

## Project Structure

```
A86/
├── boot.asm           - Bootloader
├── kernel.asm         - Main OS kernel (STABLE)
├── A86_0.1.img        - STABLE bootable disk image
│
└── TESTING/           - UNSTABLE experimental builds
    ├── README.txt     - Testing version documentation
    ├── kernel.asm     - Kernel with FAT16 module
    ├── fat16.asm      - FAT16 filesystem module
    ├── A86_TEST.img   - Test disk image
    └── build.sh       - Build script
```

## STABLE Version (Recommended)

**Location**: Main folder
**Disk Image**: `A86_0.1.img`
**Status**: ✅ WORKING

### Features:
- **40+ commands** in 16-bit real mode
- Full 32-bit protected mode support
- CPU capability detection (16/32/64-bit)
- **86-Fetch** - System information display (like fastfetch)
- Math utilities (calculator, prime checker, Fibonacci, random)
- String operations (reverse, upper, lower)
- Visual elements (banner, box, stars, spinner)
- Graphical GUI mode (VGA Mode 13h - 320x200x256 colors)
- Mode switching between real and protected mode
- Interactive graphical interface with window drawing

### To Run:
```bash
qemu-system-x86_64 -drive format=raw,file=A86_0.1.img
```

### Commands (16-bit Real Mode):
```
HELP       - Show all commands
VER        - Version information
CLS        - Clear screen
MEM        - Memory information
TIME       - System time
DATE       - System date
ECHO       - Print text
CALC       - Calculator (e.g., CALC 10 + 5)
HEX        - Convert to hexadecimal
BIN        - Convert to binary
ASCII      - Show ASCII table
REGS       - Show registers
BEEP       - PC speaker beep
RAINBOW    - Colorful output
INFO       - System information
BITCHECKER - Check CPU mode (16/32/64-bit)
PROTECTED  - Switch to 32-bit protected mode
DIR        - List directory (no filesystem)
UPTIME     - Show system uptime
SHUTDOWN   - Power off system (APM)
PAUSE      - Wait for keypress
COLOR      - Change text color
GUI        - Launch graphical mode ⭐ NEW!
```

### Commands (32-bit Protected Mode):
```
PM:\> HELP   - Show commands
PM:\> VER    - Version
PM:\> REAL   - Return to real mode (reboots)
```

## TESTING Version (Experimental)
Note: Testing is no longer public and is used for testing features before they join stable.

**Location**: `TESTING/` folder
**Disk Image**: `TESTING/A86_TEST.img`
**Status**: ⚠️ UNSTABLE - FAT16 filesystem experimental

### What's Different:
- Includes FAT16 filesystem module (`fat16.asm`)
- Attempts to initialize FAT16 on boot
- Same command set as stable version
- May have bugs or fail to boot

### To Build:
```bash
cd TESTING
./build.sh
```

### To Run:
```bash
cd TESTING
qemu-system-x86_64 -drive format=raw,file=A86_TEST.img
```

## GUI Mode Features

The `GUI` command launches a graphical interface using VGA Mode 13h (320x200 pixels, 256 colors).

**GUI Controls:**
- **ESC** - Exit GUI and return to command prompt
- **1** - Draw red color fill demo
- **2** - Draw colorful pattern demo

**GUI Features:**
- Blue title bar with "A\\86 GUI v0.1" text
- Window with white borders
- Interactive buttons (green and red)
- Real-time keyboard interaction
- VGA direct memory access at 0xA000

## Version History

- **v0.1.2** - Major Feature Update
  - **86-FETCH** command - Beautiful system information display
  - **40+ total commands** (expanded from 23)
  - Math utilities: RANDOM, PRIME, FIB
  - String operations: REVERSE, UPPER, LOWER
  - Visual elements: BANNER, STARS, BOX, SPINNER
  - Additional info commands: SYSINFO, CPUINFO, DISKINFO, TREE
  - Enhanced HELP system with pagination (HELP/HELP2)
  - GUI mode with VER and SHUTDOWN buttons

- **v0.1.1** - Feature Update
  - Added GUI mode with VGA graphics (320x200x256)
  - 6 new commands: DIR, UPTIME, SHUTDOWN, PAUSE, COLOR, GUI
  - Total of 23 commands in 16-bit mode
  - Interactive graphical interface
  - Window and button drawing capabilities

- **v0.1** - Initial release
  - 16-bit real mode OS
  - 32-bit protected mode support
  - 17 commands
  - CPU detection
  - TESTING: FAT16 module added

## License

A\86 Operating System - Educational Project
