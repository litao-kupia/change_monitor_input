# Monitor Input Source Switcher

This Python script allows you to programmatically switch the input source of your Windows monitors using DDC/CI (Display Data Channel Command Interface) commands.

## Features

- Automatically detects and enumerates all physical monitors connected to your system
- Supports switching between HDMI and DisplayPort (DP) inputs
- Uses Windows API calls to communicate with monitors

## Requirements

- Windows operating system
- Python 3.x
- Administrator privileges (may be required for some monitor interactions)

## Installation

1. Clone this repository or download the script.
2. No additional Python packages are required as the script uses built-in modules and Windows API.

## Usage

Run the script from the command line, specifying the desired input source as an argument:

```
python monitor_input_switcher.py <input_source>
```

Where `<input_source>` can be either `hdmi` or `dp`.

Example:
```
python monitor_input_switcher.py hdmi
```

This will switch all compatible monitors to the HDMI input.

## How it works

1. The script enumerates all physical monitors connected to the system.
2. It then sends a VCP (Virtual Control Panel) feature command to each monitor to change the input source.
3. The VCP code `0x60` is used for input source selection.
4. HDMI is represented by the value `0x11`, and DisplayPort by `0x0F`.

## Limitations

- This script will only work on Windows systems.
- Not all monitors support DDC/CI commands. The script may not work with monitors that don't support this feature.
- Some monitors may require different VCP codes or values. You may need to adjust these in the script if your monitor doesn't respond to the default values.
