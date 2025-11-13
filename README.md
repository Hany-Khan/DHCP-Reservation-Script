# DHCP-Reservation-Script
A Bash tool that performs manual DHCP address requests by dynamically probing the network, discovering its prefix, and requesting a specific IP via DHCP Option 50. Built for networking labs and VMware environments.

A Bash script that manually interacts with DHCP servers to:
- Probe the current network and learn its prefix.
- Ask the user for a custom host portion (last octet).
- Send a DHCP request for that specific IP address (Option 50).
- Display whether the server accepted the request.
Originally developed for VMware NAT / Host-Only labs on Red Hat Enterprise Linux 8.

---

## Features
- Discovers network prefix automatically.
- Builds a requested IP dynamically (`prefix + last_octet`).
- Generates temporary `dhclient.conf` files to control DHCP behavior.
- Prints full debug output for learning or troubleshooting.
- Works great for virtual lab environments or DHCP testing.

---

# Usage
- Create the script file:
touch dhcpreserveration.sh
- Give the file executable permissions
chmod +x dhcpreservation.sh
- Edit the file and paste the configurations from script.txt
- You’ll be asked for the last octet you want
- Run script
sudo ./dhcp_requester.sh

---
# Example Output:

=== DHCP Reservation Script ===

Cleaning up old dhclient processes...
Removed stale PID file
Internet Systems Consortium DHCP Client 4.3.6
Copyright 2004-2017 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/ens160/00:0c:29:5f:b7:ac
Sending on   LPF/ens160/00:0c:29:5f:b7:ac
Sending on   Socket/fallback
[-] Killing existing dhclient PID 44495
./dreserv2.sh: line 19: kill: (44495) - No such process

What would you like the host portion to be assuming we are using a /24?: 20

Preparing/Cleaning the interface...
Error: Device 'ens160' (/org/freedesktop/NetworkManager/Devices/2) disconnecting failed: This device is not active
Error: not all devices disconnected.

Sending DHCP probe to learn network prefix...
Network portion is: 192.168.109.0/24
Target address is: 192.168.109.20

Creating custom DHCP request config...
Requesting address 192.168.109.20 from DHCP server...
Removed stale PID file
Internet Systems Consortium DHCP Client 4.3.6
Copyright 2004-2017 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/ens160/00:0c:29:5f:b7:ac
Sending on   LPF/ens160/00:0c:29:5f:b7:ac
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client 4.3.6
Copyright 2004-2017 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/ens160/00:0c:29:5f:b7:ac
Sending on   LPF/ens160/00:0c:29:5f:b7:ac
Sending on   Socket/fallback
DHCPREQUEST on ens160 to 255.255.255.255 port 67 (xid=0x47235d15)
DHCPACK from 192.168.109.134 (xid=0x47235d15)
bound to 192.168.109.20 -- renewal in 707 seconds.

New address is: 192.168.109.20

=== Script Finished ===
