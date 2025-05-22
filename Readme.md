# 🐳 Docker Template for PHP, Nginx, and MySQL

🚀 A production-ready Docker template for modern PHP web development with Nginx and MySQL. Perfect for building scalable web applications with ease.

![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
![PHP](https://img.shields.io/badge/php-%23777BB4.svg?style=for-the-badge&logo=php&logoColor=white)
![Nginx](https://img.shields.io/badge/nginx-%23009639.svg?style=for-the-badge&logo=nginx&logoColor=white)
![MySQL](https://img.shields.io/badge/mysql-%2300f.svg?style=for-the-badge&logo=mysql&logoColor=white)

## ✨ Features

- **PHP 8.2** with essential extensions (PDO, GD, Intl, etc.)
- **Nginx** as high-performance web server
- **MySQL** database with optimized configuration
- **Adminer** for intuitive database management
- **Node.js, NPM, and Yarn** pre-installed for frontend tooling
- **Composer** for PHP dependency management
- Customizable user/group IDs for proper file permissions

## 📋 Prerequisites

- Docker Engine v20.10+
- Docker Compose v2.0+
- Git (optional)

## 🏗 Project Structure

```
.
├── .docker/               # Docker service configurations
│   ├── nginx/             # Nginx config files
│   ├── php/               # PHP config and extensions
│   └── db/                # MySQL config
├── db.env                 # Database environment variables
├── docker-compose.yml     # Main Docker Compose file
├── .env.example           # Environment variables template
└── Readme.md              # This documentation
```

## 🚀 Quick Start

### 1. Clone the repository
```bash
git clone https://github.com/ItsTaufikHdyt/fwdocker.git
cd fwdocker
```

### 2. Setup environment
```bash
cp .env.example .env  # Configure as needed
```

### 3. Start services
```bash
docker-compose up -d --build
```

### 4. Access services
| Service   | URL                     | Credentials (if any)     |
|-----------|-------------------------|--------------------------|
| Web       | [http://localhost](http://localhost) | - |
| Adminer   | [http://localhost:8080](http://localhost:8080) | Use MySQL credentials |
| MySQL     | `localhost:3306`        | Defined in `db.env`      |

## ⚙️ Configuration

### PHP
- Modify `.docker/php/php.ini` for PHP settings
- Add extensions in `.docker/php/Dockerfile`

### Nginx
- Update `.docker/nginx/default.conf` for site config
- Modify `.docker/nginx/nginx.conf` for global settings

### MySQL
- Customize credentials in `db.env`
- Tune settings in `.docker/db/my.cnf`

## 📚 Documentation Links

- [Docker Compose](https://docs.docker.com/compose/)
- [PHP](https://www.php.net/docs.php)
- [Nginx](https://nginx.org/en/docs/)
- [MySQL](https://dev.mysql.com/doc/)

## 🤝 Contributing

Contributions welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Submit a pull request

## 📜 License

MIT License - see [LICENSE](LICENSE) file for details.

---

💻 **Happy Coding!** Let's build something amazing! 🚀
