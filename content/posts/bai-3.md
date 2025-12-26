---
title: "Đọc và ghi file văn bản trong Java"
date: 2025-12-06T08:30:00+07:00
draft: false
tags: ["Java", "File", "IO"]
---

Trong lập trình mạng, dữ liệu thường không chỉ được nhập trực tiếp từ bàn phím
mà còn được lưu trữ dưới dạng các tập tin văn bản.
Do đó, Java cung cấp các lớp hỗ trợ đọc và ghi file văn bản trong gói `java.io`.

Trong các bài thực hành lập trình mạng, file văn bản thường được dùng để:
- Lưu dữ liệu cấu hình
- Lưu nội dung gửi qua mạng
- Ghi log trong chương trình client–server

---

## 1. Ghi dữ liệu vào file văn bản

Để ghi dữ liệu vào file văn bản, Java thường sử dụng lớp `FileWriter`.
Lớp này cho phép ghi dữ liệu dạng ký tự vào file.

### Ví dụ ghi nội dung vào file văn bản

```java
import java.io.FileWriter;

public class WriteTextFile {
    public static void main(String[] args) {
        try {
            FileWriter writer = new FileWriter("data.txt");
            writer.write("Lap trinh mang Java\n");
            writer.write("Thuc hanh doc va ghi file");
            writer.close();

            System.out.println("Ghi file thanh cong");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

---

## 2. Đọc dữ liệu từ file văn bản

Sau khi đã ghi dữ liệu vào file, ta có thể đọc lại nội dung file bằng
`FileReader` kết hợp với `BufferedReader`.

Ví dụ đọc nội dung từ file văn bản:

```java
import java.io.BufferedReader;
import java.io.FileReader;

public class ReadTextFile {
    public static void main(String[] args) {
        try {
            BufferedReader reader =
                new BufferedReader(new FileReader("data.txt"));

            String line;
            while ((line = reader.readLine()) != null) {
                System.out.println(line);
            }

            reader.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

---

## 3. Giải thích chương trình

- `FileWriter`
Dùng để ghi dữ liệu dạng văn bản vào file.

- `BufferedReader`
Giúp đọc dữ liệu từng dòng, tăng hiệu suất so với đọc từng ký tự.

- `readLine()`
Trả về một dòng văn bản, trả về null khi hết file.

Những lớp này thường được sử dụng trong các bài thực hành trước khi
dữ liệu được gửi qua mạng.

---

## 4. Liên hệ bài học lập trình mạng

Trong các chương trình client–server:

- Client có thể đọc dữ liệu từ file để gửi lên server

- Server có thể ghi dữ liệu nhận được từ client vào file

Vì vậy, việc nắm vững cách đọc và ghi file văn bản là nền tảng quan trọng
trước khi học đến truyền dữ liệu qua Socket.