# geth-node

Create a hosts file like so

```ini
[geth_node]
X.X.X.X nodename={node name}

[geth_node:vars]
domain={domain for caddy reverse proxy}
```

Run the playbook

```
ansible-playbook site.yml -i hosts
```

# enode

How to retrieve your enode number

```
journalctl -u geth | grep enode | grep -o -E 'enode://.+discport=0'
```

# Reference

https://media.consensys.net/how-to-build-a-private-ethereum-blockchain-fbf3904f337
