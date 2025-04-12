# ComfyUI-Docker-Windows

A streamlined solution for running ComfyUI with Docker on Windows systems.

## Overview

This repository provides a Docker-based implementation of ComfyUI specifically configured for Windows environments. ComfyUI is a powerful node-based UI for Stable Diffusion, and this project simplifies its deployment using Docker containers, eliminating complex setup procedures and dependency conflicts.

## Features

- **Easy Installation**: Get ComfyUI running with minimal setup steps
- **Docker-based**: Isolated environment that doesn't interfere with your system
- **Windows-optimized**: Configured specifically for Windows systems
- **GPU Acceleration**: Properly configured for NVIDIA GPU support
- **Volume Mapping**: Easy access to models, outputs, and workflows
- **Custom Nodes Support**: Ability to add and use custom nodes

## Prerequisites

- Windows 10/11
- [Docker Desktop for Windows](https://www.docker.com/products/docker-desktop/)
- NVIDIA GPU with the latest drivers
- [NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html) (for GPU support)

## Installation

1. Clone this repository:
   ```markdown
   git clone https://github.com/abhinavasr/ComfyUI-Docker-Windows.git
   cd ComfyUI-Docker-Windows
   ```

2. Build the Docker image:
   ```markdown
   docker-compose build
   ```

3. Start the container:
   ```markdown
   docker-compose up
   ```

4. Access ComfyUI in your browser:
   ```markdown
   http://localhost:8188
   ```

## Directory Structure

```markdown
ComfyUI-Docker-Windows/
├── docker-compose.yml      # Container configuration
├── Dockerfile              # Build instructions
├── models/                 # Place your models here
│   ├── checkpoints/        # Stable Diffusion models
│   ├── loras/              # LoRA files
│   └── vae/                # VAE files
├── custom_nodes/           # For adding custom extension nodes
├── input/                  # Input images for img2img, etc.
└── output/                 # Generated images appear here
```

## Adding Models

1. Place your models in the appropriate directories:
   - Stable Diffusion checkpoints: `models/checkpoints/`
   - LoRA files: `models/loras/`
   - VAE files: `models/vae/`
   - Embeddings: `models/embeddings/`
   - ControlNet models: `models/controlnet/`

2. Restart the container if it's already running:
   ```markdown
   docker-compose restart
   ```

## Adding Custom Nodes

1. Add custom nodes to the `custom_nodes` directory (either manually or using git clone)
2. Restart the container:
   ```markdown
   docker-compose restart
   ```

## Configuration Options

You can modify the `docker-compose.yml` file to change various settings:

- Port mapping: Change the default port (8188) if needed
- Volume paths: Modify where models and outputs are stored
- GPU settings: Adjust resources allocated to ComfyUI

## Troubleshooting

### Common Issues

1. **Docker container fails to start**
   - Ensure Docker Desktop is running
   - Check that your NVIDIA drivers are up to date
   - Verify NVIDIA Container Toolkit is properly installed

2. **Cannot access ComfyUI in browser**
   - Check if the container is running: `docker ps`
   - Verify port mapping in docker-compose.yml
   - Check Windows firewall settings

3. **GPU not detected**
   - Run `nvidia-smi` to verify GPU driver functionality
   - Ensure Docker Desktop has WSL integration enabled
   - Check NVIDIA Container Toolkit configuration

### Logs

To view container logs:
```markdown
docker-compose logs
```

## Performance Tips

- Allocate sufficient memory to Docker in Docker Desktop settings
- Use SSD for volume locations to improve model loading times
- Close other GPU-intensive applications while running ComfyUI

## Updating

To update to the latest version:

```markdown
git pull
docker-compose down
docker-compose build
docker-compose up
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgements

- [ComfyUI](https://github.com/comfyanonymous/ComfyUI) for the amazing Stable Diffusion UI
- The Docker community for container technologies
- All contributors to this project
