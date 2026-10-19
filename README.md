# Image Background Remover

A simple web app built with [Streamlit](https://streamlit.io) that removes the background from an image using the [rembg](https://github.com/danielgatis/rembg) library. Upload a PNG or JPG, see the original and the result side by side, and download the result as a PNG.

## Features

- Upload a PNG, JPG or JPEG image from the sidebar
- Side-by-side view of the original and the background-removed image
- Download the result as a transparent PNG
- Shows a sample image (`zebra.jpeg`) when nothing is uploaded
- Upload limit of 5 MB per image

## Project Structure

```
.
├── bg_remove.py        # Main Streamlit application
├── requirements.txt    # Python dependencies
├── zebra.jpeg          # Sample image shown on first load
└── README.md           # This file
```

## Requirements

- **Python 3.10 or newer** (check with `python3 --version`)
- **pip** (comes with Python)
- An internet connection for the first run (the AI model is downloaded once)

## How to Run the Application

### Step 1: Get the code

Clone the repository and move into the project folder. Replace the placeholders with the real values from the repository page.

```bash
git clone https://github.com/<username>/<repository-name>.git
cd <repository-name>
```

If you downloaded the code as a ZIP instead, unzip it and open a terminal inside the unzipped folder.

### Step 2: Check that you are in the right folder

Run:

```bash
ls
```

(On Windows, use `dir`.) You should see `bg_remove.py`, `requirements.txt` and `zebra.jpeg`. If you do not, you are in the wrong folder. Use `cd` to move into the project folder before continuing.

### Step 3: Create a virtual environment (recommended)

A virtual environment keeps this project's packages separate from the rest of your computer.

**macOS / Linux**

```bash
python3 -m venv venv
source venv/bin/activate
```

**Windows (Command Prompt)**

```bash
python -m venv venv
venv\Scripts\activate
```

**Windows (PowerShell)**

```bash
python -m venv venv
venv\Scripts\Activate.ps1
```

When it is active, your terminal prompt starts with `(venv)`.

### Step 4: Install the dependencies

```bash
python3 -m pip install -r requirements.txt
```

(On Windows, use `python` instead of `python3`.)

This can take a few minutes. A lot of text in the terminal is normal.

### Step 5: Start the app

```bash
python3 -m streamlit run bg_remove.py
```

Streamlit starts a local server and usually opens your browser automatically. If it does not, open this address yourself:

```
http://localhost:8501
```

### Step 6: Use the app

1. Click **Upload** in the left sidebar and choose a PNG or JPG image (maximum 5 MB).
2. Wait for processing. The **original** appears on the left and the **background-removed** image on the right.
3. Click **Download fixed image** in the sidebar to save the result as `fixed.png`.

> **Note:** The very first time you process an image, `rembg` downloads its AI model (roughly 170 MB). This can take a few minutes, and the page may look stuck while it works. Do not refresh. Later runs take only a few seconds.

### Step 7: Stop the app

Go back to the terminal and press `Ctrl + C`. To leave the virtual environment, run `deactivate`.

## Running It Again Later

Each time you come back to the project:

```bash
cd <repository-name>
source venv/bin/activate        # Windows: venv\Scripts\activate
python3 -m streamlit run bg_remove.py
```

## Troubleshooting

| Problem | Fix |
| --- | --- |
| `Error: Invalid value: File does not exist: bg_remove.py` | You are not in the project folder. Run `cd <repository-name>` first, then try again. |
| `Could not open requirements file` | Same cause. Move into the project folder before running `pip install`. |
| `command not found: streamlit` or `command not found: pip` | Use `python3 -m streamlit ...` and `python3 -m pip ...` as shown above. |
| `ModuleNotFoundError` (for example `rembg`, `onnxruntime`) | Run `python3 -m pip install -r requirements.txt` again, with the virtual environment active. |
| `FileNotFoundError: ./zebra.jpeg` | `zebra.jpeg` must be in the same folder as `bg_remove.py`. Do not rename or move it. |
| Page stays on "Running..." for a long time | Normal on the first run while the model downloads. Wait a few minutes and keep an eye on the terminal for errors. |
| `Port 8501 is already in use` | Another Streamlit app is running. Stop it with `Ctrl + C`, or start this one on another port: `python3 -m streamlit run bg_remove.py --server.port 8502` |
| `The uploaded file is too large` | Use an image smaller than 5 MB. |

## Tech Stack

- [Python](https://www.python.org)
- [Streamlit](https://streamlit.io) for the web interface
- [rembg](https://github.com/danielgatis/rembg) for background removal
- [Pillow](https://python-pillow.org) for image handling

## Contributing

1. Create a new branch for your change: `git checkout -b your-feature-name`
2. Make and test your changes locally.
3. Commit and push your branch, then open a pull request to `main`.
4. Wait for the team lead to review it before merging.

Please do not commit your `venv/` folder. Add it to a `.gitignore` file.
