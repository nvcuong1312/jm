# Hướng dẫn giả lập J2ME trên máy game cổ (Retro Handheld)

---

## 1. Giới thiệu

Game Java (J2ME) từng là tuổi thơ của rất nhiều người với các tựa game như:

- Ninja School  
- Avatar  
- Diamond Rush

  <img width="1536" height="2048" alt="image" src="https://github.com/user-attachments/assets/403a4c4c-4f38-4cf9-8f20-037bb47ab0ed" />


Tuy nhiên ngày nay rất khó để chơi lại trên điện thoại cũ.

May mắn là chúng ta có thể sử dụng **FreeJ2ME** để chạy game Java trên các máy game cổ chạy Linux như:

- TrimUI  
- RG351  
- Miyoo (CFW)  
- ArkOS  
- JELOS  
- AmberELEC  

Trong bài viết này mình sẽ hướng dẫn cài đặt và cấu hình chi tiết.

---

## 2. Chuẩn bị

Bạn cần:

- Máy game cổ hỗ trợ **PortMaster** (ArkOS, JELOS,…)
- Đã cài PortMaster
- Game J2ME định dạng `.jar`
- Gói JM.zip ở đây [Link quảng cáo](https://shrinkme.click/J2me) / Hoặc JM.zip trong mục Release


---

## 3. Cài đặt

### Bước 1: Chép JM vào thư mục autoinstall của PortMaster

<img width="492" height="103" alt="image" src="https://github.com/user-attachments/assets/ac70d3f9-a533-4bb9-b977-2648d9da06f9" />


Thư mục `autoinstall` có thể khác nhau tùy firmware (ArkOS, JELOS, AmberELEC…).

Tham khảo vị trí thư mục tại:
https://portmaster.games/faq.html

---

### Bước 2: Cài đặt tự động

1. Mở ứng dụng **PortMaster**
2. Hệ thống sẽ tự động cài đặt
3. Sau khi hoàn tất, giả lập **JM** sẽ xuất hiện trong mục **Game Ports**

> Lưu ý:
> - Một số firmware yêu cầu cập nhật lại danh sách game  
> - Hoặc khởi động lại máy nếu chưa thấy trong mục Ports  

---

## 4. Cách sử dụng

### Chép game

Cấu trúc thư mục:

```
/roms/ports/JM/
 └── Jars/
     ├── 128x128/
     ├── 240x320/
     ├── 320x240/
     └── 640x360/
```

Đây là nơi bạn cần chép các game `.jar`.

Game J2ME được thiết kế theo độ phân giải màn hình điện thoại đời cũ.  
Vì vậy bạn cần chép game vào đúng thư mục tương ứng.

Ví dụ:

```
Game 128x128 → /roms/ports/JM/Jars/128x128/
```

---

### Mở JM Launcher

Vào **Game Ports → JM Launcher**

---
<img width="640" height="480" alt="muOS_20260212_1344_0" src="https://github.com/user-attachments/assets/a2bed35e-0ff3-4b52-8cad-9547ab09b166" />


## Điều khiển cơ bản

### Bàn phím chính

| Nút | Chức năng |
|------|-----------|
| A | Play - 30fps |
| X | Play - 60fps (một số game khó nhập text ở chế độ này) |
| B | Exit |
| Start | Xoá file map phím |
| D-Pad | Di chuyển |

---

## Map phím lần đầu

Ở lần đầu mở game, bạn cần thực hiện map phím.

Hệ thống sử dụng các nút:

```
UP
DOWN
LEFT
RIGHT
A
B
X
Y
L1
L2
R1
R2
SELECT
START
MENU
```

Hãy bấm lần lượt theo hướng dẫn trên màn hình.

---

### Sau khi map xong

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

---

## Hệ thống Hotkeys

| Tổ hợp | Chức năng |
|---------|-----------|
| MENU + UP | Bật bàn phím T9 |
| MENU + DOWN | Thoát game |
| MENU + Y | Bật/tắt con trỏ cảm ứng |
| MENU + B | Xoay màn hình |

---

## Cách sử dụng bàn phím T9

1. Bấm `MENU + UP` để bật bàn phím  
2. Dùng D-Pad để chọn phím  
3. Nhấn `X` để click phím  
4. `A` để thực hiện nút chọn trái (thường là xoá ký tự)  
5. `B` để tắt bàn phím  

---

## 5. Lưu ý về phiên bản chia sẻ

Phiên bản JM mình chia sẻ trong bài viết này có watermark trong quá trình sử dụng.

Watermark không ảnh hưởng đến:

- Hiệu năng  
- Khả năng chạy game  
- Tính tương thích  

Mục đích của watermark là để xác định nguồn phát hành và hỗ trợ duy trì dự án.

---

## Phiên bản không watermark

Nếu bạn muốn sử dụng phiên bản không watermark, vui lòng liên hệ trực tiếp để trao đổi thêm về bản đầy đủ.

Thông tin liên hệ:

- Telegram: @cuongnv1312  
- YouTube: @YeuRetroHandheld  

---
