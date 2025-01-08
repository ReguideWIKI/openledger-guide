
## Bước 1: Tạo thư mục đích
Tạo thư mục để chứa nội dung giải nén:
```bash
mkdir -p openledger-node-1
```

## Bước 2: Giải nén file `.deb` vào thư mục
Di chuyển vào thư mục đích:
```bash
cd openledger-node-1
```

Sử dụng lệnh `ar` để giải nén file `.deb`:
```bash
ar x /root/openledger-node-1.0.0.deb
```

Sau khi chạy lệnh này, bạn sẽ thấy các file sau trong thư mục:
- `control.tar.xz`
- `data.tar.xz`
- `debian-binary`

## Bước 3: Giải nén `data.tar.xz`
Giải nén nội dung thực tế từ `data.tar.xz`:
```bash
tar -xf data.tar.xz
```

Nội dung sẽ được giải nén trực tiếp vào thư mục `/tmp/openledger-node-1`.

## Bước 4: (Tuỳ chọn) Giải nén `control.tar.xz`
Nếu cần kiểm tra thông tin cấu hình của gói, tạo thư mục con `control` và giải nén `control.tar.xz` vào đó:
```bash
mkdir -p control
tar -xf control.tar.gz -C control
```

## Bước 5: Kiểm tra nội dung
Sau khi hoàn thành các bước trên, kiểm tra nội dung thư mục bằng lệnh:
```bash
ls -l openledger-node-1
```

## Kết Quả
Toàn bộ nội dung của file `.deb` sẽ được giải nén trong thư mục `/openledger-node-1`. Bạn có thể làm việc với các file đã giải nén.
