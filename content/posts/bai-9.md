---
title: "Truyền file giữa Client và Server trong Java"
date: 2025-10-24T09:20:00+07:00
draft: false
tags: ["Java", "Socket", "File"]
---

Ứng dụng truyền file là một trong những bài thực hành quan trọng
trong môn Lập trình mạng Java.
Bài thực hành này giúp hiểu rõ cách sử dụng Socket để truyền dữ liệu
dưới dạng file giữa Client và Server.

---

## 1. Mô hình truyền file Client – Server

- **Client**: đọc dữ liệu từ file và gửi qua mạng  
- **Server**: nhận dữ liệu từ Client và ghi ra file  
- Dữ liệu được truyền theo từng khối byte  

---

## 2. Chương trình Client gửi file

```java
import java.io.FileInputStream;
import java.io.OutputStream;
import java.net.Socket;

public class SendFileClient {
    public static void main(String[] args) {
        try {
            // Kết nối đến Server
            Socket socket = new Socket("localhost", 1234);

            // Mở file cần gửi
            FileInputStream fis =
                new FileInputStream("test.txt");

            // Lấy luồng gửi dữ liệu
            OutputStream os =
                socket.getOutputStream();

            byte[] buffer = new byte[1024];
            int count;

            // Đọc file và gửi từng khối dữ liệu
            while ((count = fis.read(buffer)) > 0) {
                os.write(buffer, 0, count);
            }

            fis.close();
            socket.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

---

## 3. Chương trình Server nhận file

```java
import java.io.FileOutputStream;
import java.io.InputStream;
import java.net.ServerSocket;
import java.net.Socket;

public class ReceiveFileServer {
    public static void main(String[] args) {
        try {
            // Tạo ServerSocket lắng nghe tại cổng 1234
            ServerSocket server =
                new ServerSocket(1234);

            // Chờ Client kết nối
            Socket socket = server.accept();

            // Lấy luồng nhận dữ liệu
            InputStream is =
                socket.getInputStream();

            // Tạo file để ghi dữ liệu nhận được
            FileOutputStream fos =
                new FileOutputStream("receive.txt");

            byte[] buffer = new byte[1024];
            int count;

            // Nhận dữ liệu và ghi ra file
            while ((count = is.read(buffer)) > 0) {
                fos.write(buffer, 0, count);
            }

            fos.close();
            socket.close();
            server.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
``` 

--- 

## 4. Kết quả thực hiện

- File test.txt từ Client được gửi qua mạng

- Server tạo file receive.txt với nội dung giống file gốc

- Chương trình minh họa rõ cách truyền file bằng TCP Socket trong Java