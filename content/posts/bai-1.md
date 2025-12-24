---
title: "Quản lý địa chỉ IP với lớp InetAddress"
date: 2025-12-24T08:00:00+07:00
draft: false
tags: ["Java", "Network"]
---

Trong lập trình mạng Java, việc xác định địa chỉ của máy cục bộ hoặc máy từ xa
là yêu cầu cơ bản khi xây dựng các ứng dụng client–server.
Java cung cấp lớp `InetAddress` thuộc gói `java.net` để thực hiện các công việc
liên quan đến địa chỉ IP và tên miền.

Lớp `InetAddress` hỗ trợ cả hai chuẩn địa chỉ **IPv4** và **IPv6**, đồng thời cho
phép phân giải tên miền (domain name) sang địa chỉ IP tương ứng.
Đây là lớp thường xuyên xuất hiện trong các bài thực hành lập trình mạng.

---

## 1. Tổng quan về InetAddress

`InetAddress` không có constructor công khai, vì vậy đối tượng của lớp này
được tạo thông qua các phương thức tĩnh.
Một số chức năng chính của `InetAddress` gồm:

- Phân giải tên miền sang địa chỉ IP
- Lấy thông tin host cục bộ
- Kiểm tra khả năng kết nối đến một host
- Hỗ trợ làm việc với mạng TCP và UDP

---

## 2. Phân giải tên miền sang địa chỉ IP

Trong thực tế, người dùng thường làm việc với tên miền thay vì địa chỉ IP.
Do đó, việc chuyển đổi từ tên miền sang IP là rất quan trọng.

### Ví dụ lấy địa chỉ IP của một website

```java
import java.net.InetAddress;

public class InetAddressDemo {
    public static void main(String[] args) {
        try {
            // Phân giải tên miền sang địa chỉ IP
            InetAddress address = InetAddress.getByName("www.hutech.edu.vn");

            // In ra địa chỉ IP
            System.out.println("Địa chỉ IP: " + address.getHostAddress());

            // In ra tên host
            System.out.println("Tên host: " + address.getHostName());
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

---

## 3. Phân tích chương trình

`InetAddress.getByName()`
Dùng để lấy thông tin địa chỉ IP từ một tên miền hoặc chuỗi IP.

`getHostAddress()`
Trả về địa chỉ IP ở dạng chuỗi, ví dụ: 203.113.xxx.xxx.

`getHostName()`
Trả về tên miền tương ứng với địa chỉ IP.

Đoạn chương trình trên thường được sử dụng trong các bài thực hành đầu tiên
để làm quen với lập trình mạng trong Java.

---

## 4. Lấy thông tin máy cục bộ

Ngoài việc làm việc với máy từ xa, InetAddress còn cho phép lấy thông tin
địa chỉ IP của chính máy đang chạy chương trình.

```java
import java.net.InetAddress;

public class LocalHostDemo {
    public static void main(String[] args) {
        try {
            InetAddress local = InetAddress.getLocalHost();
            System.out.println("Local IP: " + local.getHostAddress());
            System.out.println("Local Hostname: " + local.getHostName());
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

---

## 5. Ứng dụng thực tế

Lớp `InetAddress` thường được sử dụng trong:

- Chương trình chat client–server

- Ứng dụng truyền file qua mạng

- Kiểm tra trạng thái kết nối mạng

- Các hệ thống phân tán đơn giản

Việc nắm vững `InetAddress` là nền tảng quan trọng trước khi học đến
Socket, ServerSocket, TCP và UDP trong Java.