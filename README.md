# TCP Reverse Shell with Python

This project is a simple TCP reverse shell application built using Python. It includes both a server-side GUI and a client-side script, allowing you to interact with a remote client over a TCP connection. The application supports various features such as file transfer, command execution, and more.

## Features

- **File Operations**: Send and receive files from the client.
- **Command Execution**: Execute commands on the client machine and view the results.
- **Screen Capture**: Capture screenshots from the client machine.
- **Port Scanning**: Scan ports on the client's IP address.
- **Wi-Fi Scan**: Scan available Wi-Fi networks on the client machine.
- **File Search**: Search for files on the client machine.
- **Key Logging**: Record keystrokes on the client machine.
- **Clipboard Monitoring**: Retrieve clipboard contents from the client machine.
- **Browse History**: Retrieve browsing history from the client machine.

## Installation

To run this application, you need Python and a few additional libraries. Follow these steps to set up the environment:

### Clone the Repository

```bash
git clone https://github.com/SB1450/Python-Reverse-Shell
cd Python-Reverse-Shell
```

### Install Dependencies

Ensure you have Python 3.x installed. Then, install the required libraries:

```bash
pip install pycryptodome pynput pyperclip browser-history pillow
```

## Usage

### Server Side

#### Run the Server

Start the server application by running the following command:

```bash
python server.py
```

This will open a Tkinter GUI window. The server will listen for incoming connections on and port `8080`. You may need to adjust these values depending on your network configuration.

#### Using the GUI

- **Send Command**: Enter commands in the text box and press "Send Command" or press Enter.
- **Send File**: Click "Send File ..." to select and send a file to the client.
- **Grab File**: Click "Grab ..." to list and retrieve files from the client.
- **Screen Capture**: Click "Screen Capture" to capture a screenshot from the client.
- **Port Scan**: Click "Scan Ports" and enter the target IP and ports to scan.
- **Wi-Fi Scan**: Click "Scan Wifis" to scan available Wi-Fi networks.
- **Search Files**: Click "Search Files" to search for files with a specific extension.
- **Key Logger**: Click "Key Logger" to start keylogging on the client.
- **Clipboard**: Click "Clipboard" to retrieve the client's clipboard contents.
- **Browse History**: Click "Browse History" to retrieve the client's browsing history.



## Client-Side Script Overview

The client-side script is designed to operate as part of a client-server architecture, where it interacts with a server to execute commands and perform various tasks on the client machine. The script provides functionalities like file management, system monitoring, and data retrieval. Below is a detailed description of the script's features and how to use it.

### Key Features

#### **1. Initial Setup and Configuration**
- **File Copying and Conversion**: The script first creates a backup of itself, removes the first line of the script (presumably containing sensitive information or metadata), and converts it into an executable file using `pyinstaller`. This executable is then copied to the user's Documents folder.
- **Startup Registration**: The script registers itself to run on system startup by modifying the Windows registry.

#### **2. Encryption and Decryption**
- **AES Encryption**: The script uses AES encryption to secure communication between the client and server. It supports both encryption and decryption of messages to ensure data confidentiality.
- **RSA Decryption**: RSA keys are used to decrypt the AES key received from the server.

#### **3. File and Data Management**
- **File Transfer**: The client can upload or download files from the server. It includes functionality to check if a file exists, transfer its content, and save received files to the local filesystem.
- **Command Execution**: The script can execute shell commands and return their output or errors to the server.

#### **4. System Information and Monitoring**
- **Port Scanning**: The script can scan specified ports on a target IP address to determine if they are open or closed.
- **WiFi Information**: It retrieves and reports saved WiFi profiles and their passwords.
- **Keylogging**: The script logs keystrokes and sends the recorded data to the server.
- **Clipboard Monitoring**: It monitors and logs clipboard content.
- **Browser History**: The script extracts and sends the browser history in CSV format.

#### **5. Screenshot Capture**
- **Screen Capture**: The client can take screenshots of the desktop and transfer the image file to the server.

### How to Use

1. **Setup and Execution**:
   - Place the script on the client machine.
   - Ensure that Python and required libraries (`pyinstaller`, `pynput`, `pyperclip`, `browser_history`, `pycryptodome`, `Pillow`) are installed.
   - Run the script using Python. It will handle initial setup tasks such as creating an executable and registering itself to run on startup.

2. **Interaction with Server**:
   - The client connects to the server at the specified IP address and port.
   - Once connected, the client listens for commands from the server and executes them. Commands can include file operations, system scans, and data retrieval tasks.

3. **Commands Overview**:
   - **`grab*<path>`**: Uploads a specified file to the server.
   - **`send*<file>`**: Downloads a file from the server and saves it to the client machine.
   - **`cd*<directory>`**: Changes the current working directory on the client machine.
   - **`screencap`**: Takes a screenshot and uploads it to the server.
   - **`wifi`**: Scans for saved WiFi networks and their passwords.
   - **`scan*<ip>:<ports>`**: Scans the specified ports on the given IP address.
   - **`search*<path>*<ext>`**: Searches for files with the specified extension in the given path.
   - **`key`**: Logs keystrokes and uploads the log file.
   - **`clipboard`**: Monitors and logs clipboard contents.
   - **`history`**: Extracts and uploads browser history.

4. **Termination**:
   - To stop the client, the server can send a `terminate` command. The client will then disconnect and cease operations.

### Important Considerations

- **Ethical Use**: This script should only be used in environments where you have explicit permission to do so. Unauthorized use can be illegal and unethical.
- **Dependencies**: Ensure all required libraries are installed and that the script paths are correctly set up.
