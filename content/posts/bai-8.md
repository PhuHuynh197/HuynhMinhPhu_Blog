---
title: "Lập trình UDP với Datagram trong Java"
date: 2025-12-24T10:00:00+07:00
draft: false
tags: ["Java", "Network", "UDP"]
---

Trong lập trình mạng, UDP (User Datagram Protocol) là giao thức truyền dữ liệu
không kết nối. UDP không đảm bảo độ tin cậy nhưng có tốc độ truyền nhanh.
Java hỗ trợ UDP thông qua các lớp `DatagramSocket` và `DatagramPacket`
trong gói `java.net`.

---

## 1. Đặc điểm của UDP

- Không cần thiết lập kết nối trước khi truyền dữ liệu  
- Dữ liệu được gửi dưới dạng các gói tin (datagram)  
- Không đảm bảo thứ tự và độ tin cậy  
- Phù hợp cho các bài thực hành so sánh với TCP  

---

## 2. UDP Client gửi dữ liệu

```java
import java.net.DatagramPacket;
import java.net.DatagramSocket;
import java.net.InetAddress;

public class UDPClient {
    public static void main(String[] args) {
        try {
            // Tạo socket UDP phía client
            DatagramSocket socket = new DatagramSocket();

            // Dữ liệu cần gửi
            String message = "Hello UDP Server";
            byte[] data = message.getBytes();

            // Địa chỉ IP server
            InetAddress serverAddress = InetAddress.getByName("localhost");

            // Tạo gói tin gửi đi
            DatagramPacket packet =
                new DatagramPacket(data, data.length, serverAddress, 9876);

            // Gửi gói tin
            socket.send(packet);

            // Đóng socket
            socket.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

---

## 3. UDP Server nhận dữ liệu

```java
import java.net.DatagramPacket;
import java.net.DatagramSocket;

public class UDPServer {
    public static void main(String[] args) {
        try {
            DatagramSocket socket = new DatagramSocket(9876);
            byte[] buffer = new byte[1024];

            DatagramPacket packet =
                new DatagramPacket(buffer, buffer.length);

            socket.receive(packet);

            String message =
                new String(packet.getData(), 0, packet.getLength());

            System.out.println("Nhan duoc: " + message);
            socket.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

---

## 4. Nhận xét

- UDP Client gửi dữ liệu mà không cần chờ phản hồi

- UDP Server luôn ở trạng thái chờ nhận datagram

- UDP thường được sử dụng trong các bài thực hành cơ bản
để so sánh với TCP