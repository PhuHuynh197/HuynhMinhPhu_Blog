---
title: "Tổng hợp mô hình Client – Server trong lập trình mạng Java"
date: 2025-03-07T10:20:00+07:00
draft: false
tags: ["Java", "Network", "ClientServer"]
---

Mô hình Client – Server là mô hình nền tảng trong lập trình mạng.
Toàn bộ các bài thực hành trong môn Lập trình mạng Java
đều xoay quanh mô hình này với hai giao thức chính là TCP và UDP.

---

## 1. Tổng quan mô hình Client – Server

- **Client**: khởi tạo kết nối và gửi yêu cầu  
- **Server**: chờ kết nối, xử lý yêu cầu và phản hồi  
- Hai bên giao tiếp thông qua mạng máy tính  

---

## 2. Mô hình TCP Client – Server

### TCP Client

```java
import java.io.DataInputStream;
import java.io.DataOutputStream;
import java.net.Socket;

public class TCPClient {
    public static void main(String[] args) {
        try {
            Socket socket = new Socket("localhost", 1234);

            DataOutputStream dos =
                new DataOutputStream(socket.getOutputStream());
            DataInputStream dis =
                new DataInputStream(socket.getInputStream());

            dos.writeUTF("Hello Server");
            String response = dis.readUTF();

            System.out.println("Server tra ve: " + response);

            socket.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

---

## 4. Luồng xử lý UDP Client – Server

```java
// UDP Client
DatagramSocket clientSocket = new DatagramSocket();

// UDP Server
DatagramSocket serverSocket = new DatagramSocket(9876);
```

---

## 5. Tổng kết bài học

- `InetAddress` dùng để xử lý địa chỉ IP

- File dùng để lưu và đọc dữ liệu

- Thread dùng để xử lý song song

- TCP đảm bảo độ tin cậy

- UDP đảm bảo tốc độ

Toàn bộ các nội dung trên là kiến thức cốt lõi
trong các bài thực hành lập trình mạng Java.