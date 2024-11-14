# Docker Role

This Ansible role installs Docker on a target machine and configures it for use with containers. It is designed to be used in environments where Docker needs to be installed and configured via Ansible.

## Requirements

- Ansible 2.x or higher
- Target machine running Ubuntu (or Debian-based distributions)
- Root privileges for installing system packages (via `become: true`)


## Role Variables

This section describes the variables that can be set for the role.

- `docker_gpg_key_url`: URL of the Docker GPG key. Default: `https://download.docker.com/linux/ubuntu/gpg`
- `docker_repository_url`: Docker repository URL. Default: `https://download.docker.com/linux/ubuntu`
- `docker_repo_distribution`: The Ubuntu distribution to use for the Docker repository (e.g., `focal` for Ubuntu 20.04). Default: `focal`
- `docker_package_state`: The state of the Docker package (can be `stable` or another state). Default: `stable`
- `docker_package`: The name of the Docker package. Default: `docker-ce`
- `docker_group_user`: The user who will be added to the Docker group. Default: the user running the Ansible playbook (`{{ ansible_user }}`)

### Default Variables (in `defaults/main.yml`)
```yaml
docker_gpg_key_url: "https://download.docker.com/linux/ubuntu/gpg"
docker_repository_url: "https://download.docker.com/linux/ubuntu"
docker_repo_distribution: "focal"
docker_package_state: "stable"
docker_package: "docker-ce"
docker_group_user: "{{ ansible_user }}"


### Dependencies
This role does not have any external dependencies or prerequisites that are not covered by Ansible itself.

### Example Playbook
----------------

---
- name: Install Docker on application nodes
  hosts: app
  become: true
  roles:
    - Docker

