## Requirements

- Ubuntu 20.04 

## Installation

1. Lakukan update/upgrade

    ```bash
    apt update && apt upgrade -y && reboot
    ```
2. Setting Cloudflare

    - Masuk ke DNS Records atur seperti ini
        
        Jika pakai sub domain

        Type  | Name           | Content            | Proxy Status | TTL 
        ------|----------------|--------------------|--------------|-----
        A     | vpn            | [IP Server VPS]    | DNS Only     | Auto 

        Jika pakai domain
        
        Type  | Name           | Content            | Proxy Status | TTL 
        ------|----------------|--------------------|--------------|-----
        A     | domainmu.com   | [IP Server VPS]    | DNS Only     | Auto 

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

7. Membuat akun Trojan

    - Masuk ke menu ketik **xmenu**
    - Buat Akun Trojan

    Lakukan reboot

    ```bash
    reboot
    ```

8. Cek apakah port 443 sudah open/listen

    ```bash
    netstat -tuln
    ```
    Jika port sudah listen tandanya sudah berhasil 

9. Tambakan auto reboot setiap pukul 5 AM
     ```bash
    (crontab -l ; echo "0 5 * * * /sbin/reboot") > temp && crontab temp && rm temp
    ```

    Lakukan reboot

    ```bash
    reboot
    ```

10. Selesai

### Service Xray TLS dan HTTP

| Jenis            | Port TLS | Port HTTP |
|------------------|----------|-----------|
| TROJAN WS        | 443      | 80        |
| TROJAN GRPC      | 443      | 80        |
| SHADOWSOCKS WS   | 443      | 80        |
| SHADOWSOCKS GRPC | 443      | 80        |
| VMESS WS         | 443      | 80        |
| VMESS GRPC       | 443      | 80        |
| VLESS WS         | 443      | 80        |
| VLESS GRPC       | 443      | 80        |
