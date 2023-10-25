##  一、下载并解压

```bash

# 下载
wget https://github.com/shadowsocks/shadowsocks-rust/releases/download/v1.16.1/shadowsocks-v1.16.1.x86_64-unknown-linux-gnu.tar.xz


# 解压
tar -xf  shadowsocks-v1.16.1.x86_64-unknown-linux-gnu.tar.xz -C /usr/local/bin/
```

## 二、配置文件
    mkdir/etc/shadowsocks.service && curl -Lo /etc/shadowsocks/config.json https://raw.githubusercontent.com/MHY2233/shadowsocks-install/main/config.json

```bash

# 创建目录
mkdir /etc/shadowsocks

# 创建配置文件
vi /etc/shadowsocks/config.json

# 写入以下内容
{
    "server": "0.0.0.0",
    "server_port": 8388,
    "local_address": "127.0.0.1",
    "local_port": 1080,
    "mode":"tcp_and_udp",
    "password": "TheBeautifulPassword",
    "timeout": 300,
    "method": "chacha20-ietf-poly1305"
}
```

## 三、使用 systemd 守护进程

```bash
# 创建service文件
vi /etc/systemd/system/shadowsocks.service

写入以下内容

[Unit]
Description=Shadowsocks Server
After=network.target

[Service]
ExecStart=/usr/local/bin/ssserver -c /etc/shadowsocks/config.json

Restart=on-abort

[Install]
WantedBy=multi-user.target
```

## 四、配置ss开机自启动

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
