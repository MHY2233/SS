# ShadowSocks-Rust-install

##  一、下载并解压

```bash
wget https://github.com/shadowsocks/shadowsocks-rust/releases/download/v1.16.1/shadowsocks-v1.16.1.x86_64-unknown-linux-gnu.tar.xz

tar -xf  shadowsocks-v1.16.1.x86_64-unknown-linux-gnu.tar.xz -C /usr/local/bin/
```

## 二、配置文件

```bash
mkdir -p /etc/shadowsocks

vi /etc/shadowsocks/config.json

写入以下配置
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
systemctl daemon-reload  #Systemctl重载

systemctl start shadowsocks  #启动

systemctl restart shadowsocks 重启
systemctl enable shadowsocks #添加开机自启动

systemctl status shadowsocks #查看状态

```
