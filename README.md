# Triển khai Web Server Nginx trên Ubuntu Server :)

## 1. Mục tiêu

* Tạo user Linux.
* SSH bằng user mới.
* Cài đặt Nginx.
* Tạo website HTML.
* Cấu hình Nginx Server Block.
* Cấu hình UFW.
* Kiểm tra website bằng curl và trình duyệt.

## 2. Môi trường

* Cloud Server: WiServices
* OS: Ubuntu Server
* Web Server: Nginx
* HTTP Port: 80
* SSH Port: 22

## 3. User Linux

User sử dụng:

```text
student
```

Kiểm tra:

```bash
whoami
groups
```

## 4. Thư mục website

```text
/var/www/mywebsite/
```

File chính:

```text
/var/www/mywebsite/index.html
```

## 5. Cấu hình Nginx

File cấu hình:

```text
/etc/nginx/sites-available/mywebsite
```

Cấu hình:

```nginx
server {
    listen 80;
    listen [::]:80;

    server_name _;

    root /var/www/mywebsite;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

Kích hoạt website:

```bash
sudo ln -s /etc/nginx/sites-available/mywebsite /etc/nginx/sites-enabled/mywebsite
```

Kiểm tra cấu hình:

```bash
sudo nginx -t
```

Kết quả:

```text
syntax is ok
test is successful
```

## 6. Firewall UFW

Cho phép SSH:

```bash
sudo ufw allow OpenSSH
```

Cho phép HTTP:

```bash
sudo ufw allow 'Nginx HTTP'
```

Kiểm tra:

```bash
sudo ufw status
```

## 7. Kiểm tra Nginx

```bash
sudo systemctl status nginx
```

Kiểm tra website:

```bash
curl http://localhost
```

## 8. Truy cập website

Truy cập bằng trình duyệt:

```text
http://IP_SERVER
```

## 9. Minh chứng

Các ảnh minh chứng được lưu trong thư mục:

```text
screenshots/
```

Bao gồm:

* User Linux
* Nginx version
* Nginx configuration test
* Nginx service
* UFW
* Curl
* Website trên trình duyệt
