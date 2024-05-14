![Proxmox](https://www.casalicomputers.com/sites/default/files/proxmox-logo.png)
# PiPBS - Proxmox Backup Server for the Raspberry Pi
![arm64](https://img.shields.io/badge/architecture-arm64-9cf)
[![wofferl](https://img.shields.io/badge/wofferl-proxmox--backup--arm64-orange.svg)](https://github.com/wofferl/proxmox-backup-arm64)
![GitHub last commit](https://img.shields.io/github/last-commit/dexogen/pipbs)
![Workflow](https://github.com/dexogen/pipbs/actions/workflows/main.yml/badge.svg)
![GitHub Tag](https://img.shields.io/github/v/tag/wofferl/proxmox-backup-arm64)

Based on the excellent script of [wofferl](https://github.com/wofferl/proxmox-backup-arm64).

## Installation

### Set up the repository

1. Update the apt package index and install packages to allow apt to use a repository over HTTPS:
    ```bash
    apt update
    apt install -y ca-certificates curl gnupg lsb-release
    ```

2. Add GPG key:
    ```bash
    mkdir -p /etc/apt/keyrings
    curl -fsSL https://dexogen.github.io/pipbs/gpg.key | gpg --dearmor -o /etc/apt/keyrings/pipbs.gpg
    # or deprecated method
    curl -fsSL https://dexogen.github.io/pipbs/gpg.key | apt-key add -
    ```

3. Use the following command to set up the repository:
    ```bash
    echo "deb [arch=arm64 signed-by=/etc/apt/keyrings/pipbs.gpg] https://dexogen.github.io/test/ bookworm main" > /etc/apt/sources.list.d/pipbs.list
    ```

### Install Proxmox Backup Server

1. Update the `apt` package index:
    ```bash
    sudo apt update
    ```
2. Install packages:
    ```bash
    apt install -y raspberrypi-kernel-headers pv zfs-initramfs zfsutils-linux
    apt install -y proxmox-backup-server
    ```