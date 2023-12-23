- **安装 shadowsocks 程序**

        wget https://github.com/shadowsocks/shadowsocks-rust/releases/download/v1.17.1/shadowsocks-v1.17.1.x86_64-unknown-linux-gnu.tar.xz && tar -xf shadowsocks-v1.17.1.x86_64-unknown-linux-gnu.tar.xz -C /usr/local/bin/ && chmod +x /usr/local/bin/ssserver && rm shadowsocks-v1.17.1.x86_64-unknown-linux-gnu.tar.xz

- **下载配置文件**

        mkdir/etc/shadowsocks/ curl -Lo /etc/shadowsocks/config.json https://raw.githubusercontent.com/MHY2233/SS/main/config.json

- **下载 service 文件**

        curl -Lo /etc/systemd/system/shadowsocks.service https://raw.githubusercontent.com/MHY2233/SS/main/shadowsocks.service && systemctl daemon-reload

- **启动 shadowsocks**

        systemctl enable -- now shadowsocks

- **重启 shadowsocks **

        systemctl restart shadowsocks 

- **查看 shadowsocks 运行状态**

        systemctl status shadowsocks 

- **查看日志**

        journalctl -u shadowsocks -o cat -e

- **查看实时日志**

        journalctl -u shadowsocks -o cat -f

- **卸载 shadowsocks**

        systemctl disable -- now shadowsocks && rm -rf /usr/local/bin/ssserver /etc/shadowsocks /etc/systemd/system/shadowsocks.service
