# Bài 5: Khởi chạy dịch vụ đơn giản với Docker Compose

## Mục tiêu
- Viết tệp `docker-compose.yml` tối giản để quản lý và khởi chạy dịch vụ theo cú pháp Compose Spec.
- Sử dụng Docker Compose CLI v2 (`docker compose`).

---

## 1. Cấu hình `docker-compose.yml`

```yaml
services:
  web:
    image: nginx:alpine
    ports:
      - "8082:80"
```

---

## 2. Thao tác và Lệnh Điều phối CLI

### 1. Khởi chạy dịch vụ ngầm (`docker compose up -d`):
```bash
$ docker compose up -d
[+] Running 2/2
 ✔ Network b5_default  Created
 ✔ Container b5-web-1  Started
```

### 2. Kiểm tra trạng thái dịch vụ (`docker compose ps`):
```bash
$ docker compose ps
NAME       IMAGE          COMMAND                  SERVICE   CREATED          STATUS          PORTS
b5-web-1   nginx:alpine   "/docker-entrypoint.…"   web       10 seconds ago   Up 10 seconds   0.0.0.0:8082->80/tcp
```

### 3. Kiểm tra phản hồi HTTP qua `curl`:
```bash
$ curl -I http://localhost:8082
HTTP/1.1 200 OK
Server: nginx/1.25.5
Connection: keep-alive
```

### 4. Dừng và gỡ bỏ toàn bộ dịch vụ (`docker compose down`):
```bash
$ docker compose down
[+] Running 2/2
 ✔ Container b5-web-1  Removed
 ✔ Network b5_default  Removed
```
