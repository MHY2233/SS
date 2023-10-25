### 1.下载shadowsocks 程序

```bash

# 下载
wget https://github.com/shadowsocks/shadowsocks-rust/releases/download/v1.16.1/shadowsocks-v1.16.1.x86_64-unknown-linux-gnu.tar.xz


# 解压
tar -xf  shadowsocks-v1.16.1.x86_64-unknown-linux-gnu.tar.xz -C /usr/local/bin/
```

### 2.下载shadowsocks配置文件
    mkdir/etc/shadowsocks.service && curl -Lo /etc/shadowsocks/config.json https://raw.githubusercontent.com/MHY2233/shadowsocks-install/main/config.json

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
