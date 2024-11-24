Here’s the updated `README.md` with instructions to install **yt-dlp**, configure it, and include a `.config` file for output paths:

```markdown
# YT-DLP App

A simple web application for downloading videos and audio using **yt-dlp**.

---

## Features
- **Backend**: Node.js server using `yt-dlp` to process video downloads.
- **Frontend**: React-based user interface.
- **Linux Application**: Easy-to-launch Linux app with a `.desktop` entry.

---

## Screenshot

![YT-DLP App Screenshot](assets/screenshot.png)

---

## Prerequisites
1. **Node.js** (v14 or later)
2. **npm** (Node Package Manager)
3. **Linux** environment (tested on Ubuntu)
4. **yt-dlp** installed on your system

---

## Installing `yt-dlp`
Follow these steps to install `yt-dlp` on your Linux system:

### Step 1: Install `yt-dlp`
1. Open the terminal.
2. Run the following command to download and install `yt-dlp`:
   ```bash
   sudo curl -L https://yt-dlp.org/downloads/latest/yt-dlp -o /usr/local/bin/yt-dlp
   sudo chmod a+rx /usr/local/bin/yt-dlp
   ```

3. Verify the installation:
   ```bash
   yt-dlp --version
   ```

### Step 2: Install Required Dependencies (Optional)
For improved performance, you can install additional dependencies:
   ```bash
   sudo apt update
   sudo apt install ffmpeg
   ```

---

## Adding a `.config` File for Output

### Step 1: Create the Configuration Directory
1. Create a configuration folder for `yt-dlp`:
   ```bash
   mkdir -p ~/.config/yt-dlp
   ```

2. Navigate to the folder:
   ```bash
   cd ~/.config/yt-dlp
   ```

### Step 2: Add a `.config` File
1. Create a file named `config`:
   ```bash
   nano config
   ```

2. Add the following content to define the output path:
   ```plaintext
   -o "~/Downloads/yt-dlp/%(title)s.%(ext)s"
   ```

3. Save and exit (`Ctrl+O`, `Enter`, `Ctrl+X`).

Now, all downloaded files will be saved in `~/Downloads/yt-dlp` with their respective titles and extensions.

---

## Installation

### 1. Clone the Repository
```bash
git clone https://github.com/RoyRoki/YT-DLP-App.git
cd YT-DLP-App
```

### 2. Install Dependencies
#### Backend:
```bash
cd backend
npm install
```

#### Frontend:
```bash
cd ../
npm install
```

---

## Running the Application

### Start the Backend
Run the backend server:
```bash
cd backend
node server.js
```

### Start the Frontend
Run the React app:
```bash
cd ../
npm start
```

---

## Creating a Linux Application

### Step 1: Create a Shell Script
Write a script to start both the backend and frontend:
1. Create the script:
   ```bash
   nano ~/start-yt-dlp-app.sh
   ```

2. Add the following code:
   ```bash
   #!/bin/bash
   cd /home/roki/React/yt-dlp-app/backend
   nohup node server.js > /dev/null 2>&1 &
   
   cd /home/roki/React/yt-dlp-app
   nohup npm start > /dev/null 2>&1 &
   ```

3. Save and exit.

4. Make it executable:
   ```bash
   chmod +x ~/start-yt-dlp-app.sh
   ```

### Step 2: Create a Desktop Entry
Add a shortcut for easy access:
1. Create a `.desktop` file:
   ```bash
   nano ~/.local/share/applications/yt-dlp-app.desktop
   ```

2. Add the following content:
   ```plaintext
   [Desktop Entry]
   Type=Application
   Name=YT-DLP App
   Exec=/bin/bash -c "/home/roki/start-yt-dlp-app.sh"
   Icon=/home/roki/React/yt-dlp-app/public/slylogox.png
   Terminal=false
   Categories=Utility;
   ```

3. Save and exit.

4. Reload the application menu:
   ```bash
   update-desktop-database ~/.local/share/applications
   ```

---

## Stopping the Application
To stop the backend and frontend, find their process IDs and terminate them:
1. List running processes:
   ```bash
   ps aux | grep server.js
   ps aux | grep npm
   ```

2. Kill the processes:
   ```bash
   kill <PID>
   ```

---

## Contributing
Feel free to submit issues or pull requests to improve this project.

---