```
#!/bin/bash

# List of remote hosts
REMOTE_HOSTS=("10.0.0.7" "10.0.0.8" "10.0.0.9")

NUM_REQUESTS=500

# Perform web requests and delete index.html file
for host in "${REMOTE_HOSTS[@]}"; do
    for ((i=1; i<=NUM_REQUESTS; i++)); do
        echo "Making web request $i to http://$host"
        wget -q "http://$host" -O index.html
        rm index.html
    done
done
```
