# How to Install NVM on Ubuntu: Step-by-Step Guide

## Prerequisites

- **Operating System**: Active Ubuntu 20.04 server environment ready for installation.
- **Package Manager**: Ensure the `apt` package manager is installed on your Ubuntu system.
- **Curl**: The `curl` command-line tool should be installed. If not, install it using: `sudo apt install curl`.
- **Access**: Administrative privileges or sudo access.

## Installation Steps

1. **Update the System**:

   ```bash
   sudo apt update
   ```

2. **Download and Install NVM**:

   ```bash
   curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
   ```

3. **Verify NVM Installation**:

   ```bash
   nvm --version
   ```

4. **Install Node.js Using NVM**:

   - Install the latest version of Node.js:
     ```bash
     nvm install node
     ```
   - Verify the Node.js installation:
     ```bash
     node --version
     ```
   - Install the current LTS version of Node.js:
     ```bash
     nvm install --lts
     ```
   - Install a specific Node.js version (e.g., 11.5):
     ```bash
     nvm install 11.5
     ```

5. **Managing Node.js Versions**:

   - List installed Node.js versions:
     ```bash
     nvm ls
     ```
   - Switch between installed Node.js versions (e.g., to version 14.10.0):
     ```bash
     nvm use v14.10.0
     ```
   - Uninstall a specific Node.js version (e.g., version 11.5):
     ```bash
     nvm uninstall 11.5
     ```

6. **Update NVM to the Latest Version**:

   ```bash
   curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/$(curl -s https://api.github.com/repos/nvm-sh/nvm/releases/latest | grep 'tag_name' | cut -d\" -f4)/install.sh | bash
   ```

7. **Uninstall NVM**:
   - Remove the NVM directory:
     ```bash
     rm -rf ~/.nvm
     ```

## Conclusion

NVM is a critical tool for managing multiple Node.js versions on Ubuntu systems. By following the above steps, developers can install and manage various versions of Node.js to suit their project needs.

## Script for Executable Commands

### script 1: basic installation - latest version of Node.js

file name - `install_nvm_latest.sh`

```bash
echo '#!/bin/bash

# Source NVM from typical initialization locations
if [ -s "$HOME/.nvm/nvm.sh" ]; then
  source "$HOME/.nvm/nvm.sh" 
elif [ -s "$HOME/.bashrc" ]; then
  source "$HOME/.bashrc"      
elif [ -s "$HOME/.zshrc" ]; then
  source "$HOME/.zshrc"       
fi

# Check if nvm is installed
if ! type nvm > /dev/null 2>&1; then
  echo "NVM is not installed. Installing now..."
  echo "Updating system..."
  sudo apt update

  echo "Installing NVM..."
  curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash

  echo "NVM installed successfully. Please restart your terminal or run the script again."
  exit 1
else
  echo "NVM is already installed."
fi

echo "Verifying NVM installation..."
nvm --version

echo "Installing the latest version of Node.js..."
nvm install node

echo "Listing installed Node.js versions..."
nvm ls' > install_nvm_latest.sh
```


Ensure you have the necessary permissions to execute the script, and you may need to modify the executable permissions with `chmod +x filename.sh` before running it.




