---
title: "Làm việc với tập tin và thư mục trong Java"
date: 2025-12-15T08:15:00+07:00
draft: false
tags: ["Java", "File", "IO"]
---

Trong lập trình mạng, dữ liệu thường được lưu trữ hoặc trao đổi thông qua
các tập tin trên máy tính.
Vì vậy, Java cung cấp các lớp trong gói `java.io` để hỗ trợ làm việc với
tập tin và thư mục.

Trong các bài thực hành lập trình mạng, thao tác với file thường được dùng
để đọc dữ liệu, ghi dữ liệu hoặc chuẩn bị dữ liệu trước khi truyền qua mạng.

---

## 1. Lớp File trong Java

Lớp `File` đại diện cho một tập tin hoặc một thư mục trong hệ thống.
Lớp này không dùng để đọc hoặc ghi dữ liệu trực tiếp, mà dùng để:

- Kiểm tra sự tồn tại của file hoặc thư mục
- Tạo hoặc xóa file, thư mục
- Lấy thông tin về đường dẫn, tên file
- Liệt kê các file con trong thư mục

---

## 2. Kiểm tra sự tồn tại của file và thư mục

Trước khi thao tác với file, cần kiểm tra file hoặc thư mục đó có tồn tại hay không.

```java
import java.io.File;

public class FileCheckDemo {
    public static void main(String[] args) {
        File file = new File("D:/Data/demo.txt");

        if (file.exists()) {
            System.out.println("File tồn tại");
        } else {
            System.out.println("File không tồn tại");
        }
    }
}
```

---

## 3. Làm việc với thư mục

Java cho phép kiểm tra một đối tượng File có phải là thư mục hay không
và liệt kê các file con bên trong thư mục đó.

Ví dụ liệt kê các file trong một thư mục

```java
import java.io.File;

public class DirectoryDemo {
    public static void main(String[] args) {
        File dir = new File("D:/Data");

        if (dir.exists() && dir.isDirectory()) {
            File[] files = dir.listFiles();

            for (File f : files) {
                System.out.println(f.getName());
            }
        }
    }
}
```

---

## 4. Giải thích chương trình

- `exists()`
Dùng để kiểm tra file hoặc thư mục có tồn tại hay không.

- `isDirectory()`
Kiểm tra đối tượng File có phải là thư mục.

- `listFiles()`
Trả về danh sách các file và thư mục con.

Những thao tác này thường được sử dụng trước khi thực hiện đọc hoặc ghi file.

---

## 5. Liên hệ bài thực hành lập trình mạng

Trong các bài thực hành tiếp theo, file và thư mục thường được dùng để:

- Đọc dữ liệu từ file để gửi qua mạng

- Ghi dữ liệu nhận được từ client/server vào file

- Quản lý dữ liệu trong các chương trình truyền file

Do đó, việc nắm vững lớp File là kiến thức nền quan trọng trước khi
làm việc với Socket và truyền dữ liệu qua mạng.