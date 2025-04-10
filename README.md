# SkyAutoMusic Player

A Python script designed to automatically play music notes by simulating keyboard presses, likely intended for games like "Sky: Children of the Light". It reads song data from structured text files and uses AutoHotkey for keyboard control.

## Features

* **Folder-Based Song Loading**: Loads all `.txt` song files from a specified folder[cite: 6].
* **GUI Folder Selection**: Uses `tkinter` to provide a user-friendly dialog for selecting the songs folder[cite: 4].
* **Flexible File Encoding**: Attempts multiple common text encodings (UTF-8, UTF-16, etc.) to read song files, improving compatibility[cite: 7].
* **JSON Song Format**: Reads song data structured in JSON format within the text files[cite: 8].
* **Selectable Keymaps**: Choose between different keyboard layouts ("Normal" and "Sky") to match application or user preference[cite: 14, 15].
* **Playback Control**:
    * Adjust playback speed using a speed factor[cite: 41].
    * Start playback from a specific timestamp within the song (e.g., "1m 30s")[cite: 44].
    * Pause and resume playback using the Spacebar[cite: 50, 52].
    * Stop playback and return to song selection using the Escape key[cite: 1].
* **Background Stop Detection**: Uses a separate thread to listen for the 'Esc' key, allowing immediate interruption without disrupting playback timing[cite: 1].
* **Live Playback Timer**: Displays the current position (mm:ss) in the song during playback[cite: 56].

## Requirements

* **Python 3**: Ensure you have Python 3 installed.
* **AutoHotkey**: **Must be installed** on your system. The script relies on AutoHotkey being present to send key presses. You can download it from [https://www.autohotkey.com/](https://www.autohotkey.com/).
* **Python Libraries**:
    * `keyboard`: For detecting global key presses (Esc, Space).
    * `ahk-script`: A Python wrapper for AutoHotkey (requires AutoHotkey installed). You might need to install `ahk` depending on the specific wrapper used, typically via `pip install ahk`. *Note: The import uses `ahk`, ensure you install the correct corresponding package.*
    * `tkinter`: Usually included with standard Python installations, used for the folder selection dialog.

## Installation

1.  **Install Python 3**: Download and install from [python.org](https://www.python.org/) if you haven't already.
2.  **Install AutoHotkey**: Download and install from [autohotkey.com](https://www.autohotkey.com/).
3.  **Install Required Python Libraries**: Open your terminal or command prompt and run:
    ```bash
    pip install keyboard ahk-script
    ```
    *(Note: If `pip install ahk-script` doesn't work, try `pip install ahk`)*
4.  **Download the Script**: Place the `SkyAutoMusicFolderV2.txt` (or rename it to `.py`) file in a convenient location.
5.  **Create a Songs Folder**: Create a folder where you will store your song `.txt` files (e.g., `C:\Users\YourName\Documents\SkySongs`). (Or you could change it later in the program)

## Usage

1.  **Run the Script**: Open your terminal or command prompt, navigate to the directory where you saved the script, and run it using:
    ```bash
    python SkyAutoMusicFolderV2.txt
    ```
    (Or `python your_script_name.py` if you renamed it).
2.  **Select Songs Folder**:
    * The script will show a default path (e.g., `D:\SkySongs`)[cite: 2].
    * It will ask if you want to change the folder (`y/n`)[cite: 3].
    * If you type 'y', a folder selection dialog will appear[cite: 4]. Browse to and select your songs folder.
3.  **Select Keymap**:
    * You'll be prompted to choose between "1. Normal" and "2. Sky" keymaps[cite: 14, 15]. Enter `1` or `2`.
4.  **Select Song**:
    * A list of loaded songs will be displayed[cite: 25].
    * Enter the number or part of the name of the song you want to play[cite: 27]. The script handles ambiguous inputs (e.g., if multiple songs match)[cite: 29, 39].
5.  **Configure Playback**:
    * Enter the desired playback speed factor (e.g., `1.0` for normal, `1.5` for faster, `0.5` for slower)[cite: 41].
    * Enter the starting position (e.g., `0` for the beginning, `1m 30s` to start at 1 minute 30 seconds)[cite: 44].
6.  **Start Playing**:
    * There will be a 3-second delay after entering the start position[cite: 45]. Quickly switch focus to the target application window (e.g., the game) during this time.
    * The script will begin simulating key presses to play the song.

## Controls During Playback

* **`Esc` Key**: Immediately stops the current song playback, releases held keys, and returns you to the song selection menu[cite: 1].
* **`Spacebar`**: Toggles pause/resume. Press once to pause, press again to resume[cite: 50, 52].

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
