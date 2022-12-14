![Proxmox](https://www.casalicomputers.com/sites/default/files/proxmox-logo.png)
# PiPBS - Proxmox Backup Server for the Raspberry Pi
![arm64](https://img.shields.io/badge/architecture-arm64-9cf)
[![wofferl](https://img.shields.io/badge/wofferl-proxmox--backup--arm64-orange.svg)](https://github.com/wofferl/proxmox-backup-arm64)
![GitHub last commit](https://img.shields.io/github/last-commit/dexogen/pipbs)

Based on the excellent script of [wofferl](https://github.com/wofferl/proxmox-backup-arm64).

## Installation

### Set up the repository

1. Update the apt package index and install packages to allow apt to use a repository over HTTPS:
    ```bash
    sudo apt-get update
    sudo apt-get install \
        ca-certificates \
        curl \
        gnupg \
        lsb-release
    ```

2. Add GPG key:
    ```bash
    sudo mkdir -p /etc/apt/keyrings
    curl -fsSL https://dexogen.github.io/pipbs/main/pipbs.gpg | sudo gpg --dearmor -o /etc/apt/keyrings/pipbs.gpg
    # OR 
    curl -SsL https://dexogen.github.io/pipbs/main/pipbs.gpg | sudo apt-key add -
    ```

3. Use the following command to set up the repository:
    ```bash
    sudo curl -SsL -o /etc/apt/sources.list.d/pipbs.list https://dexogen.github.io/pipbs/main/pipbs.list
    ```

### Install Proxmox Backup Server

1. Update the `apt` package index:
    ```bash
    sudo apt-get update
    ```
2. Install packages:
    ```bash
    sudo apt-get install raspberrypi-kernel-headers pv zfs-initramfs zfsutils-linux
    sudo apt-get install proxmox-backup-server
    ```

## ToDo
- Automatic build (periodic or based on changes in the main repository)
