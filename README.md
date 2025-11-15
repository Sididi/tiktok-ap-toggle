# tiktok-ap-toggle

Small repo to help manage and toggle a local Wi‑Fi access point (create_ap) for testing and quick tethering.

This repository mirrors the local install under ~/.local on the author machine (Arch Linux). When pushing to GitHub be careful NOT to publish secrets (PSKs, IP addresses, etc.).

## What `bin/tiktok-ap-toggle` does

- It's a shell script to toggle a hotspot on your laptop using `create_ap` or equivalent.
- It reads configuration from `share/ap-inter/ap-secrets.conf` (AP interface, SSIDs, PSKs, country, and optional IP blocks).
- It writes its last detected public upstream IP to `state/ap-inter/last_uplink_ip.txt`.
- It will refuse to start a hotspot if the detected uplink IP is in `RESIDENTIAL_UPLINK_BLOCK_IPS` (for safety).

## Important: secrets and state

- `share/ap-inter/ap-secrets.conf` contains the SSID and (locally filled) PSK variables. The public copy in this repository intentionally leaves PSKs empty. Fill them locally and do not commit your real PSKs.
- `state/ap-inter/last_uplink_ip.txt` is runtime state. It contains a placeholder IP in the public repo. Do not commit your real upstream IPs to a public repository.

## How to push (short instructions)

1. Make sure `share/ap-inter/ap-secrets.conf` does not contain real PSKs.
2. Make sure `state/ap-inter/last_uplink_ip.txt` contains a test or empty value.
3. Create a GitHub repository named `tiktok-ap-toggle` and push your repo:

   git init
   git add .
   git commit -m "Initial sanitized repo"
   # create repository on GitHub and follow the URL below
   git remote add origin git@github.com:<your-username>/tiktok-ap-toggle.git
   git push -u origin main

4. Keep your local PSKs secret — a recommended pattern is to add the secrets file to `.gitignore` and keep an example file in the repo.

## Local developer tip

If you use this repo across machines you might use a private config file such as `share/ap-inter/ap-secrets.conf.local` and add it to `.gitignore` so your personal keys never touch the repo.

---
This README and the repo are intended for educational or personal use — be mindful of local laws and Wi‑Fi usage policies.
