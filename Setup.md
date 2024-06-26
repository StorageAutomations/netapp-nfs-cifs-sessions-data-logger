# Steps to configure NetApp connected clients datacollector

1. Installing docker on a Linux host (For Yum based installer)
   > Skip this step if Docker is already installed and move to step 2.

    ```bash
    sudo yum update -y
    sudo yum install docker -y
    sudo systemctl enable docker
    sudo systemctl start docker
    sudo usermod -aG docker $USER
    ```

2. Installing `docker-compose`
    ```bash
    sudo curl -L "https://github.com/docker/compose/releases/download/v2.24.5/docker-compose-linux-x86_64" -o /usr/local/bin/docker-compose
    sudo chmod +x /usr/local/bin/docker-compose
    ```

3. Download the zip file using the presigned URL provided.
   ```bash
   git clone https://github.com/StorageAutomations/netapp-nfs-cifs-sessions-data-logger.git
   cd netapp-nfs-cifs-sessions-data-logger/
   ```
   
4. Update `config_input.json` file in the **input** folder with list of Netapp Storage arrays, *Username*, *Password* and *IP address* to collect data.

5. Start data collection process using `docker-compose` to launch the container
    ```bash
    docker-compose up -d
    ```