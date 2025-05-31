
# Networking

## What is Networking?

- Networking is about connecting two or more devices with each other to communicate, share files, ideas, and beliefs.
- It is used for sharing data.

### Definition
- Networking is the interconnection of computers and devices that allows them to communicate and share resources, which we call a network.

## Types of Networks

1. **LAN (Local Area Network)**
   - Covers a small geographical area, such as a home, office, or campus.
   - High speed and relatively low cost.
   - Example: Office intranet.

2. **MAN (Metropolitan Area Network)**
   - Covers a city or metropolitan area.
   - Larger than a LAN but smaller than a WAN.
   - Example: City-wide Wi-Fi networks.

3. **WAN (Wide Area Network)**
   - Spans a large geographical area, connecting multiple LANs.
   - Example: The Internet.

4. **PAN (Personal Area Network)**
   - Focused on a single person’s devices.
   - Short range, usually within a few meters.
   - Example: Bluetooth connections.

5. **WLAN (Wireless LAN)**
   - A type of LAN that enables devices to connect and communicate wirelessly within a limited geographical area using radio frequency (RF) technology.
   - Example: Wi-Fi, Hotspot.

6. **VPN (Virtual Private Network)**
   - Provides secure access to a private network over a public network (Internet).
   - Uses encryption methods such as AES (Advanced Encryption Standard), RSA, and SHA (Secure Hash Algorithms).

## Networking Devices
- Devices used to connect with networks:
  - Routers
  - Switches
  - Repeaters
  - Gateways
  - Mesh

## Communication Protocols

1. **Unicast**
   - One-to-one communication within the same network.

2. **Multicast**
   - Communication from one to many groups/communities.

3. **Broadcast**
   - Transmits data from one sender to all devices over all networks.

4. **TCP/IP (Transmission Control Protocol/Internet Protocol)**
   - Enables communication between devices over the internet.
   - Provides a reliable, standardized method for data transmission.

5. **UDP (User Datagram Protocol)**
   - A connectionless communication method within the TCP/IP suite.
   - Suitable for applications where speed is critical and reliability is less important.

## Addressing

### IP (Internet Protocol)
- A unique address given to devices to identify them on a network.
- Two types:
  - **IPv4**: 32 bits (4 bytes)
  - **IPv6**: 128 bits (16 bytes)

### IPv4 Address Representation
- Example: 192.168.1.1
- Binary: 11000000.10101000.00000001.00000001

### Subnetting (Classes of IPv4)
- Used to identify:
  - Network ID
  - Host ID
- IPv4 classes:

| Class | IP Range | Default Subnet Mask | Hosts Per Network | Usage |
|-------|----------|----------------------|-------------------|-------|
| A     | 1.0.0.0 - 127.0.0.0 | 255.0.0.0 | 16,777,214 | Large organizations |
| B     | 128.0.0.0 - 191.255.0.0 | 255.255.0.0 | 65,534 | Medium to large organizations |
| C     | 192.0.0.0 - 223.255.255.0 | 255.255.255.0 | 254 | Small-scale networks |
| D     | 224.0.0.0 - 239.255.255.255 | N/A | N/A | Multicast communication |
| E     | 240.0.0.0 - 255.255.255.255 | N/A | N/A | Research and experimental |

### Loopback Addresses
- For internal testing and diagnostics.
- Range: 127.0.0.0 to 127.255.255.255
- Common address: 127.0.0.1 (localhost)

## Types of IP

1. **Public IP**
   - Assigned when connected to the internet.
   - Assigned by IANA (Internet Assigned Numbers Authority).

2. **Private IP**
   - Reserved for use within private networks.
   - Ranges:
     - Class A: 10.0.0.0 to 10.255.255.255
     - Class B: 172.16.0.0 to 172.31.255.255
     - Class C: 192.168.0.0 to 192.168.255.255

## Network Services

- **Service used**: `NetworkManager`
- **Configuration file**: `/etc/NetworkManager`

### Check Network Service
```bash
systemctl status NetworkManager
```

### Check IP Details
```bash
ifconfig
ip addr
nmcli connection show
```

## Network Management

### Ways to Configure Network
1. GUI
2. Command Line
3. GUI interface using command: `nmtui`

### Add New Network
```bash
nmcli connection add con-name "con-name" type ethernet ifname <ifname>
nmcli connection modify "con-name" ipv4.addresses <ip/subnet> ipv4.gateway <gateway> ipv4.dns <dns>
```

### Modify Existing Connection
```bash
nmcli connection modify "con-name" ipv4.address "ip/subnet"
nmcli connection modify "con-name" ipv4.dns "8.8.8.8" ipv4.gateway "192.168.1.2"
```

### Enable/Disable Network
```bash
nmcli connection up "con-name"
nmcli connection down "con-name"
```

### Delete Network
```bash
nmcli connection delete "con-name"
```

### Alternative Configuration
- Using config file:
```bash
/etc/NetworkManager/system-connections
```

### CLI with GUI Interface
```bash
nmtui
```

### Check Network Availability
```bash
ping <ip_address>
```

### Change Hostname
```bash
hostname <host_name>
```
