# Ansible Web Server Setup Playbook

![GitHub stars](https://img.shields.io/github/stars/YOUR_USERNAME/ansible-web-setup?style=social)
![License](https://img.shields.io/badge/license-MIT-green)
![Ansible](https://img.shields.io/badge/Ansible-2.9+-blue)

A complete Ansible playbook to automatically setup and configure a web development environment on Ubuntu with:
- **Node.js 20.x LTS**
- **npm (latest)**
- **MySQL 8.0**
- **Apache2 Web Server**

## 🚀 Quick Start

### Prerequisites
- Ansible 2.9+ installed on controller machine
- Ubuntu 18.04+ on target server
- SSH access with sudo privileges

### Installation

```bash
# 1. Clone repository
git clone https://github.com/YOUR_USERNAME/ansible-web-setup.git
cd ansible-web-setup

# 2. Configure inventory
cp inventory.ini.example inventory.ini
nano inventory.ini
# Update with your server IP and credentials

# 3. Run playbook
ansible-playbook -i inventory.ini site.yml -v
```

## 📋 What Gets Installed

✅ **System Updates** - Latest security patches  
✅ **Node.js 20.x LTS** - JavaScript runtime  
✅ **npm** - Node package manager  
✅ **MySQL 8.0** - Database server  
✅ **Apache2** - Web server  
✅ **Build Tools** - Development essentials  

## 🔧 Configuration

Edit `site.yml` to customize:

```yaml
vars:
  mysql_root_password: "Root@123"
  mysql_db_user: "webapp_user"
  mysql_db_password: "WebApp@123"
  mysql_database: "webapp_db"
```

## 📖 Documentation

- [Installation Guide](docs/INSTALLATION.md)
- [Troubleshooting](docs/TROUBLESHOOTING.md)
- [Usage Examples](docs/USAGE.md)

## 🛠️ Verification

After successful execution, verify services:

```bash
ssh ubuntu@your_server_ip

# Check services
sudo systemctl status mysql
sudo systemctl status apache2

# Check versions
node --version
npm --version
mysql --version
```

## 📊 Directory Structure

```
├── site.yml              # Main playbook
├── inventory.ini         # Inventory file
├── roles/                # Ansible roles
│   ├── nodejs/          # Node.js setup
│   ├── mysql/           # MySQL setup
│   ├── apache2/         # Apache2 setup
│   └── app_setup/       # Application setup
├── docs/                # Documentation
└── scripts/             # Helper scripts
```

## 🐛 Troubleshooting

### MySQL fails to start
```bash
sudo mkdir -p /var/run/mysqld
sudo chown mysql:mysql /var/run/mysqld
sudo systemctl restart mysql
```

### Check service status
```bash
ansible -i inventory.ini web_servers -m systemd -a "name=mysql state=started"
```

See [TROUBLESHOOTING.md](docs/TROUBLESHOOTING.md) for more issues.

## 🤝 Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create feature branch (`git checkout -b feature/improvement`)
3. Commit changes (`git commit -am 'Add improvement'`)
4. Push to branch (`git push origin feature/improvement`)
5. Create Pull Request

## 📝 License

This project is licensed under the MIT License - see [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Ahmed CLG**
- GitHub: [@Ahmed-CLG](https://github.com/Ahmed-CLG)
- LinkedIn: [Ahmed CLG](https://linkedin.com/in/Ahmed-CLG)

## 🙏 Acknowledgments

- [Ansible Documentation](https://docs.ansible.com/)
- [Ubuntu Community](https://help.ubuntu.com/)
- [MySQL Documentation](https://dev.mysql.com/doc/)

## 📞 Support

For issues and questions:
1. Check [TROUBLESHOOTING.md](docs/TROUBLESHOOTING.md)
2. Open an [Issue](https://github.com/YOUR_USERNAME/ansible-web-setup/issues)
3. Contact: ahmed@example.com

---

⭐ If you find this helpful, please give it a star!
