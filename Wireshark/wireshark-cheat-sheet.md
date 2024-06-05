Concise cheat sheet for using Wireshark to analyze captured traffic.

### Wireshark Basics

- **Interface Selection**: Choose the correct network interface to start capturing packets.
  - `Capture > Options` or `Capture > Interfaces`

- **Starting/Stopping Capture**:
  - Start: Click the blue shark fin button or `Capture > Start`.
  - Stop: Click the red square button or `Capture > Stop`.

- **Open Capture Files**:
  - `File > Open` to open a previously saved capture file (`.pcap` or `.pcapng`).

### Display Filters

- **Basics**:
  - Syntax: `<protocol>.<field> <operator> <value>`
  - Examples:
    - `ip.addr == 192.168.1.1`: Filter packets from/to IP address 192.168.1.1.
    - `tcp.port == 80`: Filter packets using TCP port 80 (HTTP).
    - `http`: Display only HTTP packets.

- **Common Filters**:
  - `tcp`: Display only TCP packets.
  - `udp`: Display only UDP packets.
  - `dns`: Display only DNS packets.
  - `icmp`: Display only ICMP packets.

### Follow Streams

- **TCP Stream**:
  - Right-click on a packet and select `Follow > TCP Stream` to see the complete TCP conversation.
- **UDP Stream**:
  - Right-click on a packet and select `Follow > UDP Stream`.

### Packet Details

- **Inspecting Packets**:
  - Expand the packet details pane to see the hierarchical structure of the packet.
  - Layers: Frame, Ethernet, IP, TCP/UDP, Application Layer (e.g., HTTP, DNS).

### Common Analysis Tasks

- **Finding Errors**:
  - Use filters to find retransmissions and errors:
    - `tcp.analysis.retransmission`
    - `tcp.analysis.flags`

- **DNS Queries**:
  - Filter DNS traffic: `dns`
  - Inspect queries and responses for domain name resolution issues.

- **HTTP Analysis**:
  - Filter HTTP traffic: `http`
  - Examine requests and responses, headers, and payload data.

### Exporting Data

- **Export Packets**:
  - `File > Export Specified Packets` to save filtered packets to a new file.
- **Export Objects**:
  - `File > Export Objects` to save files transferred over protocols like HTTP.

### Graphical Tools

- **IO Graphs**:
  - `Statistics > I/O Graphs` to visualize traffic over time.
- **Protocol Hierarchy**:
  - `Statistics > Protocol Hierarchy` to see a breakdown of protocols in the capture.

### Useful Shortcuts

- **Start/Stop Capture**: `Ctrl+E`
- **Restart Capture**: `Ctrl+R`
- **Open File**: `Ctrl+O`
- **Save File**: `Ctrl+S`
- **Display Filter**: `Ctrl+` + `Enter`
- **Find Packet**: `Ctrl+F`

### Practical Tips

- **Coloring Rules**: Use `View > Coloring Rules` to differentiate packet types visually.
- **Marking Packets**: Mark important packets with the right-click menu (`Mark/Unmark Packet`).
- **Time Reference**: Set a packet as a time reference to measure relative timings.

### Example Filters for Common Tasks

- **Display Only HTTP Traffic**:
  - `http`
- **Find Packets with a Specific IP Address**:
  - `ip.addr == 10.0.0.1`
- **Filter for a Specific TCP Port**:
  - `tcp.port == 443` (for HTTPS)
- **Show Packets with Errors**:
  - `tcp.analysis.flags`

### Additional Resources

- **Wireshark User Guide**: Accessible via `Help > User's Guide`.
- **Wireshark Wiki**: Extensive documentation and community support.
