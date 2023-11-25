# VivoBook 15 X509DA Battery Threshold Setter for Ubuntu 22.04 LTS

## Overview

This repository contains a systemd service for setting the battery charge control end threshold on the Asus VivoBook 15 X509DA model running Ubuntu 22.04 LTS. The purpose is to automatically configure the battery threshold when the system starts.

## Table of Contents

- [Installation](#installation)
- [Configuration](#configuration)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)

## Installation

1. Clone the repository to your ASUS VivoBook 15 X509DA running Ubuntu 22.04 LTS:

    ```bash
    git clone https://github.com/mrankitvish/vivobook-x509da-battery-threshold-setter.git
    cd vivobook-x509da-battery-threshold-setter
    ```

2. Copy the systemd service file to the appropriate location:

    ```bash
    sudo cp battery_threshold.service /etc/systemd/system/
    ```

3. Reload systemd:

    ```bash
    sudo systemctl daemon-reload
    ```

4. Enable the service to start on boot:

    ```bash
    sudo systemctl enable battery_threshold.service
    ```

5. Start the service:

    ```bash
    sudo systemctl start battery_threshold.service
    ```

## Configuration

Edit the `ExecStart` line in the `battery_threshold.service` file to set your desired battery charge control end threshold:

```ini
[Service]
Type=oneshot
ExecStart=/bin/bash -c 'echo "80" | tee /sys/class/power_supply/BAT0/charge_control_end_threshold'
RemainAfterExit=yes
