# AWX / Ansible – Lab Semana 1 🚀

[![Ansible](https://img.shields.io/badge/Ansible-EE0000?style=for-the-badge&logo=ansible&logoColor=white)](https://www.ansible.com/)
[![AWX](https://img.shields.io/badge/AWX-4A90E2?style=for-the-badge&logo=ansible&logoColor=white)](https://github.com/ansible/awx)

---

## 📖 Descrição
Laboratório inicial com **Ansible** para preparar o uso do **AWX**.  
Estrutura com 1 VM **control** (Ansible instalado) e 2 VMs **nodes** gerenciadas.

---

## 🧱 Arquitetura

```bash
control (192.168.56.10) ── ansible
├─ node1 (192.168.56.11)
└─ node2 (192.168.56.12)
```

---

## ⚙️ Passos

### 1. Subir as VMs
```bash
vagrant up
vagrant ssh control
```

### 2. Instalar Ansible no control
```bash
sudo dnf -y install epel-release
sudo dnf -y install ansible
ansible --version
```
3. Testar conectividade
```bash
ansible node_servers -m ping \
  -u vagrant --private-key ~/.ssh/vagrant_insecure_key
  ```
## 📂 Estrutura do projeto
```yml
ansible-lab/
├─ Vagrantfile
├─ ansible.cfg
├─ hosts.ini
├─ group_vars/
│  └─ node_servers.yml
├─ playbooks/
│  ├─ 01-install-packages.yml
│  ├─ 02-create-user.yml
│  └─ 03-copy-file-and-service.yml
└─ files/
   └─ motd
```
## ▶️ Executando playbooks

```bash
ansible-playbook playbooks/01-install-packages.yml -u vagrant --private-key ~/.ssh/vagrant_insecure_key
ansible-playbook playbooks/02-create-user.yml     -u vagrant --private-key ~/.ssh/vagrant_insecure_key
ansible-playbook playbooks/03-copy-file-and-service.yml -u vagrant --private-key ~/.ssh/vagrant_insecure_key
```

