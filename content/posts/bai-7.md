---
title: "Lập trình TCP Client và TCP Server trong Java"
date: 2025-12-24T09:30:00+07:00
draft: false
tags: ["Java", "Network", "TCP"]
---

Trong mô hình lập trình mạng TCP, **Client** là phía khởi tạo kết nối đến Server.
Client sử dụng lớp `Socket` để kết nối đến địa chỉ IP và cổng (port) của Server.
Dưới đây là các khái niệm.

---

## 1. Khái niệm TCP Client

TCP Client chịu trách nhiệm:
- Kết nối đến TCP Server
- Gửi dữ liệu đến Server
- Nhận dữ liệu phản hồi từ Server

Trong Java, TCP Client được xây dựng dựa trên lớp `Socket`
thuộc gói `java.net`.

---

## 2. Tạo kết nối TCP Client

Client cần biết:
- Địa chỉ IP của Server
- Số cổng mà Server đang lắng nghe

---

## 3. Ví dụ chương trình TCP Client

```java
import java.io.DataInputStream;
import java.io.DataOutputStream;
import java.net.Socket;

public class TCPClient {
    public static void main(String[] args) {
        try {
            // Tạo kết nối đến Server
            Socket socket = new Socket("localhost", 1234);

            // Tạo luồng gửi dữ liệu
            DataOutputStream dos =
                new DataOutputStream(socket.getOutputStream());

            // Tạo luồng nhận dữ liệu
            DataInputStream dis =
                new DataInputStream(socket.getInputStream());

            // Gửi dữ liệu đến Server
            dos.writeUTF("Hello Server");

            // Nhận phản hồi từ Server
            String response = dis.readUTF();
            System.out.println("Server response: " + response);

            // Đóng kết nối
            socket.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

---

## 4. Ý nghĩa chương trình

- `Socket(host, port)` tạo kết nối TCP đến Server

- `DataOutputStream` dùng để gửi dữ liệu

- `DataInputStream` dùng để nhận dữ liệu

- TCP đảm bảo dữ liệu truyền đi chính xác và đầy đủ

TCP Client thường được dùng trong các bài thực hành
kết nối và trao đổi dữ liệu giữa hai máy.


Trong mô hình TCP, **Server** là phía lắng nghe và chấp nhận kết nối
từ các Client.
Server sử dụng lớp `ServerSocket` để mở cổng và chờ Client kết nối.

---

## 5. Khái niệm TCP Server

TCP Server có nhiệm vụ:
- Mở cổng chờ kết nối
- Nhận dữ liệu từ Client
- Xử lý và phản hồi dữ liệu

---

## 6. Tạo TCP Server trong Java

TCP Server sử dụng lớp `ServerSocket`
thuộc gói `java.net`.

---

## 7. Ví dụ chương trình TCP Server

```java
import java.io.DataInputStream;
import java.io.DataOutputStream;
import java.net.ServerSocket;
import java.net.Socket;

public class TCPServer {
    public static void main(String[] args) {
        try {
            // Tạo ServerSocket lắng nghe tại cổng 1234
            ServerSocket serverSocket = new ServerSocket(1234);
            System.out.println("Server dang cho ket noi...");

            // Chấp nhận kết nối từ Client
            Socket socket = serverSocket.accept();
            System.out.println("Client da ket noi");

            // Tạo luồng nhận dữ liệu
            DataInputStream dis =
                new DataInputStream(socket.getInputStream());

            // Tạo luồng gửi dữ liệu
            DataOutputStream dos =
                new DataOutputStream(socket.getOutputStream());

            // Nhận dữ liệu từ Client
            String message = dis.readUTF();
            System.out.println("Client gui: " + message);

            // Gửi phản hồi lại cho Client
            dos.writeUTF("Hello Client");

            // Đóng kết nối
            socket.close();
            serverSocket.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}