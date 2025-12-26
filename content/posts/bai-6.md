---
title: "Lập trình Multi Thread trong Java"
date: 2025-11-23T09:15:00+07:00
draft: false
tags: ["Java", "Multithread"]
---

Multi thread là kỹ thuật cho phép chương trình chạy nhiều luồng
cùng lúc để xử lý nhiều công việc song song.
Trong lập trình mạng, multi thread được sử dụng phổ biến
để server có thể phục vụ nhiều client đồng thời.

---

## 1. Khái niệm Multi Thread

Multi thread là việc tạo và quản lý nhiều thread trong cùng một chương trình.
Mỗi thread thực hiện một công việc riêng nhưng cùng chia sẻ tài nguyên hệ thống.

Việc sử dụng multi thread giúp:
- Tăng hiệu suất chương trình
- Tránh tình trạng chương trình bị treo
- Xử lý đồng thời nhiều yêu cầu từ client

---

## 2. Tạo nhiều thread trong Java

Java cho phép tạo nhiều thread bằng cách khởi tạo
nhiều đối tượng kế thừa từ lớp `Thread`.

### Ví dụ Multi Thread đơn giản

```java
class MyThread extends Thread {
    private String name;

    public MyThread(String name) {
        this.name = name;
    }

    public void run() {
        System.out.println("Thread dang chay: " + name);
    }
}

public class MultiThreadDemo {
    public static void main(String[] args) {
        MyThread t1 = new MyThread("Thread 1");
        MyThread t2 = new MyThread("Thread 2");
        MyThread t3 = new MyThread("Thread 3");

        t1.start();
        t2.start();
        t3.start();
    }
}
```

---

## 3. Giải thích chương trình

- Mỗi đối tượng `MyThread` đại diện cho một thread riêng biệt.

- Khi gọi `start()`, Java sẽ tạo luồng mới và chạy phương thức `run()`.

- Các thread có thể chạy song song, không theo thứ tự cố định.

Thứ tự in ra kết quả có thể khác nhau mỗi lần chạy chương trình.

---

## 4. So sánh Single Thread và Multi Thread

- Single Thread

    - Chỉ xử lý một công việc tại một thời điểm

     -Phù hợp với chương trình đơn giản

- Multi Thread

    - Xử lý nhiều công việc đồng thời

    - Phù hợp với server và ứng dụng mạng
