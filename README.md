# DHCP-Reservation-Script
A Bash tool that performs manual DHCP address requests by dynamically probing the network, discovering its prefix, and requesting a specific IP via DHCP Option 50. Built for networking labs and VMware environments.

A Bash script that manually interacts with DHCP servers to:
- Probe the current network and learn its prefix.
- Ask the user for a custom host portion (last octet).
- Send a DHCP request for that specific IP address (Option 50).
- Display whether the server accepted the request.
Originally developed for VMware NAT / Host-Only labs on Red Hat Enterprise Linux 8.


## Features
- Discovers network prefix automatically.
- Builds a requested IP dynamically (`prefix + last_octet`).
- Generates temporary `dhclient.conf` files to control DHCP behavior.
- Prints full debug output for learning or troubleshooting.
- Works great for virtual lab environments or DHCP testing.
