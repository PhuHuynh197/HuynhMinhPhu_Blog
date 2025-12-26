---
title: "Lập trình Single Thread trong Java"
date: 2025-10-11T09:00:00+07:00
draft: false
tags: ["Java", "Thread"]
---

Trong lập trình Java, thread (luồng) cho phép chương trình thực thi
các công việc một cách độc lập với luồng chính.
Thread là kiến thức quan trọng trong lập trình mạng, vì các chương trình
client–server thường phải xử lý nhiều tác vụ khác nhau.

Trước khi tìm hiểu về multi thread, cần nắm vững khái niệm và cách sử dụng
**single thread** trong Java.

---

## 1. Khái niệm Thread trong Java

Thread là một luồng thực thi độc lập trong chương trình.
Mỗi chương trình Java khi chạy đều có ít nhất một thread,
được gọi là **main thread**.

Java cho phép tạo thread mới bằng cách:
- Kế thừa lớp `Thread`
- Ghi đè phương thức `run()`

---

## 2. Tạo Single Thread bằng cách kế thừa Thread

Cách đơn giản nhất để tạo thread là kế thừa lớp `Thread`
và ghi đè phương thức `run()`.

### Ví dụ Single Thread

```java
public class SingleThreadDemo extends Thread {

    public void run() {
        for (int i = 1; i <= 5; i++) {
            System.out.println("Thread dang chay: " + i);
        }
    }

    public static void main(String[] args) {
        SingleThreadDemo t = new SingleThreadDemo();
        t.start();
    }
}
```

---

## 3. Giải thích chương trình

- `extends Thread`
Cho phép lớp kế thừa khả năng tạo luồng.

- `run()`
Chứa đ`oạn code sẽ được thực thi khi thread chạy.

- `start()`
Dùng để khởi động thread, Java sẽ tự động gọi phương thức `run()`.

Lưu ý: Không gọi trực tiếp `run()` vì như vậy chương trình
sẽ chạy như một phương thức bình thường, không tạo thread mới.

---

## 4. Ý nghĩa của Single Thread

Single thread giúp:

- Hiểu cách Java quản lý luồng

- Làm quen với cơ chế chạy song song

- Chuẩn bị nền tảng cho multi thread

Trong các bài thực hành lập trình mạng, thread thường được dùng
để xử lý các tác vụ nền hoặc các kết nối riêng biệt.