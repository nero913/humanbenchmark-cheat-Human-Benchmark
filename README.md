# Human Benchmark Cheat

A lightweight desktop utility that detects a target color on the screen and automatically clicks the center of the detected color area.

This project is designed for personal automation practice, UI testing, repetitive local workflows, and controlled environments where color-based mouse automation is allowed.

## Overview

Color Detection Auto Clicker lets you:

- Select a target color with an eyedropper.
- Monitor the current mouse color in real time.
- Define a custom detection area on the screen.
- Automatically click the center of the detected color region.
- Use global hotkeys for fast setup and emergency stopping.
- Run without a CMD window by using the `.pyw` file extension.
- Keep the program window always on top.
- Switch the interface between multiple languages.

## Features

- Color-based screen detection.
- Eyedropper tool for picking the target color.
- Live mouse color preview.
- RGB target color editor.
- Adjustable color tolerance.
- Adjustable minimum detected area.
- Adjustable click delay.
- Custom detection area setup.
- Full-screen detection mode.
- Emergency stop hotkey.
- Always-on-top window support.
- Multilingual interface.

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

The program captures a selected region of your screen and compares each pixel against the target RGB color.

A pixel is considered a match when its color distance is within the configured tolerance.

After matching pixels are found, the program groups them into color regions and clicks the center of the largest region that is larger than the minimum area setting.

Example:

```text
Target color: RGB(0, 255, 0)
Tolerance: 45
Minimum area: 20
```

If a matching green region is found, the program clicks the center of that region.

## Requirements

### Python

Recommended:

```text
Python 3.10 or newer
```

During Python installation on Windows, enable:

```text
Add python.exe to PATH
```

### Python Packages

Install the required packages:

```bash
python -m pip install pyautogui pillow keyboard opencv-python numpy
```

## Files

Recommended repository structure:

```text
ColorDetectionAutoClicker/
├── ColorClicker_FAST.py
├── ColorClicker_FAST.pyw
└── README.md
```

Notes:

- `ColorClicker_FAST.py` is useful for debugging because it can show CMD error messages.
- `ColorClicker_FAST.pyw` is useful for normal use because it opens without a CMD window.
- If the `.pyw` version fails silently, run the `.py` version from CMD to see the error.

## Usage

### 1. Start the Program

For debugging:

```bash
python ColorClicker_FAST.py
```

For normal use without a CMD window:

```text
Double-click ColorClicker_FAST.pyw
```

### 2. Pick a Target Color

Move your mouse over the color you want to detect.

Then press:

```text
F6
```

or click:

```text
Pick color
```

The selected color will be saved as the target RGB color.

### 3. Use Live Eyedropper Preview

Click:

```text
Start live eyedropper
```

The program will continuously show the color currently under your mouse.

Click:

```text
Stop eyedropper
```

to stop the live preview.

### 4. Set the Detection Area

You can set a custom screen detection area with `F7`.

1. Move your mouse to the top-left corner of the desired detection area.
2. Press `F7`.
3. Move your mouse to the bottom-right corner of the desired detection area.
4. Press `F7` again.

The program automatically fills:

```text
X / Y / W / H
```

You can also click the detection-area button instead of pressing `F7`.

### 5. Use Full-Screen Detection

Click:

```text
Full screen
```

This sets the detection area to the entire screen.

For better speed, use a smaller detection area whenever possible.

### 6. Start Auto Clicking

Click:

```text
Start
```

The program will begin searching for the target color in the detection area.

When it finds a matching color region, it clicks the center of that region.

### 7. Stop Auto Clicking

Press:

```text
F8
```

or click:

```text
Stop
```

You can also move your mouse to the top-left corner of the screen to trigger PyAutoGUI's fail-safe stop.

## Hotkeys

| Hotkey | Action |
|---|---|
| `F6` | Pick the current mouse color as the target color |
| `F7` | Set detection area: first press = top-left, second press = bottom-right |
| `F8` | Emergency stop |

