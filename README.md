# 📚 Hệ thống Quản lý Thư viện (Library SOA Project)

Dự án demo áp dụng kiến trúc **Service-Oriented Architecture (SOA)** và **Microservices** với Spring Boot. Hệ thống mô phỏng nghiệp vụ thư viện bao gồm: **Quản lý sách**, **Độc giả**, và **Mượn trả sách**.

---

## 📑 Table of Contents

- [🚀 Công nghệ sử dụng](#-công-nghệ-sử-dụng)  
- [📂 Cấu trúc hệ thống](#-cấu-trúc-hệ-thống)  
- [🛠 Hướng dẫn Cài đặt & Chạy](#-hướng-dẫn-cài-đặt--chạy)  
  - [1. Yêu cầu](#1-yêu-cầu)  
  - [2. Cài đặt](#2-cài-đặt)  
  - [3. Khởi chạy (Quan trọng)](#3-khởi-chạy-quan-trọng)  
- [🌐 Hướng dẫn Sử dụng](#-hướng-dẫn-sử-dụng)  
- [🧪 API Endpoints (Test Backend)](#-api-endpoints-test-backend)  

---

## 🚀 Công nghệ sử dụng

- **Java**: JDK 17 (hoặc 21)  
- **Framework**: Spring Boot 3.2.x  
- **Gateway**: Spring Cloud Gateway (Netty) - Cổng giao tiếp chính  
- **Communication**: OpenFeign (Giao tiếp giữa các service, không dùng Eureka)  
- **Database**: H2 Database (In-Memory) - Dữ liệu tự reset khi tắt ứng dụng  
- **Frontend**: HTML5 / Bootstrap 5 (Tích hợp sẵn trong Gateway)  

---

## 📂 Cấu trúc hệ thống

Hệ thống bao gồm **4 Service độc lập**:

| Service           | Mô tả                                      | Port |
|------------------|--------------------------------------------|------|
| `gateway-service` | Cổng chính, chứa giao diện Web UI (`index.html`) | 8080 |
| `book-service`    | Quản lý kho sách (CRUD)                     | 8081 |
| `user-service`    | Quản lý độc giả (CRUD)                      | 8082 |
| `borrow-service`  | Xử lý nghiệp vụ mượn sách, kết nối Book và User | 8083 |

---

## 🛠 Hướng dẫn Cài đặt & Chạy

### 1. Yêu cầu
- Cài đặt **Git**, **Java 17+**, **Maven**  
- IDE: **Spring Tool Suite 4 (STS)**, **IntelliJ IDEA**, hoặc **Eclipse**

### 2. Cài đặt
Clone dự án về máy:

git clone <link-dự-án-của-bạn>

### 3. Khởi chạy (Quan trọng)
Bạn cần chạy lần lượt 4 Service theo thứ tự sau để tránh lỗi kết nối:

# Chạy book-service (Port 8081)
# Chạy user-service (Port 8082)
# Chạy borrow-service (Port 8083)
# Chạy gateway-service (Port 8080)


Lưu ý: Nếu dùng STS4, hãy dùng Boot Dashboard để start cả 4 cùng lúc.

## 🌐 Hướng dẫn Sử dụng

1. Đảm bảo cả 4 service đều đã chạy (Console không báo lỗi)  
2. Mở trình duyệt truy cập:

```text
http://localhost:8080

Đăng nhập demo:

Username: vanlan

Hoặc đăng ký tài khoản mới

##🧪 API Endpoints (Test Backend)

Nếu không dùng giao diện, bạn có thể gọi API qua Gateway (Port 8080):

# Lấy danh sách sách
GET http://localhost:8080/books

# Lấy danh sách user
GET http://localhost:8080/users

# Mượn sách
POST http://localhost:8080/borrows
Content-Type: application/json

{
  "userId": 1,
  "bookId": 1
}

Dự án demo phục vụ môn học Kiến trúc phần mềm / SOA

