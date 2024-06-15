"""
Copyright (c) [2024] Hiroshi Thomas. 

License: [GNU General Public License]
You should have received a copy of the GNU General Public License

Purpose: Converts Bitmap to Hex and Hex to Bitmap

Further documentation:
- https://github.com/iCyberia/BMP-to-Hex-to-BMP

Usage examples:
- Used in conjunction with epaper display on arduino
"""
import numpy as np
from PIL import Image
from tkinter import Tk, Text, Scrollbar, Button, filedialog, END, messagebox, Label, Entry

def hex_to_bmp(hex_data, width, height):
    # Convert hex data to binary data
    binary_data = []
    for hex_str in hex_data.split(','):
        hex_str = hex_str.strip()
        if hex_str:
            byte = int(hex_str, 16)
            binary_data.append(f'{byte:08b}')

    binary_str = ''.join(binary_data)

    # Create a numpy array to represent the image
    image_data = np.zeros((height, width), dtype=np.uint8)
    
    # Fill the image data array
    for i in range(height):
        for j in range(width):
            if binary_str[i * width + j] == '1':
                image_data[i, j] = 255

    # Create and save the image
    img = Image.fromarray(image_data, 'L')
    return img

def save_bmp(img):
    # Open file dialog to save the image
    file_path = filedialog.asksaveasfilename(defaultextension=".bmp", filetypes=[("BMP files", "*.bmp"), ("All files", "*.*")])
    if file_path:
        img.save(file_path)
        messagebox.showinfo("Save Image", f"Image saved to {file_path}")

def convert_hex():
    # Get the hex data from the text widget
    hex_data = text_widget.get("1.0", END)
    
    try:
        # Get width and height from entry widgets
        width = int(width_entry.get())
        height = int(height_entry.get())
        
        # Convert hex data to BMP
        img = hex_to_bmp(hex_data, width, height)
        
        # Save the BMP
        save_bmp(img)
    except Exception as e:
        messagebox.showerror("Error", str(e))

def main():
    global text_widget, width_entry, height_entry
    
    # Create the main window
    root = Tk()
    root.title("Hex to BMP Converter")
    
    # Create a Text widget with a Scrollbar
    text_widget = Text(root, wrap='none')
    scrollbar_y = Scrollbar(root, orient='vertical', command=text_widget.yview)
    scrollbar_x = Scrollbar(root, orient='horizontal', command=text_widget.xview)
    text_widget.config(yscrollcommand=scrollbar_y.set, xscrollcommand=scrollbar_x.set)

    # Pack the widgets
    text_widget.pack(side='left', fill='both', expand=True)
    scrollbar_y.pack(side='right', fill='y')
    scrollbar_x.pack(side='bottom', fill='x')

    # Create a Convert button
    convert_button = Button(root, text="Convert to BMP", command=convert_hex)
    convert_button.pack(side='bottom')

    # Create entry fields for width and height
    Label(root, text="Width:").pack(side='left')
    width_entry = Entry(root)
    width_entry.pack(side='left')
    width_entry.insert(0, "128")  # Default width

    Label(root, text="Height:").pack(side='left')
    height_entry = Entry(root)
    height_entry.pack(side='left')
    height_entry.insert(0, "128")  # Default height

    # Start the Tkinter main loop
    root.mainloop()

if __name__ == '__main__':
    main()
