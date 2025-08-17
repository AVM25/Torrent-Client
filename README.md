# BitTorrent Client

## What is this?
A fully functional BitTorrent client built from scratch using **Node.js** to implement the complete peer-to-peer file sharing protocol. The client connects to UDP trackers and downloads files from multiple peers concurrently using TCP connections.

## Features
- **Complete BitTorrent Protocol Implementation** - Full compliance with BEP specifications
- **UDP Tracker Support** - Efficient low-overhead tracker communication
- **Multi-peer Downloading** - Concurrent connections for maximum throughput  
- **Piece Validation** - SHA-1 hash verification for data integrity
- **Progress Tracking** - Real-time download progress monitoring
- **Error Recovery** - Robust connection handling and retry mechanisms

## Technical Implementation
- **Bencode Parser** - Custom decoder for torrent file format
- **Peer Wire Protocol** - Complete message suite (handshake, choke, unchoke, have, bitfield, request, piece)
- **Block-level Management** - 16KB block chunking for memory efficiency
- **Connection Pooling** - Asynchronous I/O with multiple simultaneous peer connections

## Architecture
```
├── index.js              # Main entry point
├── src/
│   ├── torrent-parser.js  # Torrent file parsing and metadata extraction
│   ├── tracker.js         # UDP tracker communication protocol
│   ├── download.js        # Main download coordination and peer management
│   ├── message.js         # BitTorrent peer wire protocol messages
│   ├── Pieces.js          # Piece and block state management
│   ├── Queue.js           # Download queue and request scheduling
│   └── util.js            # Utility functions and peer ID generation
```

## Development Setup

Clone the repository:
```sh
git clone https://github.com/AVM25/Torrent-Client.git
cd bittorrent-client
```

Install dependencies:
```sh
npm install
```

Run the client:
```sh
node index.js <path-to-torrent-file>
```

## Dependencies
- **bencode**: BitTorrent encoding/decoding
- **bignum**: Large number handling for file sizes

## Protocol Specifications
This implementation follows official BitTorrent Enhancement Proposals:
- **BEP 3**: Core BitTorrent Protocol
- **BEP 15**: UDP Tracker Protocol

## How It Works
1. **Parse Torrent**: Decodes `.torrent` file to extract tracker URL, file info, and piece hashes
2. **Tracker Query**: Connects to UDP tracker to get peer list
3. **Peer Handshake**: Establishes TCP connections with peers using BitTorrent protocol
4. **Download Coordination**: Requests file pieces from multiple peers simultaneously
5. **File Assembly**: Validates and writes received blocks to reconstruct original files

## License
MIT License - Feel free to use and modify for educational purposes.
