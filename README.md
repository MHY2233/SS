### 1.下载程序压缩包
    wget https://github.com/shadowsocks/shadowsocks-rust/releases/download/v1.17.0/shadowsocks-v1.17.0.x86_64-unknown-linux-gnu.tar.xz


### 2.解压程序压缩包
    tar -xf shadowsocks-v1.17.0.x86_64-unknown-linux-gnu.tar.xz -C /usr/local/bin/

### 2.创建配置文件
    mkdir /etc/shadowsocks

    vim /etc/shadowsocks/config.json


#### 写入下面配置内容
    {
        "server": "0.0.0.0",
        "server_port": 8338,
        "local_address": "127.0.0.1",
        "local_port": 1080,
        "mode": "tcp_and_udp",
        "password": "TheBeautifulPassword",
        "timeout": 300,
        "method": "chacha20-ietf-poly1305"
    }
### 3.下载systemctl文件
    curl -Lo /etc/systemd/system/shadowsocks.service https://raw.githubusercontent.com/MHY2233/shadowsocks-install/main/shadowsocks.service && systemctl daemon-reload

### 4.配置ss开机自启动

```bash

# 重新加载service文件
systemctl daemon-reload 

# 开启shadowsocks 
systemctl start shadowsocks 

# 重启shadowsocks
systemctl restart shadowsocks

# 设置shadowsocks开机自启
systemctl enable shadowsocks 

# 查看shadowsocks运行状态
systemctl status shadowsocks 

```
