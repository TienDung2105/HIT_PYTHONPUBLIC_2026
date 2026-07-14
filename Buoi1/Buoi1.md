# Bài Tập Về Nhà Buổi 1 – Python cơ bản

## Bài 1: Python là ngôn ngữ thông dịch hay biên dịch? Tại sao?

**Python là ngôn ngữ thông dịch (interpreted language).**

**Tại sao?**

Mã nguồn Python không được biên dịch trực tiếp toàn bộ thành mã máy (machine code) để phần cứng thực thi ngay, giống như các ngôn ngữ biên dịch thuần túy C hay C++. Thay vào đó, quá trình chạy một chương trình Python trải qua hai bước:

1. Mã nguồn `.py` được biên dịch ngầm thành một dạng mã trung gian gọi là **bytecode** (thường lưu dưới file `.pyc`).
2. Bytecode này sau đó được **Python Virtual Machine (PVM)** đọc và thông dịch (interpret), thực thi **tuần tự từng dòng lệnh** tại thời điểm chương trình chạy.

Mặc dù có bước biên dịch ngầm ra bytecode, nhưng vì:
- Bytecode chỉ là mã trung gian, không phải mã máy trực tiếp cho CPU;
- Chương trình luôn phải chạy qua một trình thông dịch (interpreter) thay vì tạo ra file thực thi độc lập;
- Người lập trình không cần gọi một quy trình biên dịch riêng biệt trước khi chạy (không giống C/C++ phải compile ra `.exe` rồi mới chạy);

nên Python được phân loại rộng rãi là **ngôn ngữ thông dịch**, không phải biên dịch.

**Một số hệ quả từ đặc điểm này:**
- Nhờ chạy qua PVM, Python có tính **đa nền tảng (cross-platform)** — cùng một file `.py` chạy được trên Windows, Linux, macOS mà không cần biên dịch lại riêng cho từng hệ điều hành.
- Nhược điểm: do phải thông dịch trong lúc chạy nên tốc độ thực thi thường **chậm hơn** so với ngôn ngữ biên dịch như C/C++.

---

## Bài 2: Liệt kê các thành phần cơ bản trong Python

### a) Các kiểu dữ liệu trong Python

| Nhóm | Kiểu dữ liệu | Ví dụ |
|---|---|---|
| Số (Numeric) | `int` – số nguyên | `10`, `-5` |
| Số (Numeric) | `float` – số thực | `3.14`, `-0.5` |
| Số (Numeric) | `complex` – số phức | `2 + 3j` |
| Chuỗi (Text) | `str` | `"hello"`, `'Python'` |
| Dãy có thứ tự (Sequence) | `list` – có thể thay đổi | `[1, 2, "a"]` |
| Dãy có thứ tự (Sequence) | `tuple` – không thể thay đổi | `(1, 2, 3)` |
| Dãy có thứ tự (Sequence) | `range` – dãy số, thường dùng trong vòng lặp | `range(5)` |
| Ánh xạ (Mapping) | `dict` – lưu theo cặp key-value | `{"name": "John", "age": 20}` |
| Tập hợp (Set) | `set` – phần tử duy nhất, không thứ tự | `{1, 2, 3}` |
| Tập hợp (Set) | `frozenset` – giống set nhưng không đổi được | `frozenset({1, 2})` |
| Boolean | `bool` | `True`, `False` |
| Khác | `NoneType` – giá trị rỗng | `None` |
| Nhị phân (Binary) | `bytes`, `bytearray`, `memoryview` | `b"abc"` |

### b) Các toán tử trong Python

- **Toán tử số học (Arithmetic):** `+` (cộng), `-` (trừ), `*` (nhân), `/` (chia), `//` (chia lấy phần nguyên), `%` (chia lấy phần dư), `**` (lũy thừa)
- **Toán tử gán (Assignment):** `=`, `+=`, `-=`, `*=`, `/=`, `//=`, `%=`, `**=`
- **Toán tử so sánh (Comparison):** `==` (bằng), `!=` (khác), `>` (lớn hơn), `<` (nhỏ hơn), `>=` (lớn hơn hoặc bằng), `<=` (nhỏ hơn hoặc bằng)
- **Toán tử logic (Logical):** `and` (và), `or` (hoặc), `not` (phủ định)
- **Toán tử định danh / nhận dạng (Identity):** `is` (kiểm tra cùng một đối tượng trong bộ nhớ), `is not`
- **Toán tử thành viên (Membership):** `in` (kiểm tra phần tử có thuộc tập hợp không), `not in`
- **Toán tử thao tác bit (Bitwise):** `&` (AND), `|` (OR), `^` (XOR), `~` (NOT), `<<` (dịch trái), `>>` (dịch phải)

### c) Mệnh đề điều kiện và vòng lặp

**Mệnh đề điều kiện:**
- `if`: nếu điều kiện đúng thì thực thi.
- `elif` (else if): nếu điều kiện `if` sai thì kiểm tra tiếp điều kiện này.
- `else`: nếu tất cả điều kiện trên đều sai thì thực thi.

**Vòng lặp:**
- `for`: lặp qua một tập hợp (`list`, `string`, `tuple`, `dict`...) hoặc một dãy số (`range`) — dùng khi biết trước số lần lặp / cần duyệt qua dãy.
- `while`: lặp liên tục chừng nào điều kiện kiểm tra còn trả về `True` — dùng khi lặp theo điều kiện, không biết trước số lần lặp.


**Các từ khóa kiểm soát vòng lặp:**
- `break`: thoát khỏi vòng lặp ngay lập tức.
- `continue`: bỏ qua các lệnh còn lại trong lần lặp hiện tại, chuyển sang lần lặp tiếp theo.
- `pass`: lệnh giữ chỗ, không làm gì cả (dùng khi cú pháp yêu cầu phải có ít nhất 1 lệnh nhưng chưa muốn viết logic).
- `else` (đi kèm vòng lặp): thực thi khi vòng lặp kết thúc bình thường, không bị `break`.

### d) Kiểu dữ liệu True, False

- `True` và `False` là hai giá trị thuộc kiểu dữ liệu **Boolean (`bool`)** trong Python.
- Trong Python, giá trị hợp lệ chỉ là `True` (Đúng) hoặc `False` (Sai) — chữ cái đầu **bắt buộc viết hoa**.
- Về bản chất, `bool` là kiểu con của `int`: trong các phép toán số học, Python coi `True` tương đương số nguyên `1` và `False` tương đương số nguyên `0`.
- Đây thường là kết quả trả về của các phép so sánh, phép toán logic, và được dùng rộng rãi để điều khiển luồng thực thi trong các mệnh đề điều kiện (`if`, `while`).
