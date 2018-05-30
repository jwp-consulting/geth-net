# geth-private-network

Deploy a private geth network on Debian

# Nonce Generation

```
openssl rand -hex 8
```

SSH into the node, retrieve the enode URL. This will be the bootnode enode for
the other node.

```
journalctl -u geth | grep enode | grep -o -E 'enode://.+discport=0'
```

For `[::]`, fill in the IP of the other node

Put the nonce, nodename and allocation Ethereum address in the hosts file like so

```ini
[geth_node]
X.X.X.X nodename={node name}

[geth_node:vars]
bootnode=enode://{pubkey}@{ip}:30303?discport=0
nonce=0x{16 hex character}
alloc_address=0x{ether address}
networkid={integer}
domain={domain for caddy reverse proxy}
```

Run the playbook

```
ansible-playbook site.yml -i hosts
```

# Reference

https://media.consensys.net/how-to-build-a-private-ethereum-blockchain-fbf3904f337
