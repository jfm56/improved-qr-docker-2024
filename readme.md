# Docker + Python QR Code Generator

## Overview

This project uses Docker to containerize a Python script that generates a QR code image pointing to my GitHub profile. The QR code is generated using the `qrcode` and `Pillow` libraries in Python. The script accepts environment variables for the URL and optional styling customization.

---

## How It Works

- Docker is used to build and run a containerized Python environment.
- The script reads the `QR_DATA_URL` environment variable.
- It generates a PNG image containing a QR code for the specified URL.
- You can scan the QR code using your phone’s camera to be taken to the GitHub page.

---

## Generated QR Code

Scan this QR code to visit my GitHub profile:

![QR Code to GitHub](qr_codes/QRCode_20250330015947.png)

---

## QR Code Generation Log

Below is a screenshot of the successful output log from the Docker container, confirming the QR code was created:

## QR Code Generation Log

![QR Code Generation Log](log.png)

---

## Docker Commands Used

```bash
# Build Docker image
docker build -t my-qr-app .

# Run Docker container with environment variables and volume mount
docker run -d --name qr-generator \
  -e QR_DATA_URL='https://github.com/jfm56' \
  -v $(pwd)/qr_codes:/app/qr_codes \
  my-qr-app

# View logs
docker logs qr-generator
