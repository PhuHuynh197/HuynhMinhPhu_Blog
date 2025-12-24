---
title: "Đọc và ghi file nhị phân trong Java"
date: 2025-12-24T08:45:00+07:00
draft: false
tags: ["Java", "Binary", "IO"]
---

Ngoài file văn bản, Java còn hỗ trợ làm việc với file nhị phân.
File nhị phân thường được dùng để lưu dữ liệu dạng số hoặc dữ liệu có cấu trúc,
giúp việc lưu trữ và truyền dữ liệu chính xác hơn.

Trong lập trình mạng, file nhị phân thường được sử dụng để:
- Lưu dữ liệu truyền qua mạng
- Lưu thông tin người dùng
- Lưu kết quả xử lý của server

---

## 1. Ghi dữ liệu vào file nhị phân

Java cung cấp lớp `DataOutputStream` để ghi dữ liệu nhị phân vào file.

### Ví dụ ghi file nhị phân

```java
import java.io.DataOutputStream;
import java.io.FileOutputStream;

public class WriteBinaryFile {
    public static void main(String[] args) {
        try {
            DataOutputStream dos =
                new DataOutputStream(new FileOutputStream("data.dat"));

            dos.writeInt(100);
            dos.writeDouble(8.5);
            dos.writeUTF("Lap trinh mang");

            dos.close();
            System.out.println("Ghi file nhi phan thanh cong");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

---

## 2. Đọc dữ liệu từ file nhị phân

Để đọc dữ liệu đã ghi, Java sử dụng lớp `DataInputStream`.

Ví dụ đọc file nhị phân

```java 

import java.io.DataInputStream;
import java.io.FileInputStream;

public class ReadBinaryFile {
    public static void main(String[] args) {
        try {
            DataInputStream dis =
                new DataInputStream(new FileInputStream("data.dat"));

            int number = dis.readInt();
            double score = dis.readDouble();
            String text = dis.readUTF();

            System.out.println(number);
            System.out.println(score);
            System.out.println(text);

            dis.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

---

## 3. Giải thích chương trình

- `DataOutputStream`
Ghi dữ liệu nhị phân theo đúng kiểu dữ liệu.

- `DataInputStream`
Đọc dữ liệu theo đúng thứ tự đã ghi.

Thứ tự đọc phải giống thứ tự ghi, nếu không sẽ gây lỗi.

--- 

## 4. Liên hệ bài học lập trình mạng

Trong lập trình mạng:

- Dữ liệu gửi qua Socket thường ở dạng nhị phân

- File nhị phân giúp đảm bảo dữ liệu không bị sai lệch

Do đó, nội dung file nhị phân là kiến thức quan trọng trước khi
học đến TCP Socket và truyền dữ liệu giữa client và server.