wireguard-tools
===============

Full documentation for manual Wireguard installation and configuration is available [here](https://gitlab.com/snippets/1897102).

wgcg.sh
-------

### About

This script is created to ease manual process of Wireguard configuration and will help you to automatically generate all the required configuration files (client and server), PKI key pairs and preshared key.

### Usage

Before start using it I would suggest updating default options, otherwise you will have to specify these options from the command line every time you're running the script.

```bash
export SERVER_NAME="wg0"                   # Specify any server name you like
export SERVER_WG_IP="10.0.0.1"             # VPN (WG) IP private address
export SERVER_PORT="52001"                 # Static server port
export SERVER_PUBLIC_IP="wg0.example.com"  # Server's public IP or FQDN
```

```bash
# ./wgcg.sh -h
Usage: wgcg.sh options

Options:
  -s|--server-config [server_name] [server_wg_ip] [server_port]
  -c|--client-config client_name client_wg_ip [server_name] [server_port] [server_public_ip]
  -q|--gen-qr-code config_name
```

Generate server keys and config

```bash
./wgcg.sh -s
```

Generate client keys, client config and update server config (add a new Peer)

```bash
./wgcg.sh -c foo 10.0.0.2
```