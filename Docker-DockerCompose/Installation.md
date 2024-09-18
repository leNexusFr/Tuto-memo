

# Ubuntu/Debian
## Docker

This script automates the complete installation of Docker on an **Ubuntu/Debian** system, following the steps recommended by the official Docker documentation. 
It configures the system to use the official Docker repositories, ensuring that the **latest stable version** is installed.

🤜 Copy and paste this command into your terminal and run it.
 
```
echo '#!/bin/bash

sudo apt-get update && sudo apt-get install -y \
    ca-certificates \
    curl \
    gnupg \
    lsb-release

sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update -y
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-compose-plugin' > install_docker.sh && chmod +x install_docker.sh && sudo ./install_docker.sh && sudo .rm ./install_docker.sh
```

## Docker-Compose

This script automates the complete installation of Docker Compose on an **Ubuntu/Debian** system, following the steps recommended by the official Docker documentation. 
It configures the system to use the official Docker repositories, ensuring that the **latest stable version** is installed.

🤜 Copy and paste this command into your terminal and run it.

```
echo '#!/bin/bash

VERSION=$(curl --silent https://api.github.com/repos/docker/compose/releases/latest | grep -Po '"'"'"tag_name": "\K.*\d'"'"')
echo ${VERSION}

DESTINATION=/usr/local/bin/docker-compose

sudo curl -L https://github.com/docker/compose/releases/download/${VERSION}/docker-compose-$(uname -s)-$(uname -m) -o $DESTINATION

sudo chmod 755 $DESTINATION

docker-compose -v' > install_docker_compose.sh && chmod +x install_docker_compose.sh && sudo ./install_docker_compose.sh && sudo .rm ./install_docker_compose.sh
```
