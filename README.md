# Install packer
```sh
cat <<EOF > install_packer.yaml
- name: Installer
  hosts: all
  tasks:
  - become: "yes"
    name: Install packer
    unarchive:
      creates: /usr/local/bin/packer
      dest: /usr/local/bin
      remote_src: "yes"
      src: |-
        https://releases.hashicorp.com/packer/{{ version }}/packer_{{ version }}_linux_amd64.zip
EOF
ansible-playbook -ilocalhost, -clocal -eversion=1.8.0 install_packer.yaml -K
```
