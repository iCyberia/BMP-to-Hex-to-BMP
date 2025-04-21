# BMP ↔ Hex Converter

A simple Python GUI tool to convert between bitmap (BMP) images and comma‑separated hex data.  
Originally designed to streamline workflows with Arduino e‑paper displays.

---

## Features

- **Hex → BMP**: Paste comma‑separated hex bytes, specify width/height, and export as a `.bmp` image.  
- **BMP → Hex**: (Planned) Extract raw bitmap data from a `.bmp` file into comma‑separated hex.  
- Intuitive Tkinter-based GUI with scrollable text input and pop‑up dialogs.

---

## Table of Contents

- [Demo](#demo)  
- [Requirements](#requirements)  
- [Installation](#installation)  
- [Usage](#usage)  
- [License](#license)  

---

## Requirements

- **Python 3.7+**  
- [NumPy](https://pypi.org/project/numpy/)  
- [Pillow](https://pypi.org/project/Pillow/)  
- **Tkinter** (usually included in standard library)

Install dependencies with:

```bash
pip install numpy Pillow
```

---

## Installation

1. Clone this repository:

   ```bash
   git clone https://github.com/iCyberia/BMP-to-Hex-to-BMP.git
   cd BMP-to-Hex-to-BMP
   ```

2. (Optional) Create a virtual environment:

   ```bash
   python3 -m venv venv
   source venv/bin/activate   # Linux / macOS
   venv\Scripts\activate    # Windows
   ```

3. Install required packages:

   ```bash
   pip install -r requirements.txt
   ```

---

## Usage

Run the GUI script:

```bash
python main.py
```

1. **Paste** your comma‑separated hex data into the text area.  
2. **Enter** the intended `Width` and `Height` of the bitmap.  
3. Click **Convert to BMP**.  
4. In the save dialog, choose a destination and filename (`.bmp`).

---

## Examples

Used in conjunction with Arduino e‑paper displays:

```c
// Arduino sketch snippet
#include <GxEPD.h>
#include <SPI.h>

// Paste your generated hex array here
const uint8_t bitmapData[] = {
  0xFF, 0x00, 0xAA, /* … */ 
};

void setup() {
  display.init();
  display.drawBitmap(0, 0, bitmapData, 128, 128, GxEPD_BLACK);
  display.display();
}
```


## License

This project is released under the **GNU General Public License (GPL)**.  
See [LICENSE](LICENSE) for details.  
© 2024 Hiroshi Thomas.

