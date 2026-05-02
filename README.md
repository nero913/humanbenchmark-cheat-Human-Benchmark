# Number Position Clicker

A lightweight desktop utility that records the exact center position of numbers on your screen, then clicks those saved positions in ascending numeric order.

This tool is designed for personal automation practice, UI testing, repetitive local workflows, and controlled environments where you are allowed to automate mouse clicks.

## Features

- Record number positions manually with hotkeys.
- Click recorded positions from smallest number to largest number.
- Does not rely on OCR after recording.
- Clicks the exact screen coordinates you saved.
- Multilingual user interface.
- Always-on-top window support.
- Save and load recorded coordinates with `saved_points.json`.
- Run without a CMD window by using the `.pyw` file extension.
- Emergency stop hotkey.

## Supported Interface Languages

- Traditional Chinese
- Simplified Chinese
- English
- Japanese
- Korean
- French
- Spanish
- German
- Portuguese
- Russian

## How It Works

The program stores records in this format:

```text
number -> X coordinate -> Y coordinate
```

When you start the click sequence, all records are sorted by number in ascending order.

Example:

```text
3 -> X=900, Y=500
1 -> X=300, Y=400
2 -> X=600, Y=450
```

The click order becomes:

```text
1 -> 2 -> 3
```

The program clicks the saved coordinates directly. It does not need to detect, read, or recognize numbers during the click sequence.

## Requirements

Before running the program, install Python and the required packages.

### Python

Recommended:

```text
Python 3.10 or newer
```

During installation on Windows, enable:

```text
Add python.exe to PATH
```

### Python Packages

Install dependencies:

```bash
python -m pip install pyautogui keyboard
```

## Files

Recommended repository structure:

```text
NumberPositionClicker/
├── NumberPositionClicker.pyw
├── NumberPositionClicker.py
├── README.md
└── saved_points.json
```

Notes:

- `NumberPositionClicker.py` is useful for debugging because it shows CMD errors.
- `NumberPositionClicker.pyw` is useful for normal use because it opens without a CMD window.
- `saved_points.json` is created when you press the save button.

## Usage

### 1. Start the Program

For debugging:

```bash
python NumberPositionClicker.py
```

For normal use without a CMD window:

```text
Double-click NumberPositionClicker.pyw
```

### 2. Record a Number Position

1. Enter the number you want to record.
2. Move your mouse to the exact center of that number on the screen.
3. Press `F6` or click **Record current position F6**.

Example:

```text
Number: 1
Mouse position: center of number 1
Press F6
```

The program saves:

```text
1 -> current mouse X/Y
```

### 3. Record Consecutive Numbers Faster

Use `F7` when recording numbers in order.

1. Set the number field to `1`.
2. Move the mouse to the center of number `1`.
3. Press `F7`.
4. Move the mouse to the center of number `2`.
5. Press `F7`.
6. Continue for `3`, `4`, `5`, and so on.

`F7` records the current position and automatically increases the number by 1.

### 4. Start Clicking

Press:

```text
F9
```

or click:

```text
Start sequence clicking F9
```

The program clicks all saved positions from the smallest number to the largest number.

### 5. Stop Clicking

Press:

```text
F8
```

or click:

```text
Stop F8
```

You can also move the mouse to the top-left corner of the screen to trigger the PyAutoGUI fail-safe stop.

## Hotkeys

| Hotkey | Action |
|---|---|
| `F6` | Record current mouse position for the current number |
| `F7` | Record current mouse position and increase the number by 1 |
| `F8` | Emergency stop |
| `F9` | Start clicking saved positions in ascending order |

## Settings

### Click Delay

Controls the delay between clicks.

Recommended values:

```text
0.15 = safer and easier to observe
0 = fastest
```

### Always On Top

The window is always on top by default.

Use the topmost button to toggle:

```text
Enable topmost / Disable topmost
```

### Save and Load

Click **Save points** to save recorded positions to:

```text
saved_points.json
```

Click **Load points** to reload them later.

## Important Notes

- The program clicks saved screen coordinates, not detected numbers.
- If the target window moves, recorded positions may no longer match the numbers.
- Re-record positions after changing screen resolution, display scaling, game window position, or monitor layout.
- Use this only in environments where automation is allowed.
- Do not use this tool for bypassing CAPTCHA, login verification, anti-bot systems, or any security mechanism.
- The `keyboard` package may require administrator privileges on some Windows systems for global hotkeys to work.
- If hotkeys do not respond, run CMD as administrator and start the program from there.
- When using `.pyw`, Python errors will not appear in a CMD window. Use the `.py` version for debugging.

## Troubleshooting

### The program does not open

Run the `.py` version from CMD:

```bash
python NumberPositionClicker.py
```

Then read the error message.

### Hotkeys do not work

Try running as administrator.

```text
Start Menu -> CMD -> Right click -> Run as administrator
```

Then run:

```bash
python NumberPositionClicker.py
```

### The clicks are in the wrong place

Check these issues:

- The target window moved.
- Screen resolution changed.
- Windows display scaling changed.
- You recorded the edge of the number instead of the center.
- You are using a different monitor layout.

Re-record the coordinates.

### The program clicks too fast

Increase click delay:

```text
0.1
0.15
0.25
```

### The program is too slow

Set click delay to:

```text
0
```

## License

You may publish this project under the MIT License if you want it to be open source.

## Disclaimer

This project is intended for educational, personal, and authorized automation use only. The author is not responsible for misuse, violations of third-party terms of service, or automation in restricted environments.
