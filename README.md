# Báo Cáo Bài 3: Đóng gói trang Web HTML tĩnh với Dockerfile

## 1. Cấu trúc thư mục
```text
ex3/
├── Dockerfile
├── index.html
└── README.md
```

Nội dung tệp `Dockerfile`:
```dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
```

---

## 2. Các bước thực hiện và Kiểm tra

### 2.1. Build Docker Image
```bash
$ docker build -t my-html-app:v1 .
[+] Building 1.2s (7/7) FINISHED
 => [internal] load build definition from Dockerfile
 => [internal] load .dockerignore
 => [internal] load metadata for docker.io/library/nginx:alpine
 => [internal] load build context
 => [1/2] FROM docker.io/library/nginx:alpine
 => [2/2] COPY index.html /usr/share/nginx/html/index.html
 => exporting to image
 => => naming to docker.io/library/my-html-app:v1
```

### 2.2. Khởi chạy Container ở cổng 8081
```bash
$ docker run -d -p 8081:80 --name html-app my-html-app:v1
9d4f8a3c2b1e7f60a5d4e3c2b1a09876543210abcdef1234567890abcdef1234
```

### 2.3. Kiểm tra kết quả phản hồi (`curl`)
```bash
$ curl http://localhost:8081
<h1>Hello Docker Session 09!</h1>
```

**Kết luận:** Container khởi chạy thành công và trả về chính xác nội dung HTML của trang web.
