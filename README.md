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
```bash
config.vm.network "private_network", ip: "192.168.33.10"  
```
VMを起動  
```bash
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
```bash
$
```
