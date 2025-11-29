# Text Editor

- This is a minimalist, line-oriented text editor implemented in C. It is designed to run in a Unix-like terminal environment.
- It provides basic text editing capabilities like raw mode terminal interaction, file I/O, scrolling, cursor movement, custom terminal handling, and syntax highlighting.


![Screenshot_Img](https://github.com/user-attachments/assets/b16c72f5-f046-466a-bd00-b96ac2fdd1ca)

## Features:

- **Terminal Control:** Uses **raw mode** to capture every keypress and restores terminal settings on exit.
- **Data Structure:** Stores text in an array of **`erow`** structs, separating raw text (`chars`) from display text (`render`) and highlight data (`hl`).
- **I/O:** **`editorOpen`** reads files and **`editorSave`** writes changes. It uses a **dirty flag** for unsaved modifications.
- **Screen Drawing:** It uses an **append buffer** to draw the screen in one go, preventing flicker. It includes a status bar and message bar.
- **Syntax Highlighting:** It supports **C** with rules for keywords, numbers, strings, and multi-line/single-line comments using ANSI colors.
- **Search:** It implements a **Find** function (Ctrl-F) with dynamic matching and navigation.

## Installation and Build:

* Prerequisites:

  Make sure that you have installed the C compiler (`gcc`) and the build utility (`make`).

* Automated Installation:

  The `install.sh` script handles prerequisite installation, compilation, and placing the executable in your local path.

  a. Make the script executable:

  ```
  chmod +x install.sh
  ```
  b. Run the script:

  ``` 
  ./install.sh
  ```
  This script will:

  Use `sudo` to install `gcc` and make if they are missing.
  
  Compile `text_editor.c` into the `kilo` executable.
  
  Move the `kilo` executable to `~/bin`.
  
## Key Bindings:

| Keypress | Action | Function |
| :--- | :--- | :--- |
| **Ctrl-S** | Save | Calls `editorSave()` to write the buffer to the file. |
| **Ctrl-Q** | Quit | Exits the editor. Requires multiple presses if the file is modified. |
| **Ctrl-F** | Find | Starts the search prompt (`editorFind()`). |
| **Arrow Keys** | Move Cursor | Moves the cursor up, down, left, or right. |
| **Home/End** | Jump to Line Ends | Moves cursor to the start/end of the current line. |
| **PageUp/PageDown** | Paging | Moves the cursor up/down by one screen height. |
| **Backspace/DEL** | Delete Char | Deletes the character before (Backspace/Ctrl-H) or at (DEL) the cursor. |
