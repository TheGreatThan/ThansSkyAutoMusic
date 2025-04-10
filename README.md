# SkyAutoMusic Player

A Python script designed to automatically play music notes by simulating keyboard presses, likely intended for games like "Sky: Children of the Light". It reads song data from structured text files and uses AutoHotkey for keyboard control.

## Features

* **Folder-Based Song Loading**: Loads all `.txt` song files from a specified folder.
* **GUI Folder Selection**: Uses `tkinter` to provide a user-friendly dialog for selecting the songs folder.
* **Flexible File Encoding**: Attempts multiple common text encodings (UTF-8, UTF-16, etc.) to read song files, improving compatibility.
* **JSON Song Format**: Reads song data structured in JSON format within the text files.
* **Selectable Keymaps**: Choose between different keyboard layouts ("Normal" and "Sky") to match application or user preference.
* **Playback Control**:
    * Adjust playback speed using a speed factor.
    * Start playback from a specific timestamp within the song (e.g., "1m 30s").
    * Pause and resume playback using the Spacebar.
    * Stop playback and return to song selection using the Escape key.
* **Background Stop Detection**: Uses a separate thread to listen for the 'Esc' key, allowing immediate interruption without disrupting playback timing.
* **Live Playback Timer**: Displays the current position (mm:ss) in the song during playback.

## Requirements

* **Python 3**: Ensure you have Python 3 installed.
* **AutoHotkey**: **Must be installed** on your system. The script relies on AutoHotkey being present to send key presses. You can download it from [https://www.autohotkey.com/](https://www.autohotkey.com/). **PyCharm does not manage this installation.**
* **Python Libraries**:
    * `keyboard`: For detecting global key presses (Esc, Space).
    * `ahk-script` / `ahk`: A Python wrapper for AutoHotkey.
    * `tkinter`: Usually included with standard Python installations.

## Installation

These steps cover general setup. See the "Usage" section for running via command line or PyCharm.

1.  **Install Python 3**: Download and install from [python.org](https://www.python.org/) if you haven't already. Make sure Python is added to your system's PATH during installation.
2.  **Install AutoHotkey**: Download and install from [autohotkey.com](https://www.autohotkey.com/). This is required regardless of how you run the Python script.
3.  **Install Required Python Libraries (if using command line)**: Open your terminal or command prompt and run:
    ```bash
    pip install keyboard ahk-script
    ```
    *(Note: If `pip install ahk-script` doesn't work, try `pip install ahk`. Check the specific library imported in the script.)*
4.  **Get the Script**: Download or copy the script code (from `SkyAutoMusicFolderV2.txt` or similar).
5.  **Create a Songs Folder**: Create a folder where you will store your song `.txt` files (e.g., `C:\Users\YourName\Documents\SkySongs`).

## Usage

You can run the script either directly from the command line or using an IDE like PyCharm.

### Using the Command Line

1.  **Navigate**: Open your terminal or command prompt and navigate (`cd`) to the directory where you saved the script file (e.g., `SkyAutoMusicFolderV2.py`).
2.  **Run**: Execute the script using:
    ```bash
    python SkyAutoMusicFolderV2.py
    ```
    (Replace `SkyAutoMusicFolderV2.py` with the actual filename).
3.  **Follow Prompts**: The script will then run in the terminal, prompting you for:
    * Songs folder confirmation/selection.
    * Keymap choice.
    * Song selection.
    * Speed factor.
    * Start position.
4.  **Switch Window**: After entering the start position, quickly switch focus to the target application window during the 3-second countdown.

### Using PyCharm (or similar IDE)

1.  **Open/Create Project**: Launch PyCharm and open an existing project or create a new one.
2.  **Add Script File**: Copy the code from `SkyAutoMusicFolderV2.txt` and paste it into a new Python file within your PyCharm project (e.g., right-click the project folder > New > Python File, name it `sky_player.py`).
3.  **Install AutoHotkey (Reminder)**: Ensure AutoHotkey is installed on your system. PyCharm manages Python packages, but *not* external applications like AutoHotkey.
4.  **Install Python Packages**: PyCharm needs the `keyboard` and `ahk-script` (or `ahk`) libraries for the project's Python interpreter.
    * **Option A (PyCharm Prompt):** PyCharm might detect the `import keyboard` and `import ahk` statements and show a prompt above them offering to install the missing packages. Click "Install package".
    * **Option B (PyCharm Terminal):**
        * Open the PyCharm Terminal (usually at the bottom, or via `View` > `Tool Windows` > `Terminal`).
        * Run the pip install command:
            ```bash
            pip install keyboard ahk-script
            ```
            *(Again, try `pip install ahk` if `ahk-script` is incorrect for your import).*
5.  **Run the Script**:
    * Right-click anywhere inside the script file editor.
    * Select `Run 'your_script_name'` (e.g., `Run 'sky_player'`).
6.  **Interact via Run Window**: The script's output and input prompts (for folder, keymap, song selection, etc.) will now appear in PyCharm's "Run" tool window at the bottom. Interact with the script there.
7.  **Switch Window**: As with the command line, after entering the start position, you'll need to quickly switch focus to the target application window during the 3-second countdown.

## Controls During Playback

* **`Esc` Key**: Immediately stops the current song playback, releases held keys, and returns you to the song selection menu (whether run from command line or PyCharm).
* **`Spacebar`**: Toggles pause/resume.

## Song File Format (`.txt` files)

The script expects song files to be plain text (`.txt`) files containing data in JSON format. The essential structure looks like this:

```json
{
  "name": "Example Song Title",
  "author": "Author Name",
  "transcribedBy": "Transcriber Name",
  "bpm": 120,
  "pitchLevel": 0,
  "songNotes": [
    { "time": 0, "key": "1Key0" },
    { "time": 500, "key": "1Key2" },
    { "time": 1000, "key": "1Key4" },
    { "time": 1500, "key": "1Key2" },
    { "time": 2000, "key": "1Key0" },
    { "time": 2000, "key": "1Key7" }
  ]
}
```

## For The Nerds 🤓👆

Here fully explain whats going on: https://thegreatthan.github.io/Explain
