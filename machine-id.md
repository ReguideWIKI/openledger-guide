## Bước 1: Xóa file `machine-id` hiện tại
Xóa cả hai file `machine-id` nếu tồn tại:

```bash
sudo rm -f /etc/machine-id
sudo rm -f /var/lib/dbus/machine-id
```

## Bước 2: Tạo file `machine-id` mới thủ công
Sinh một UUID mới và ghi vào file `/etc/machine-id`:

```bash
uuidgen | tr -d '-' | sudo tee /etc/machine-id > /dev/null
```

Đồng bộ với DBus (nếu cần):

```bash
sudo ln -s /etc/machine-id /var/lib/dbus/machine-id
```

## Bước 3: Kiểm tra `machine-id` mới
Xác nhận `machine-id` đã được thay đổi bằng cách kiểm tra nội dung file:

```bash
cat /etc/machine-id
```

## Bước 4: Khởi động lại dịch vụ phụ thuộc (nếu cần)
Nếu có các dịch vụ phụ thuộc vào `machine-id`, khởi động lại chúng:

```bash
sudo systemctl restart systemd-networkd
sudo systemctl restart dbus
```

## Lưu ý
- Hãy chắc chắn rằng các file được tạo có quyền và quyền sở hữu phù hợp để tránh lỗi.
- Một số ứng dụng có thể yêu cầu khởi động lại để nhận diện `machine-id` mới.
