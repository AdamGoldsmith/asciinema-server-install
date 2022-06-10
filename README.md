# Install self-hosted asciinema-server

Ansible playbook for creating a docker-compose installation of [asciinema-server](https://github.com/asciinema/asciinema-server) for self-hosting your [asciinema.org](https://asciinema.org/) recordings.

Based on this [installation guide](https://github.com/asciinema/asciinema-server/wiki/Installation-guide).

## Requirements

ansible
asciinema
docker
docker-compose

## Preparation

The following preparation steps will create a python virtual environment to satisfy the above requirements:

1. Clone repo and prepare virtual environment
    ```bash
    git clone https://github.com/AdamGoldsmith/asciinema-server-install.git
    cd asciinema-server-install
    mkdir ~/venvs
    python3 -m venv ~/venvs/asciinema-server
    source ~/venvs/asciinema-server/bin/activate
    pip install pip --upgrade
    pip install -r requirements.txt
    ```
1. Update playbook variables in asciinema-server.yml as per [asciinema-server installation guide](https://github.com/asciinema/asciinema-server/wiki/Installation-guide)
    ```yaml
    asciinema_host: localhost
    project_dir: ~/asciinema-server
    asciinema_http_port: 80
    ```
1. Run the playbook
    ```bash
    ansible-playbook asciinema-server.yml
    ```

1. Point browser at `asciinema_host:asciinema_http_port` to test


## Text-based installation walkthrough (rendered by Asciinema [of course!])

<a href="https://asciinema.org/a/a4ePXPU3KXZWtO5HdveIrbteb?autoplay=1"><img src="https://asciinema.org/a/a4ePXPU3KXZWtO5HdveIrbteb.svg" title="Installation video" alt="Installation video" width="640"/></a>

## Known issues

1. TLS not working (never does!)
2. http://localhost:PORT doesn't work - need either host's IP or 0.0.0.0
