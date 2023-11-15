### 1.下载程序压缩包
    wget https://github.com/shadowsocks/shadowsocks-rust/releases/download/v1.17.0/shadowsocks-v1.17.0.x86_64-unknown-linux-gnu.tar.xz


### 2.解压程序压缩包
    tar -xf shadowsocks-v1.17.0.x86_64-unknown-linux-gnu.tar.xz -C /usr/local/bin/

### 3.创建配置文件
    mkdir /etc/shadowsocks

    vim /etc/shadowsocks/config.json


#### 写入下面配置内容
```
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
```
### 4.配置systemctl 文件
    vim /etc/systemd/system/shadowsocks.service


#### 写入下面配置内容
```bash
[Unit]
Description=Shadowsocks Server
After=network.target

[Service]
ExecStart=/usr/local/bin/ssserver -c /etc/shadowsocks/config.json

Restart=on-abort

[Install]
WantedBy=multi-user.target
```
### 5.程序启动设置

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
