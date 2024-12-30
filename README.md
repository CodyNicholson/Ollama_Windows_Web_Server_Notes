# Running Ollama & Ollama WebUI On Windows

## Setup WSL On Windows

```
wsl --install

wsl -d Ubuntu

sudo apt update

sudo apt upgrade -y

curl -fsSL https://ollama.com/install.sh | sh
```

## Install Ollama & Pull Models

```
https://ollama.com/download

ollama pull llama2

ollama pull codegemma

ollama start

ollama run llama2
```

## If Ollama is alrady running but not working:

```
lsof -i :11434

sudo kill -9 <PID>
```

## Watch GPU Performance

```
watch -n 0.5 nvidia-smi
```

## Setup Docker

```
sudo apt-get update

sudo apt-get install ca-certificates curl

sudo install -m 0755 -d /etc/apt/keyrings

sudo curl -fsSL http://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc

sudo chmod a+r /etc/apt/keyrings/docker.asc

echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] http://download.docker.com/linux/ubuntu \
$(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

## Run Open WebUI

```
sudo docker run -d --network=host -v open-webui:/app/backend/data -e OLLAMA_BASE_URL=http://127.0.0.1:11434 --name open-webui --restart always ghcr.io/open-webui/open-webui:main
```

## List All Enabled Services In WSL

```
systemctl list-unit-files --type=service
```
