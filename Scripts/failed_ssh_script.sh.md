```
#!/bin/bash

REMOTE_USER="admin"

# List of remote hosts
REMOTE_HOSTS=("10.0.0.7" "10.0.0.8" "10.0.0.9" "10.1.0.5")
NUM_ATTEMPTS=500

for host in "${REMOTE_HOSTS[@]}"; do
    for ((i=1; i<=NUM_ATTEMPTS; i++)); do
        echo "Attempt $i for $host:"
        ssh "$REMOTE_USER@$host" 2>/dev/null &
    done
    wait
done
```
