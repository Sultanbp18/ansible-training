# Ansible Automation Installing web server and docker

Project ini merupakan demonstrasi penggunaan Ansible untuk otomatisasi provisioning server berbasis Debian menggunakan Vagrant dan VirtualBox. Tujuan project ini adalah menyiapkan dua VM dengan role berbeda:
- **web**: berisi Nginx dan konfigurasi firewall
- **docker**: berisi Docker Engine dan user tambahan

## Struktur Direktori
```
project/
├── README.md                  # Dokumentasi project
├── inventory/
│   └── hosts.ini              # Daftar host dan grup
├── playbooks/                 # Kumpulan playbook Ansible
│   ├── 01-nginx-install.yml
│   ├── 02-docker-setup.yml
│   ├── 03-user-create.yml
│   ├── 04-firewall-config.yml
│   └── 05-status-check.yml
├── files/
│   └── username.pub           # Public key untuk user baru
└── vagrant/
    └── Vagrantfile            # Konfigurasi VM lokal
```

## Cara Menjalankan Project

### 1. Jalankan VM dengan Vagrant
```bash
cd vagrant
vagrant up
```

### 2. Pastikan Ansible terinstall
```bash
ansible --version
```

### 3. Jalankan semua playbook secara berurutan
```bash
ansible-playbook -i ../inventory/hosts.ini ../playbooks/01-nginx-install.yml
ansible-playbook -i ../inventory/hosts.ini ../playbooks/02-docker-setup.yml
ansible-playbook -i ../inventory/hosts.ini ../playbooks/03-user-create.yml
ansible-playbook -i ../inventory/hosts.ini ../playbooks/04-firewall-config.yml
ansible-playbook -i ../inventory/hosts.ini ../playbooks/05-status-check.yml
```

## Fitur
- Setup otomatis dua VM dengan RAM dan CPU terbatas
- Instalasi dan konfigurasi Nginx
- Instalasi Docker dan dependensi
- Pembuatan user baru dan SSH key
- Konfigurasi firewall UFW
- Pemeriksaan status layanan secara otomatis

---# ansible-training
