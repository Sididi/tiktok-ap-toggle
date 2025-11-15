# tiktok-ap-toggle

Small repo to help manage and toggle a local Wi‑Fi access point (create_ap) for quick tethering. It allows to completely and safely isolate phones to use clean and individual mobile data for each, with one mother phone.
The whole goal is to create a "safe" environment to avoid any cross linkage between phones if you mess up inadvertently (share residential wifi instead of 5G, no 5G rotation, same SSID between phones which can trigger auto connects...)

This repository mirrors the local install under ~/.local

It was made for personal usage to manage cleanly multiple tiktok accounts. It is **not intended for automation or mass account creation** but to avoid cross linkage and have real, organic tiktok accounts with good "state".

## What `bin/tiktok-ap-toggle` does

- It's a shell script to toggle a hotspot on your laptop using `create_ap` or equivalent.
- It reads configuration from `share/ap-inter/ap-secrets.conf` (AP interface, SSIDs, PSKs, country, and optional IP blocks).
- It writes its last detected public upstream IP to `state/ap-inter/last_uplink_ip.txt`.
- It will refuse to start a hotspot if the detected uplink IP is in `RESIDENTIAL_UPLINK_BLOCK_IPS` (for safety).

## Important: secrets and state

- `share/ap-inter/ap-secrets.conf` contains the SSID and (locally filled) PSK variables. The public copy in this repository intentionally leaves PSKs empty. Fill them locally and do not commit your real PSKs.
- `state/ap-inter/last_uplink_ip.txt` is runtime state. It contains a placeholder IP in the public repo. Do not commit your real upstream IPs to a public repository.

---

This README and the repo are intended for educational or personal use — be mindful of local laws and Wi‑Fi usage policies.
