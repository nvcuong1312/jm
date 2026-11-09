# Cài đặt và sử dụng giả lập Symbian trong JM
## 1. Chuẩn bị: Firmware của dòng máy, có 2 kiểu: 
- Combo 2 file: .rom và .rpkg
- Đã đươc cài đặt sẵn, gồm 2 folder: roms và drivers

<img width="497" height="238" alt="image" src="https://github.com/user-attachments/assets/32c87a4c-ef19-4067-a35b-371a0d90f33b" />
<img width="522" height="218" alt="image" src="https://github.com/user-attachments/assets/30ce6a89-8f1d-49d3-a349-70c4def4a5f5" />


Cấu trúc của giả lập hiện tại:

```text
JM/
├── games/symbian/                      # Nơi đặt file game
└── emulators/symbian/
    ├── roms/                           # Nơi đặt .rom và .rpkg
    └── data/                           # Nơi đặt thư mục roms và thư mục drivers
```

## 2. Cài firmware từ ROM và RPKG

Ví dụ bộ firmware Nokia 5320, mã `RM-409`:

```text
JM/emulators/symbian/roms/rm-409/
├── 5320.rom
└── 5320.RPKG
```

1. Mở JM, nhấn **Y → Firmware manager** trong Game / Settings.
2. Dùng lên/xuống chọn thiết bị, trái/phải chọn hành động **Install**.
3. Nhấn **A** và chờ thao tác hoàn tất.
4. Nhấn **B** để quay về Settings.

## 3. Dùng data đã cài sẵn: roms và drivers

```text
JM/emulators/symbian/data/
```

### JM chưa có data

Chép thư mục `roms và drivers` vào `JM/emulators/symbian/data/`.

Sau khi chép, mở JM, bấm **Y → Firmware manager**, Firmwave
chưa đăng ký sẽ hiện **Ready to register**. Chọn **Install** để thêm vào registry.

## 4. Thêm game

Chép game vào:

```text
JM/games/symbian/
```

Các định dạng game đang được hỗ trợ:
`.sis`, `.sisx`
`.zip`, `.7z` -> Game N-Gage

## 5. Chọn đúng firmware và mở game

1. Chọn game trong launcher.
2. Bấm **Y → Firmware**.
3. Dùng trái/phải chọn thiết bị đã cài phù hợp.
4. Đóng Settings và nhấn **A: Play**.

## 6. Điều khiển và menu trong game

Trong chế độ Keypad, mặc định:

| Phím điện thoại | Nút tay cầm |
|-----------------|-------------|
| Chọn trái | Y |
| Chọn phải | A |
| OK | X |
| * | SELECT |
| # | START |
| 0 | B |
| 1 | L |
| 3 | R |
| 7 | L2 |
| 9 | R2 |

## 7. Thông tin liên hệ:
- Telegram: @cuongnv1312  
- YouTube: @YeuRetroHandheld
- Discord: https://discord.gg/HvX5Z6cbN3
- Ủng hộ: https://ko-fi.com/alcavic



https://github.com/user-attachments/assets/c51df280-63f4-48b2-b002-e96b9da94339


