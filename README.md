# Ubuntu 22.04 (Jammy Jellyfish) Ansible Devel Image

[![Build and Push Container](https://github.com/buluma/docker-ubuntu2204-ansible/actions/workflows/build-image.yml/badge.svg?branch=main)](https://github.com/buluma/docker-ubuntu2204-ansible/actions/workflows/build-image.yml) ![Docker Pulls](https://img.shields.io/docker/pulls/buluma/docker-ubuntu2204-ansible) [![CodeFactor](https://www.codefactor.io/repository/github/buluma/docker-ubuntu2204-ansible/badge)](https://www.codefactor.io/repository/github/buluma/docker-ubuntu2204-ansible) [![Codacy Badge](https://api.codacy.com/project/badge/Grade/9e63fd25e79042ae87cc103e7aa28842)](https://app.codacy.com/gh/buluma/docker-ubuntu2204-ansible?utm_source=github.com&utm_medium=referral&utm_content=buluma/docker-ubuntu2204-ansible&utm_campaign=Badge_Grade_Settings)

Ubuntu 22.04 Devel (Jammy Jellyfish) Docker container for Ansible playbook and role testing.

## Tags

  - `latest`: Latest stable version of Ansible.

The latest tag is a lightweight image for basic validation of Ansible playbooks.

## How to Build

This image is built on Docker Hub automatically any time the upstream OS container is rebuilt, and any time a commit is made or merged to the `main` branch. But if you need to build the image on your own locally, do the following:

  1. [Install Docker](https://docs.docker.com/install/).
  2. `cd` into this directory.
  3. Run `docker build -t ubuntu2204-ansible .`

## How to Use

  1. [Install Docker](https://docs.docker.com/engine/installation/).
  2. Pull this image from Docker Hub: `docker pull buluma/docker-ubuntu2204-ansible:latest` (or use the image you built earlier, e.g. `ubuntu2204-ansible:latest`).
  3. Run a container from the image: `docker run --detach --privileged --volume=/sys/fs/cgroup:/sys/fs/cgroup:ro buluma/docker-ubuntu2204-ansible:latest` (to test my Ansible roles, I add in a volume mounted from the current working directory with ``--volume=`pwd`:/etc/ansible/roles/role_under_test:ro``).
  4. Use Ansible inside the container:
    a. `docker exec --tty [container_id] env TERM=xterm ansible --version`
    b. `docker exec --tty [container_id] env TERM=xterm ansible-playbook /path/to/ansible/playbook.yml --syntax-check`

## Notes

I use Docker to test my Ansible roles and playbooks on multiple OSes using CI tools like Jenkins and Travis. This container allows me to test roles and playbooks using Ansible running locally inside the container.

> **Important Note**: I use this image for testing in an isolated environment—not for production—and the settings and configuration used may not be suitable for a secure and performant production environment. Use on production servers/in the wild at your own risk!

## Author

Created in Dec 2021 by [Michael Buluma](https://www.buluma.co.ke/).
