# Python Cơ Bản: Kiểu Dữ Liệu & Vòng Lặp

Tài liệu này tổng hợp kiến thức về các **kiểu dữ liệu cơ bản** trong Python và **cách dùng vòng lặp `for`** để duyệt qua các kiểu này.

---

## 1. Kiểu Dữ Liệu Nguyên Thủy

| Kiểu       | Ví dụ           | Dùng để                |
| ---------- | --------------- | ---------------------- |
| `int`      | `5`, `-10`      | Số nguyên              |
| `float`    | `3.14`, `-0.5`  | Số thực (dấu chấm)     |
| `str`      | `"hello"`       | Chuỗi ký tự            |
| `bool`     | `True`, `False` | Biểu diễn đúng/sai     |
| `NoneType` | `None`          | Biểu thị không giá trị |

## ✅ Duyệt được bằng vòng lặp `for`: Iterable

| Kiểu dữ liệu | Mô tả               | Ví dụ lặp được     |
| ------------ | ------------------- | ------------------ |
| `list`       | Danh sách           | ✅                  |
| `tuple`      | Bộ giá trị cố định  | ✅                  |
| `set`        | Tập hợp không trùng | ✅                  |
| `dict`       | Từ điển (key-value) | ✅ (qua `.items()`) |
| `str`        | Chuỗi ký tự         | ✅                  |
| `range()`    | Dãy số sinh tự động | ✅                  |

```python
for x in [1, 2, 3]: print(x)           # list
for x in (1, 2, 3): print(x)           # tuple
for x in {"a", "b"}: print(x)          # set
for k, v in {"a": 1}.items(): print(k, v)  # dict
for ch in "abc": print(ch)             # str
```

---

## ❌ Không duyệt được trực tiếp: Non-iterable

| Kiểu dữ liệu | Mô tả            | Có duyệt được bằng `for` không? |
| ------------ | ---------------- | ------------------------------- |
| `int`        | Số nguyên        | ❌ Không                         |
| `float`      | Số thực          | ❌ Không                         |
| `bool`       | Đúng/sai         | ❌ Không                         |
| `NoneType`   | Không có giá trị | ❌ Không                         |

```python
# for i in 5: print(i)  ❌ TypeError: 'int' object is not iterable
```

👉 Nhưng các kiểu này có thể dùng trong `range()` để tạo iterable:

```python
for i in range(5): print(i)  # ✅ Tạo vòng lặp 0–4 từ số nguyên
```

---

## 2. Cấu Trúc Dữ Liệu

### 2.1 `list` – Danh sách

```python
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(f"Trái cây: {fruit}")
```

* Duy trì thứ tự
* Phần tử trùng lặp được
* Cho phép thay đổi nội dung, thứ tự, thêm hoặc xóa phần tử.
* Dùng khi dữ liệu cần cập nhật liên tục (danh sách việc cần làm, giỏ hàng,...).

### 2.2 `tuple` – Bộ giá trị cố định

```python
point = (10, 20)
for coord in point:
    print(f"Tọa độ: {coord}")
```

* Giống list nhưng không thay đổi được
* Không thể sửa, xóa, hoặc thêm phần tử sau khi đã tạo.
* Dùng khi dữ liệu mang tính cố định (tọa độ, cấu hình, hằng số,...).

### 2.3 `set` – Tập hợp không trùng lặp

```python
colors = {"red", "green", "blue"}
for color in colors:
    print(f"Màu: {color}")
```

* Không có thứ tự (dữ liệu in ra có thể hiện thị không đúng thứ tự ban đầu), không trùng lặp dữ liệu

### 2.4 `dict` – Từ điển key/value

```python
person = {"name": "A", "age": 21}
for key, value in person.items():
    print(f"{key}: {value}")
```

* Truy cập nhanh theo key

### 2.5 `str` – Chuỗi ký tự

```python
text = "hello"
for ch in text:
    print(f"Ký tự: {ch}")
```

---

## 3. Duyệt Danh Sách Từ Điển (List of Dicts)

```python
users = [
    {"name": "A", "role": "Admin"},
    {"name": "B", "role": "Viewer"}
]

for user in users:
    print(f"{user['name']} là {user['role']}")
```

---

## 4. Bảng So Sánh

| Kiểu    | Thứ tự | Trùng lặp | Thay đổi | Truy cập nhanh | Ghi nhớ                         |
| ------- | ------ | --------- | -------- | -------------- | ------------------------------- |
| `list`  | ✅      | ✅         | ✅        | Theo index     | Danh sách thông thường          |
| `tuple` | ✅      | ✅         | ❌        | Theo index     | Dữ liệu cố định                 |
| `set`   | ❌      | ❌         | ✅        | ChẮm           | Tài liệu duy nhất, không thứ tự |
| `dict`  | ❌      | Value ✅   | ✅        | Theo key       | Lưu dữ liệu rõ ràng (JSON/API)  |
