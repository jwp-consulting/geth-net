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

Put the nonce and bootnode URL in the hosts file like so

```
[geth_node]
X.X.X.X nonce={16 hex character} boo
```

Run the playbook

```
ansible-playbook site.yml -i hosts
```

# Reference

https://media.consensys.net/how-to-build-a-private-ethereum-blockchain-fbf3904f337
