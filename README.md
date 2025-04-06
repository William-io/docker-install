1. Set up Docker's apt repository.
```bash
sudo sysctl -w kernel.apparmor_restrict_unprivileged_userns=0
```

### Add Docker's official GPG key:

```bash
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

### Add the repository to Apt sources:
```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

2. Install the Docker packages.
```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

3. Create the docker group.
```bash
sudo groupadd docker

sudo usermod -aG docker $USER

newgrp docker

docker --version
```
4. Restart
5. Download Dockermanager/install: [download](https://desktop.docker.com/linux/main/amd64/docker-desktop-amd64.deb?utm_source=docker&utm_medium=webreferral&utm_campaign=docs-driven-download-linux-amd64&_gl=1*jkex6h*_ga*Njc0OTU3MDgwLjE3NDM3MTY0MTA.*_ga_XJWPQMJYHQ*MTc0MzcyMzU1MS4yLjEuMTc0MzcyNDAzNS40Mi4wLjA.)

6. Download SQLServer
```bash
docker pull mcr.microsoft.com/mssql/server
```
7. RUN
```bash
docker run --name sqlserver -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=1q2w3e4r@#$" -p 1433:1433 -d mcr.microsoft.com/mssql/server
```

Connection String

Se você utilizou as mesmas configurações deste artigo, sua Connection String será igual abaixo. Caso necessário, modifique as informações que alterou na execução dos containers.
```bash
Server=localhost,1433;Database=balta;User ID=sa;Password=1q2w3e4r@#$;Trusted_Connection=True;
```

