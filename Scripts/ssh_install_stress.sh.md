```
#!/bin/bash

REMOTE_USER="Guru"
PRIVATE_KEY_PATH="~/.ssh/id_rsa"

REMOTE_HOSTS=("10.0.0.7" "10.0.0.8" "10.0.0.9")

# Correct the permissions for the private key
chmod 600 "$PRIVATE_KEY_PATH"

# Install stress on remote hosts
for host in "${REMOTE_HOSTS[@]}"; do
    echo "Installing stress on $host..."
    ssh -i "$PRIVATE_KEY_PATH" "$REMOTE_USER@$host" "sudo apt update && sudo apt install -y stress"
done

# Run stress on remote hosts
for host in "${REMOTE_HOSTS[@]}"; do
    echo "Running stress on $host..."
    ssh -i "$PRIVATE_KEY_PATH" "$REMOTE_USER@$host" "sudo stress --cpu 1" &
done

wait
```
