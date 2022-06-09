# Install terraform
https://www.terraform.io/downloads
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

# Install go
https://go.dev/dl/
```sh
cat <<EOF > install_go.yaml
- name: Installer
  hosts: all
  tasks:
  - become: "yes"
    name: Install go
    unarchive:
      creates: /usr/local/go/
      dest: /usr/local/
      remote_src: "yes"
      src: |-
        https://go.dev/dl/go{{ version }}.linux-amd64.tar.gz
EOF
ansible-playbook -ilocalhost, -clocal -eversion=1.18.3 install_go.yaml -K
```