## Settings

### RGB

The target color is stored as RGB values:

```text
R = Red
G = Green
B = Blue
```

You can edit these values manually or use the eyedropper.

### Color Tolerance

Controls how close a screen color must be to the target color.

Lower value = stricter matching.

Higher value = looser matching.

Recommended values:

```text
25-40 = precise detection
45-70 = normal detection
80-100 = loose detection
```

### Minimum Area

Controls the smallest region that will be accepted as a valid target.

Lower value = detects smaller objects but may detect noise.

Higher value = ignores small noise but may miss small targets.

Recommended values:

```text
10-20 = small targets
20-50 = normal targets
50-100 = avoid noise
```

### Click Delay

Controls the delay between clicks.

Recommended values:

```text
0 = fastest
0.05 = very fast
0.15 = safer and easier to observe
0.3 = slow and controlled
```

## Recommended Setup

For precise color detection:

```text
Color tolerance: 25-40
Minimum area: 20
Click delay: 0
Detection area: small custom area
```

For easier detection when the color changes slightly:

```text
Color tolerance: 60-90
Minimum area: 10-30
Click delay: 0.05
```

If the program clicks the wrong place:

```text
Lower color tolerance
Increase minimum area
Reduce detection area
Pick the target color again
```

## Performance Tips

- Use the smallest detection area possible.
- Avoid full-screen detection if speed matters.
- Use click delay `0` for maximum speed.
- Increase minimum area to ignore small color noise.
- Pick the color directly from the target screen instead of guessing RGB values.
- Close unnecessary screen overlays that may contain similar colors.

## Important Notes

- The program detects colors, not objects.
- If other areas on the screen have similar colors, the program may click them.
- If lighting, effects, transparency, or anti-aliasing changes the color, increase tolerance.
- If it clicks too broadly, decrease tolerance or increase minimum area.
- Re-pick the target color if the target appearance changes.
- Use this only in environments where automation is allowed.
- Do not use this tool for bypassing CAPTCHA, login verification, anti-bot systems, or security mechanisms.
- Some games or protected applications may block simulated mouse input.
- The `keyboard` package may require administrator privileges on some Windows systems for global hotkeys to work.

## Troubleshooting

### The Program Does Not Open

Run the `.py` version from CMD:

```bash
python ColorClicker_FAST.py
```

Then read the error message.

### Hotkeys Do Not Work

Try running CMD as administrator:

```text
Start Menu -> CMD -> Right click -> Run as administrator
```

Then run:

```bash
python ColorClicker_FAST.py
```

### The Program Clicks the Wrong Color

Try these fixes:

```text
Lower color tolerance
Increase minimum area
Pick the color again with F6
Use a smaller detection area
```

### The Program Cannot Find the Color

Try these fixes:

```text
Increase color tolerance
Lower minimum area
Make sure the detection area includes the target
Use F6 to pick the exact color again
```

### The Program Clicks Too Fast

Increase click delay:

```text
0.05
0.15
0.3
```

### The Program Is Too Slow

Try:

```text
Click delay: 0
Smaller detection area
Lower screen resolution or smaller target region
```

### The CMD Window Appears

Rename the file extension:

```text
.py -> .pyw
```

Example:

```text
ColorClicker_FAST.pyw
```

### The Program Freezes or Clicks Continuously

Press:

```text
F8
```

or move the mouse to the top-left corner of the screen.

## Safety

This program can move and click your mouse automatically.

Before starting:

- Make sure the detection area is correct.
- Test with a slower click delay first.
- Keep `F8` ready for emergency stop.
- Keep PyAutoGUI fail-safe enabled.

## License

You may publish this project under the MIT License if you want it to be open source.

## Disclaimer

This project is intended for educational, personal, and authorized automation use only. The author is not responsible for misuse, violations of third-party terms of service, or automation in restricted environments.
