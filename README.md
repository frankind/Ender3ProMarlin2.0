# Ender3ProMarlin2.0 with BLTouch enabled
* For who is using Ender 3 Pro with creality silent board 1.1.5
* The default setting is using base on my machine with add original Creality BLTouch (v3.1)

# Hardware
* Ender 3 Pro with silent board 1.1.5 (8 bits)
* Creality BLTouch (v3.1)

# Prerequisite
1. Already flash bootloader (normally silent board already installed it)
1. installed hardware with [this](https://www.youtube.com/watch?v=2B4qdKdqJj4)
1. Has some experience on flashing firmware

# Recommended Youtube
* [Install hardware](https://www.youtube.com/watch?v=2B4qdKdqJj4)
* [Install bootloader and firmware](https://www.youtube.com/watch?v=aquuSNEekvY)
* [Install with VSCode](https://www.youtube.com/watch?v=RbbzsJBpEhc)

# My Environment
* Macbook Pro (OSX Catalina)
* Visual Studio Code (VSCode) with extensions
  * Auto Build Marlin
  * Platform IO IDE

# Firmware base
* Base on Marlin 2.0.6
  * [Marlin](https://github.com/MarlinFirmware/Marlin/releases/tag/2.0.6)
  * [Config](https://github.com/MarlinFirmware/Configurations/tree/release-2.0.6/config/examples/Creality/Ender-3%20Pro)


# What will you get
* No responsible from me (Do at your own risk)
* Firmware 2.0.6 with supporting BLTouch (Original Creality v3.1)
* THERMAL RUNAWAY ENABLED (Default)
* Auto home will go to Z20 (bed & nozzle protection)
* SDCard support (Yes)

# Limitation (not enough space)
* No custom boot screen
* Slim Menu

# Configuration.h
```c
#define NOZZLE_TO_PROBE_OFFSET { -44, -6, 0 } // install normal side
#define DEFAULT_AXIS_STEPS_PER_UNIT   { 80, 80, 400, 102.8 } // my E-Step is 102.8
#define Z_PROBE_SPEED_SLOW (Z_PROBE_SPEED_FAST / 4) // I use 4, it's quite slow but more accurate
#define RESTORE_LEVELING_AFTER_G28 // Restore bed level after auto home
```

# Post installation
1. Make sure you level 4 bed corners (by paper ~ 0.1 mm)
1. Do probe z offset by
      1. Run Autohome // it will stop at ~ Z 20
      1. Manual move z to 0 by 10 (twice)
      1. Move z again with by (0.0025) // Will see it might more or lower than 0
      1. Move it to bigger than 0 value with one step // Now you will see the nozzle is not touching bed yet
      1. Go to motion > bed leveling > probe z offset // Move it in negative value until it hit your paper firmly (~0.1 mm thickness)
      1. Remove paper and you must see the gap between nozzle and bed
      1. Move nozzle down a little bit and must not hit the bed (might add around 0.04 - 0.09, example: current mine -3.0 then I move down to -3.08)
      1. Store configuration
1. Do Bed leveling
1. Store configuration

# Note
* I am not guarantee that it will work on any Ender 3 Pro