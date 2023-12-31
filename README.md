<a name="readme-top"></a>
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
<!-- omit in toc -->
# Ansible Homelab

This repository houses Ansible resources for configuring my personal homelab.
It covers the setup of physical hosts, such as configuring UPS systems and ZFS Event
Daemon with Postfix as an SMTP relay for critical issue notifications, as well as
declarations for virtual machines.

<!-- omit in toc -->
## 📚 Table of Contents

- [ℹ️ About The Project](#ℹ️-about-the-project)
- [✈️ Getting Started](#️-getting-started)
- [📖 Usage](#-usage)
- [🛣 Roadmap](#-roadmap)
- [🤝 Contributing](#-contributing)
- [📜 License](#-license)
- [📬 Contact](#-contact)


<p align="right">(<a href="#readme-top">back to top</a>)</p>

## ℹ️ About The Project

This project aims to be completely declarative and able to bootstrap an empty environment
in to use for disaster recovery and initial setup. The roles are written to be re-usable
and independent of the underlying Linux OS family. All roles are used / tested on Debian-based
systems.

Built with [Ansible](https://www.ansible.com/)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## ✈️ Getting Started

The following is necessary to start using this repository:

**Required packages**:

- `ansible`
- `sshpass` (for initial setup)
- `python-passlib`
- `jq`
- `python-jmespath`

**Optional packages**:

- `bitwarden-cli` (for getting secrets)
- `sshpass` (for populating public SSH keys during initial setup)

**Ansible collections**:

- `ansible.builtin`
- `community.general` (for bitwarden lookups)
- `community.proxmox`

**Installation example on Arch (btw)**

The `ansible` package includes all required collections

```bash
sudo pacman --sync ansible sshpass python-passlib jq python-jmespath
```

**Role documentation**:

- [apt_upgrade](roles/apt_upgrade/README.md)
- [chrony_configuration](roles/chrony_configuration/README.md)
- [postfix_configuration](roles/postfix_configuration/README.md)
- [pve_user_configuration](roles/pve_user_configuration/README.md)
- [remote_user_configuration](roles/remote_user_configuration/README.md)
- [unattended_upgrades_configuration](roles/unattended_upgrades_configuration/README.md)
- [ups_configuration](roles/ups_configuration/README.md)
- [zed_configuration](roles/zed_configuration/README.md)

## 📖 Usage

The Playbooks should be called using the `site.yaml` Playbook. It includes tags
for various combination of steps:

```bash
ansible-playbook site.yaml --tags init                 # bootstrap a new environment
ansible-playbook site.yaml --tags init --limit proxmox # bootstrap all proxmox nodes environment
ansible-playbook site.yaml --tags upgrade              # upgrade all systems
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- ROADMAP -->
## 🛣 Roadmap


- [ ] Proxmox
    - [ ] [Ubuntu Cloud image](https://cloud-images.ubuntu.com/) VM template
    - [ ] VM storage backend (probably [Ceph](https://pve.proxmox.com/wiki/Deploy_Hyper-Converged_Ceph_Cluster))
    - [ ] [Proxmox Backup Server](https://www.proxmox.com/de/proxmox-backup-server/uebersicht)
- [ ] [Nextcloud](https://docs.nextcloud.com/server/latest/admin_manual/installation/) ([currently on TrueNAS Scale](https://truecharts.org/charts/stable/nextcloud/))
    - [ ] Performance optimization
    - [ ] Automated apps setup
- [ ] Kubernetes
    - [ ] Setup [RKE2](https://docs.rke2.io/)
    - [ ] Setup [Longhorn](https://longhorn.io/) storage

See the [open issues](https://github.com/justsomescripts/homelab.ansible/issues) for a full list of proposed features (and known issues).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## 🤝 Contributing

Although this is project is specifically targeted to my personal setup and probably
not re-used, contributions are *greatly appreciated*. So if you have any suggestions
for improvements or fixes, feel free to open an [issue](https://github.com/justsomescripts/homelab.ansible/issues) or a [pull request](https://github.com/justsomescripts/homelab.ansible/pulls)

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## 📜 License

Distributed under the *GNU GENERAL PUBLIC LICENSE*. See [`LICENSE`](LICENSE) for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## 📬 Contact

David Gries - [@dgries](https://www.linkedin.com/in/dgries/) - mail@dgries.de


<br><sup>README based on [othneildrew/Best-README-Template](https://github.com/othneildrew/Best-README-Template/tree/master)</sup>

<p align="right">(<a href="#readme-top">back to top</a>)</p>

[contributors-shield]: https://img.shields.io/github/contributors/justsomescripts/homelab.ansible.svg?style=for-the-badge
[contributors-url]: https://github.com/justsomescripts/homelab.ansible/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/justsomescripts/homelab.ansible.svg?style=for-the-badge
[forks-url]: https://github.com/justsomescripts/homelab.ansible/network/members
[stars-shield]: https://img.shields.io/github/stars/justsomescripts/homelab.ansible.svg?style=for-the-badge
[stars-url]: https://github.com/justsomescripts/homelab.ansible/stargazers
[issues-shield]: https://img.shields.io/github/issues/justsomescripts/homelab.ansible.svg?style=for-the-badge
[issues-url]: https://github.com/justsomescripts/homelab.ansible/issues
[license-shield]: https://img.shields.io/github/license/justsomescripts/homelab.ansible.svg?style=for-the-badge
[license-url]: https://github.com/justsomescripts/homelab.ansible/blob/main/LICENSE
