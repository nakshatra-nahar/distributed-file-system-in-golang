# Peer-to-Peer Content Addressable Distributed File System (CADFS)

## Overview

This project implements a **Content Addressable Distributed File System (CADFS)**, leveraging peer-to-peer technology for efficient, encrypted, and fault-tolerant file storage and retrieval. Unlike conventional file systems that rely on hierarchical paths or filenames, CADFS uses **content-based addressing** to identify and access files based on their content. Built with Go, this system includes a custom peer-to-peer networking library on top of TCP, designed from scratch to enable chunk-based file streaming. This allows for efficient transmission of large files across a network of peers.

## Key Features

- **Encryption and Decryption**: Files are securely encrypted during storage and transmission.
- **Content Addressable Storage**: Files are identified and located based on their content rather than traditional filenames or paths.
- **Peer-to-Peer Distributed Storage**: Files are stored across a distributed network of nodes (peers), ensuring scalability and efficiency.
- **Data Redundancy**: Multiple copies of files are maintained across peers to provide fault tolerance and reliability.
- **Data Streaming**: Large files are split into smaller chunks and streamed across the network for efficient data exchange.

## Getting Started

### Prerequisites

Before running the project, ensure that Go is installed on your machine. You can install Go from the official [Go website](https://go.dev/doc/install). The project has been tested and built with Go version `1.22.2`.

### Installation and Setup

To get started with this project, follow these steps:

1. **Clone the Repository**  
   First, clone this repository to your local machine:
   ```bash
   git clone https://github.com/your-username/cadfs.git
   cd cadfs
   ```

2. **Install Dependencies**  
   After cloning the repository, install the necessary dependencies by running:
   ```bash
   go mod tidy
   ```

3. **Run the Project**  
   To run the project, you can use the `Makefile` provided. This will initialize three peers, with one acting as the primary node that broadcasts files to the others.
   ```bash
   make run
   ```

   Upon successful execution, three directories will be created in the root of the project:
   - `:3000_network`
   - `:4000_network`
   - `:5000_network`

   These directories represent the local file storage for the peers running on ports 3000, 4000, and 5000, respectively. The peer on port 4000 will create five files and distribute them across the network for redundancy.

## How It Works

- **Content Addressing**: Files are hashed and stored based on their unique content hash, making it easy to retrieve files no matter where they are stored in the network.
- **Encryption**: All files are encrypted before transmission and storage, ensuring that data remains secure during transit and at rest.
- **File Chunking**: Large files are broken down into smaller, manageable chunks and transmitted across the network in pieces. Once all chunks are received, they are reassembled at the destination.
- **Data Redundancy**: Each file is replicated and stored on multiple peers. In case a peer goes offline, the system ensures that the file is still available by retrieving it from other peers.
- **Fault Tolerance**: Due to data redundancy, the system can withstand node failures, ensuring that no data is lost when a peer goes down.

## Contributing

We welcome contributions to improve this project! Feel free to open issues or submit pull requests to propose new features, fix bugs, or enhance documentation.

To contribute:
1. Fork the repository.
2. Create a new branch for your feature or bugfix.
3. Submit a pull request with a detailed description of your changes.

## License

This project is licensed under the [MIT License](https://opensource.org/license/mit). See the `LICENSE` file for full details.
