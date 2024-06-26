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
        A     | domainmu.my.id   | [IP Server VPS]    | DNS Only     | Auto 

    - Masuk ke SSL/TLS -> Overview -> (set ke full)
    - Masuk ke SSL/TLS -> Edge Certificates -> Always Use HTTPS -> (set ke off)
    - Masuk ke Network -> WebSockets -> (set ke on)

3. Sesuaikan domain kamu atau bisa juga subdomain dibawah ini, silahkan ubah **vpn.domainmu.my.id**

    ```bash
    DOMAIN="vpn.domainmu.my.id"; echo "$DOMAIN" > /root/domain; mkdir -p /etc/xray; echo "$DOMAIN" > /etc/xray/domain
    ```

4. Untuk install VPN

    ```bash
    wget https://raw.githubusercontent.com/rosdiyanto/vpn-xray/main/setup.sh && chmod +x setup.sh && ./setup.sh
    ```

5. Install SSL

    ```bash
    certv2ray
    ```

    Jika ada tulisan hijau tandanya SSL berhasil di install

    ```bash
    restart-xray
    ```

    Lakukan restart xray

6. Tambakan auto reboot setiap pukul 6 AM
     ```bash
    (crontab -l ; echo "0 6 * * * /sbin/reboot") > temp && crontab temp && rm temp
    ```

    Lakukan cek cronjob

    ```bash
    crontab -e
    ```

7. Membuat akun Trojan

    - Masuk ke menu ketik **xmenu**
    - Buat Akun Trojan

    Lakukan reboot

    ```bash
    reboot
    ```

8. Cek port 443 apakah open

     ```bash
    result=$(netstat -tuln -p | grep ":443 "); echo "$result"; if [ -n "$result" ]; then echo "Port 443 is open"; else echo "Port 443 is closed"; fi
    ```

    ***Jika port 443 open, vpn sudah bisa digunakan***

    Untuk cek semua port yang open
    ```bash
    netstat -tuln -p
    ```

9. Selesai

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
