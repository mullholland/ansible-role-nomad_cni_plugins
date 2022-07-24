# [nomad_cni_plugins](#nomad_cni_plugins)

|GitHub|GitLab|
|------|------|
|[![github](https://github.com/mullholland/ansible-role-nomad_cni_plugins/workflows/Ansible%20Molecule/badge.svg)](https://github.com/mullholland/ansible-role-nomad_cni_plugins/actions)|[![gitlab](https://gitlab.com/mullholland/ansible-role-nomad_cni_plugins/badges/main/pipeline.svg)](https://gitlab.com/mullholland/ansible-role-nomad_cni_plugins)|

description

## [Role Variables](#role-variables)

These variables are set in `defaults/main.yml`:
```yaml
---
# https://www.nomadproject.io/docs/integrations/consul-connect#cni-plugins
# Nomad uses CNI plugins to configure the network namespace used to secure
# the Consul service mesh sidecar proxy. All Nomad client nodes using network
# namespaces must have CNI plugins installed.

nomad_cni_plugins_version: "1.1.1"

# yamllint disable-line rule:line-length
nomad_cni_plugins_download_url: "https://github.com/containernetworking/plugins/releases/download/v{{ nomad_cni_plugins_version }}/cni-plugins-linux-{{ nomad_cni_plugins_arch }}-v{{ nomad_cni_plugins_version }}.tgz"

nomad_cni_plugins_install_path: "/opt/cni/bin"

nomad_cni_plugins_sysctl_settings:
  - name: "net.bridge.bridge-nf-call-arptables"
    value: "1"
  - name: "net.bridge.bridge-nf-call-ip6tables"
    value: "1"
  - name: "net.bridge.bridge-nf-call-iptables"
    value: "1"
```


## [Example Playbook](#example-playbook)

This example is taken from `molecule/default/converge.yml` and is tested on each push, pull request and release.
```yaml
---
- name: Converge
  hosts: all
  become: true
  gather_facts: true
  # vars:
  #   example_var: "value"
  roles:
    - role: "mullholland.nomad_cni_plugins"
```





## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/mullholland):

-   [debian10](https://hub.docker.com/r/mullholland/docker-molecule-debian10)
-   [debian11](https://hub.docker.com/r/mullholland/docker-molecule-debian11)
-   [ubuntu1804](https://hub.docker.com/r/mullholland/docker-molecule-ubuntu1804)
-   [ubuntu2004](https://hub.docker.com/r/mullholland/docker-molecule-ubuntu2004)
-   [centos7](https://hub.docker.com/r/mullholland/docker-molecule-centos7)
-   [centos-stream8](https://hub.docker.com/r/mullholland/docker-molecule-centos-stream8)
-   [fedora35](https://hub.docker.com/r/mullholland/docker-molecule-fedora35)
-   [fedora36](https://hub.docker.com/r/mullholland/docker-molecule-fedora36)
-   [rockylinux8](https://hub.docker.com/r/mullholland/docker-molecule-rockylinux8)
-   [almalinux8](https://hub.docker.com/r/mullholland/docker-molecule-almalinux8)

The minimum version of Ansible required is 2.10, tests have been done to:

-   The previous versions.
-   The current version.





If you find issues, please register them in [GitHub](https://github.com/mullholland/ansible-role-nomad_cni_plugins/issues)

## [License](#license)

MIT


## [Author Information](#author-information)

[Mullholland](https://github.com/mullholland)

## [Special Thanks](#special-thanks)

Template inspired by [Robert de Bock](https://github.com/robertdebock)
