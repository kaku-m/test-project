# test-project

## ローカル開発環境構築例（Windows）

### 事前準備
・VirtualBoxのインストール  
　https://www.virtualbox.org/  
・Vagrantのインストール  
　https://www.vagrantup.com/  
・PuTTYのインストール  
　https://www.putty.org/  

### 手順
PowerShellまたはコマンドプロンプトを起動
```
> mkdir MyVagrant/MyCentOS/

> cd MyVagrant/MyCentOS/

> vagrant init bento/centos-8.1

> vim ./Vagrantfile
```
Vagrantfileの以下のコメントアウトを外す  
```
# config.vm.network "private_network", ip: "192.168.33.10"  
```
VMを起動  
```
> vagrant up
```
PuTTYを起動  
Host Name「192.168.33.10」  
Port「22」  
Connection type:「SSH」  
を入力して「Open」  
PuTTY Security Alert「はい」  
login as:「vagrant」  
password:「vagrant」  
```
$ su
# Password:「vagrant」

# gitのインストール
$ yum install -y git
$ exit

# Homebrewのインストール
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
# Enter押下
$ echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"' >> /home/vagrant/.bash_profile
$ eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"
$ brew -v

# nodeのインストール
$ brew install gcc
$ brew install nodebrew
$ /home/linuxbrew/.linuxbrew/opt/nodebrew/bin/nodebrew setup_dirs
$ export PATH=$HOME/.nodebrew/current/bin:$PATH
$ nodebrew -v
$ nodebrew ls-remote
$ nodebrew install-binary v14.16.1
$ nodebrew ls
$ nodebrew use v14.16.1
$ echo 'export PATH=$HOME/.nodebrew/current/bin:$PATH' >> /home/vagrant/.bash_profile

# 設定反映
$ source ~/.bash_profile

# MySQLのインストール
$ su
# Password:「vagrant」
$ dnf localinstall https://dev.mysql.com/get/mysql80-community-release-el8-1.noarch.rpm
# Is dhis ok:「y」
$ dnf module disable mysql
# Is dhis ok:「y」
$ dnf info mysql-community-server
$ dnf install mysql-community-server
# Is dhis ok:「y」
# Is dhis ok:「y」
$ mysqld --version

# MySQLを起動
$ systemctl start mysqld
$ systemctl status mysqld

# MySQLの設定
# パスワードの確認
$ grep 'temporary password' /var/log/mysqld.log
$ mysql_secure_installation
# Enter password for user root:「確認したパスワードを入力」
# New password:「Password@9」
# Re-enter new password:「Password@9」
# Change the password for root ?:「y」
# New password:「Password@9」
# Re-enter new password:「Password@9」
# Do you wish to continue with the password provided?:「y」
# Remove anonymous users?:「y」
# Disallow root login remotely?:「n」
# Remove test database and access to it?:「n」
# Reload privilege tables now?:「n」

# テーブルの作成
$ mysql -uroot -pPassword@9
> CREATE DATABASE test_db;
> SHOW DATABASES;
> USE test_db;
> CREATE TABLE pages (
> id INT NOT NULL PRIMARY KEY,
> path TEXT NOT NULL,
> title VARCHAR(255) NOT NULL UNIQUE,
> content TEXT,
> created_at DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
> updated_at DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
> );
```

