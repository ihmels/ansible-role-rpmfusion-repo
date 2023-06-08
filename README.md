Ansible Role: RPM Fusion repositories
=====================================

Installs and configures [RPM Fusion][1] free and nonfree repositories.

Requirements
------------

On RHEL or other compatible distributions like CentOS the EPEL repository is required, which can be installed with the `geerlingguy.repo-epel` role.

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`).

The URLs from which the RPM Fusion free and nonfree repositories will be downloaded and installed:

    rpmfusion_repo_free_repo_url: "https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-{{ rpmfusion_repo_distribution_major_version }}.noarch.rpm"
    rpmfusion_repo_nonfree_repo_url: "https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-{{ rpmfusion_repo_distribution_major_version }}.noarch.rpm"

GPG key location for RPM Fusion free and nonfree repositories:

    rpmfusion_repo_free_gpg_url: "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-free-{{ rpmfusion_repo_distribution }}-{{ rpmfusion_repo_gpg_key_version }}"
    rpmfusion_repo_nonfree_gpg_url: "https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-nonfree-{{ rpmfusion_repo_distribution }}-{{ rpmfusion_repo_gpg_key_version }}"

GPG key fingerprints for corresponding keys:

    rpmfusion_repo_free_fingerprint: "{{ rpmfusion_repo_fingerprints[rpmfusion_repo_distribution][rpmfusion_repo_gpg_key_version]['free'] }}"
    rpmfusion_repo_nonfree_fingerprint: "{{ rpmfusion_repo_fingerprints[rpmfusion_repo_distribution][rpmfusion_repo_gpg_key_version]['nonfree'] }}"

Enable or disable repositories:

    rpmfusion_repo_enable_free: true
    rpmfusion_repo_enable_nonfree: true

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: ihmels.rpmfusion_repo }

License
-------

MIT

[1]: https://rpmfusion.org
