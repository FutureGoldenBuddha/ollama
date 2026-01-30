add the Repository Correctly. Use the command from the official NVIDIA guide, which ensures the GPG key is correctly referenced. Paste this single block:

```bash
curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey | gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg && curl -s -L https://nvidia.github.io/libnvidia-container/stable/deb/nvidia-container-toolkit.list | sed 's#deb https://#deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit-keyring.gpg] https://#g' | tee /etc/apt/sources.list.d/nvidia-container-toolkit.list
```

```
apt-get update && apt-get install -y nvidia-container-toolkit
```

```
nvidia-ctk runtime configure --runtime=docker
systemctl restart docker
```

confirma

```
docker run --rm --runtime=nvidia --gpus all nvidia/cuda:12.4.0-base-ubuntu22.04 nvidia-smi
```
