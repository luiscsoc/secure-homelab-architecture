# My Secure Home Lab Journey 🏠🔒

## Project Overview
I decided to build my own home lab from scratch to apply my networking and 
security knowledge in a real-world environment. My goal was to create a 
secure, private infrastructure that I could access remotely without exposing 
my home network to the internet.

## Building the Infrastructure
I started with a basic PC (Intel Pentium, 4GB RAM) and installed **Debian Linux**. 
After setting up the base OS, I configured a segmented local network and deployed 
several services to make the server useful for my daily life:
- **Nextcloud + Apache2:** To host my own private cloud and file sharing.
- **Samba:** To create a local file server with restricted access.
- **AdGuard Home:** To set up a network-wide DNS sinkhole and block trackers.

## Security Hardening & Problem Solving
Security was my main priority during this project. Here is what I implemented:
1. **Secure Remote Access:** Instead of opening ports on my router (which is dangerous) 
I deployed **Tailscale VPN**. I configured it with `--accept-dns=false` to prevent DNS 
leaks and maintain my local resolution.
2. **Firewall Configuration:** I used **UFW** to block all inbound traffic by default, 
allowing only SSH (22) and HTTP/HTTPS (80/443).
3. **SSH Hardening:** I disabled root login and moved to a specific user with sudo 
privileges to reduce the attack surface.

## Lessons Learned (The Hard Way)
- **DNS Nightmares:** I spent hours troubleshooting a DNS conflict between 
`systemd-resolved` and Tailscale that was breaking my internet connection. 
I learned how to properly manage and debug DNS resolution.
- **Network Management:** I learned how to configure static IPs and 
manage Wi-Fi connections using `nmcli` in the terminal.
- **Secure HTTPS:** I successfully set up certificate-based HTTPS access 
using Tailscale Serve, avoiding the complexity of manually managing SSL certificates.
