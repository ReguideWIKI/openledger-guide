## Bước 1: Cài Đặt Công Cụ `asar`

### 1.1: Cài Đặt Node.js và npm
Cài đặt Node.js và npm bằng lệnh:
```bash
sudo apt update
sudo apt install nodejs npm -y
```

### 1.2: Cài Đặt `asar`
Sau khi cài đặt Node.js, cài đặt `asar`:
```bash
npm install -g asar
```

---

## Bước 2: Giải Nén File `app.asar`

### 2.1: Tạo Thư Mục Chứa Nội Dung Giải Nén
Tạo thư mục mới để chứa nội dung giải nén:
```bash
mkdir /root/openledger-node-1/app
```

### 2.2: Giải Nén File `app.asar`
Sử dụng `asar` để giải nén:
```bash
asar extract /root/openledger-node-1/opt/OpenLedger\ Node/resources/app.asar /root/openledger-node-1/app
```

---

## Bước 3: Chỉnh Sửa Nội Dung

Di chuyển vào thư mục chứa nội dung đã giải nén:
```bash
cd /root/openledger-node-1/app
```

Sửa file cần thiết, ví dụ `main.js`:
```bash
nano build/electron/main.js
```

---

## Bước 4: Đóng Gói Lại File `app.asar`

Sau khi chỉnh sửa, đóng gói lại:
```bash
asar pack /root/openledger-node-1/app /root/openledger-node-1/opt/OpenLedger\ Node/resources/app.asar
```

---

## Bước 5: Khởi Động Lại Ứng Dụng

Khởi động lại `openledger-node`:
```bash
/root/openledger-node-1/opt/OpenLedger\ Node/openledger-node --no-sandbox
```

---

## Lưu Ý:

- **Backup file gốc**: Trước khi chỉnh sửa, hãy sao lưu file `app.asar`:
  ```bash
  cp /root/openledger-node-1/opt/OpenLedger\ Node/resources/app.asar /root/openledger-node-1/opt/OpenLedger\ Node/resources/app.asar.bak
  ```

- **Kiểm tra quyền thực thi**: Đảm bảo file thực thi (`openledger-node`) có quyền thực thi:
  ```bash
  chmod +x /root/openledger-node-1/opt/OpenLedger\ Node/openledger-node
  
