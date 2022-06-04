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
ansible-playbook -ilocalhost, -clocal -eversion=1.8.1 install_packer.yaml -K
```

# Install terraform
```sh
cat <<EOF > install_terraform.yaml
- name: Installer
  hosts: all
  tasks:
  - become: "yes"
    name: Install terraform
    unarchive:
      creates: /usr/local/bin/terraform
      dest: /usr/local/bin
      remote_src: "yes"
      src: |-
        https://releases.hashicorp.com/terraform/{{ version }}/terraform_{{ version }}_linux_amd64.zip
EOF
ansible-playbook -ilocalhost, -clocal -eversion=1.2.2 install_terraform.yaml -K
```
