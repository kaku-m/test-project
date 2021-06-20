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
```bash
# 適当なフォルダを作成
mkdir MyVagrant/MyCentOS/
cd MyVagrant/MyCentOS/
vagrant init bento/centos-8.1
vim ./Vagrantfile
```
Vagrantfileの以下のコメントアウトを外す  
config.vm.network "private_network", ip: "192.168.33.10"  




```bash
# install dependencies
$ npm install

# serve with hot reload at localhost:3000
$ npm run dev

# build for production and launch server
$ npm run build
$ npm run start

# generate static project
$ npm run generate
```

For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).
