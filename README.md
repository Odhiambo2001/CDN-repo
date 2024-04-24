# CDN-repo

 Content Delivery Network (CDN) Implementation

This repository contains the implementation of a simple CDN using DNS redirection and an HTTP server with cache management. The CDN is designed to serve content with optimized response time by choosing the replica server with the fastest access time for each client.

Table of Contents

System Overview(system-overview)
Requirements(requirements)
Installation(installation)
Configuration(configuration)
Running the CDN(running-the-cdn)
Testing(testing)
Support(support)

System Overview

The CDN consists of the following components:
DNS Server: Directs clients to the most appropriate replica server based on response time.
HTTP Server: Serves requests for content, retrieving data from either a local cache or the origin server.
Cache Management: Handles the storage and retrieval of cached content, implementing an efficient cache replacement strategy.
Deployment Scripts: Scripts for deploying, running, and stopping the CDN across multiple servers.


Requirements

- Linux or UNIX-like operating system or Windows environment
- Python 3.7 or higher
- Access to multiple servers for deploying the CDN components
- Network access to the origin server for content fetching

Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/yourcdnproject.git
   cd yourcdnproject
   ```
2. Install required Python libraries:
   ```bash
   pip install -r requirements.txt
   ```
Configuration
- DNS Server Configuration:
  Modify `config/dns_config.json` to set the IP addresses of the replica servers and the port number.
  
- HTTP Server Configuration:
  Update `config/http_config.json` to specify the cache size and the origin server's address.

- Deployment Settings:
  Edit the `deployCDN`, `runCDN`, and `stopCDN` scripts with the appropriate server addresses, usernames, and key file paths.
 Running the CDN

1. Deploy the CDN:
   ```bash
   ./deployCDN -p [port] -o [origin] -n [name] -u [username] -i [keyfile]
   ```
2. Run the CDN:
   ```bash
   ./runCDN -p [port] -o [origin] -n [name] -u [username] -i [keyfile]
   ```
3. Stop the CDN:
   ```bash
   ./stopCDN -p [port] -u [username] -i [keyfile]
   ```
 Testing

Test DNS Resolution:
  ```bash
  dig @<DNS server IP> -p <port> cs5700cdn.example.com
  ```
Test Content Fetching:
  ```bash
  time wget http://<replica server IP>:<port>/path/to/content
  ```
- Use the beacon monitoring tool provided at https://site.cdn-beacon.khoury.northeastern.edu/ to view performance data and system logs.


