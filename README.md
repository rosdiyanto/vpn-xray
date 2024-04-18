## FITUR XRAY TLS
- TROJAN WS        : **443**
- TROJAN GRPC      : **443**
- SHADOWSOCKS WS   : **443**
- SHADOWSOCKS GRPC : **443**
- VMESS WS         : **443**
- VMESS GRPC       : **443**
- VLESS WS         : **443**
- VLESS GRPC       : **443**

## FITUR XRAY HTTP
- TROJAN WS        : **80**
- TROJAN GRPC      : **80**
- SHADOWSOCKS WS   : **80**
- SHADOWSOCKS GRPC : **80**
- VMESS WS         : **80**
- VMESS GRPC       : **80**
- VLESS WS         : **80**
- VLESS GRPC       : **80**

## Requirements

- Ubuntu 20.04 

## Installation

1. Lakukan update/upgrade

    ```bash
    apt update && apt upgrade -y
    ```
2. Setting Cloudflare

    - Masuk ke DNS Records atur seperti ini

        Type  | Name           | Content            | Proxy Status | TTL 
        ------|----------------|--------------------|--------------|-----
        A     | vpn            | [IP Server VPS]    | DNS Only     | Auto 

    - Masuk ke SSL/TLS -> Overview -> (set ke full)
    - Masuk ke SSL/TLS -> Edge Certificates -> Always Use HTTPS -> (set ke off)
    - Masuk ke Network -> WebSockets -> (set ke on)

3. Masukan domain kamu atau bisa juga subdomain

    ```bash
    echo "vpn.domainmu.com" >/root/domain; mkdir -p /etc/xray; echo "vpn.domainmu.com" >/etc/xray/domain
    ```

4. Untuk install

    ```bash
    wget https://raw.githubusercontent.com/rosdiyanto/vpn-xray/main/setup.sh && chmod +x setup.sh && ./setup.sh
    ```

5. Lakukan reboot

    ```bash
    reboot
    ```

6. Install SSL

    ```bash
    certv2ray
    ```

    Jika ada tulisan hijau tandanya SSL berhasil di install

    ```bash
    restart-xray
    ```

7. Membuat akun TROJAN

    - Masuk ke menu ketik **xmenu**
    - Buat Akun Trojan

8. Lakukan reboot

    ```bash
    reboot
    ```

9. Cek apakah port 443 sudah open/listen

    ```bash
    netstat -tuln
    ```
    - Jika port sudah listen tandanya sudah berhasil 