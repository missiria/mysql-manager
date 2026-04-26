# MySQL Manager

A comprehensive, interactive command-line tool for MySQL database administration — written in pure Bash. No dependencies beyond MySQL itself.

Built by [EKSNEKS](https://www.eksneks.com) · Version 3

---

## Features

**Database Operations**
- Create, drop, export, import, backup, and clone databases
- Backup a single database or all databases at once

**Table & Data Tools**
- Global search & replace across all text columns
- Clean up tables by prefix or WordPress plugin tables
- Check, repair, and analyze table integrity

**URL & Domain Scanner**
- Regex-based scan to find and extract all URLs/domains stored in the database

**Database Insights**
- Total database size, per-table sizes and row counts
- Charset, collation, and engine information

**User Management**
- Create/drop users, grant/revoke privileges, change passwords

**WordPress Tools**
- Domain migration (siteurl, home, post content, GUIDs)
- Remove UTM/tracking query parameters from links
- Clear transients, delete revisions, clean trash & spam
- Remove orphaned postmeta/commentmeta/term_relationships
- Optimize all WordPress tables
- All-in-one maintenance bundle

**File Tools**
- Mass file renaming utility for media directory cleanup

---

## Requirements

- Bash 4+ (macOS ships Bash 3; see macOS install note below)
- `mysql` and `mysqldump` CLI tools
- A running MySQL or MariaDB server
- Standard Unix utilities: `grep`, `awk`, `find`, `date`

---

## Installation

### Linux (Ubuntu / Debian / CentOS / RHEL)

```bash
# 1. Install MySQL client tools if not already installed
# Ubuntu/Debian
sudo apt-get update && sudo apt-get install -y mysql-client

# CentOS/RHEL
sudo yum install -y mysql

# 2. Clone the repository
git clone https://github.com/missiria/mysql-manager.git
cd mysql-manager

# 3. Make the script executable
chmod +x db-manager.sh

# 4. Run it
./db-manager.sh
```

**Optional — install system-wide:**

```bash
sudo cp db-manager.sh /usr/local/bin/mysql-manager
sudo chmod +x /usr/local/bin/mysql-manager

# Then run from anywhere:
mysql-manager
```

---

### macOS

macOS ships with Bash 3 (which is too old) and uses Zsh by default. You need to install Bash 4+ and the MySQL client.

```bash
# 1. Install Homebrew if not already installed
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# 2. Install Bash 4+ and MySQL client
brew install bash mysql-client

# 3. Add mysql-client to your PATH (add this to ~/.zshrc or ~/.bash_profile)
echo 'export PATH="/opt/homebrew/opt/mysql-client/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc

# 4. Clone the repository
git clone https://github.com/missiria/mysql-manager.git
cd mysql-manager

# 5. Make the script executable
chmod +x db-manager.sh

# 6. Run it
./db-manager.sh
```

> **Apple Silicon (M1/M2/M3):** Homebrew installs to `/opt/homebrew`. Intel Macs use `/usr/local`. Adjust the PATH export above accordingly.

---

## Configuration

The script reads optional environment variables for defaults. Set them before running or export them in your shell profile:

```bash
export DB_USER="root"
export DB_PASS="your_password"
export DEFAULT_BACKUP_DIR="/var/backups/mysql"
export DEFAULT_EXPORT_PATH="/tmp/dump.sql"
export DEFAULT_IMPORT_PATH="/tmp/dump.sql"
export DEFAULT_GRANT_USER="myuser"
export DEFAULT_GRANT_HOST="localhost"

# Optional: override binary paths
export MYSQL_BIN="/usr/local/bin/mysql"
export MYSQLDUMP_BIN="/usr/local/bin/mysqldump"
```

If not set, the tool will prompt you for credentials interactively.

---

## Usage

```bash
./db-manager.sh
```

The tool launches an interactive menu. Navigate by entering the number next to each option and pressing `Enter`.

**Main menu sections:**

```
[1] Database Operations
[2] Table & Data Operations
[3] Search & Scan
[4] Database Info & Insights
[5] User Management
[6] File Tools
[7] WordPress Tools
[0] Exit
```

---

## Safety

- Destructive operations (DROP, DELETE) require explicit confirmation before execution.
- Backups can be triggered automatically before modifications.
- SQL inputs are escaped to prevent injection.
- Bash strict mode (`set -u`, `set -o pipefail`) is enabled throughout.

---

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

1. Fork the repository
2. Create your feature branch: `git checkout -b feature/my-feature`
3. Commit your changes: `git commit -m 'feat: add my feature'`
4. Push to the branch: `git push origin feature/my-feature`
5. Open a Pull Request

---

## License

MIT License — see [LICENSE](LICENSE) for details.

---

## Links

- Website: [www.eksneks.com](https://www.eksneks.com)
- GitHub: [github.com/missiria/mysql-manager](https://github.com/missiria/mysql-manager)
- Issues: [github.com/missiria/mysql-manager/issues](https://github.com/missiria/mysql-manager/issues)
