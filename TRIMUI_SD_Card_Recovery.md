# Hướng dẫn khôi phục bộ nhớ trong Trimui về nguyên bản nhà sản xuất

Máy Trimui có bộ nhớ trong được cài đặt hệ điều hành (OS) của nhà sản xuất. Hướng dẫn này sẽ giúp bạn **khôi phục bộ nhớ trong về trạng thái nguyên bản của nhà sản xuất** bằng phương pháp sử dụng thẻ nhớ cứu hộ (SD Recovery).

## 1. Tải file Recovery

Lựa chọn đúng phiên bản firmware tương ứng với thiết bị của bạn.

### Trimui BrickPro

- **Firmware:** [v1.1.1-20260717](https://github.com/trimui/firmware_brickpro/releases/tag/v1.1.1-20260717)
- **File Recovery:** `sd_recovery_tg4040_brick_pro_v1.1.1_20260717.7z`

### Trimui Brick

- **Firmware:** [v1.1.1-20251126](https://github.com/trimui/firmware_brick/releases/tag/v1.1.1-20251126)
- **File Recovery:** `sd_recovery_BRICK_tg3040_v1.1.1_20251126.zip`

### Trimui SmartProS

- **Firmware:** [v1.0.1](https://github.com/trimui/firmware_smartpro_s/releases/tag/v1.0.1)
- **File Recovery:** `sd_recovery_tg5050_smart_pro_S_v1.0.1_20251218.7z`

### Các dòng máy Trimui khác

Bạn có thể truy cập kho GitHub chính thức của Trimui để tìm firmware tương ứng với thiết bị của mình:

- [Trimui – GitHub Repositories](https://github.com/trimui?tab=repositories)

---

## 2. Giải nén file Recovery

Sau khi tải file Recovery về máy tính, hãy giải nén.

Bạn sẽ thấy các tệp cần thiết để thực hiện quá trình khôi phục, bao gồm tệp hình ảnh `.img` và các công cụ liên quan.

<img width="721" height="207" alt="image" src="https://github.com/user-attachments/assets/f979cb75-72ca-4e63-a4f6-cac8959fda1f" />


## 3. Flash file `.img` vào thẻ nhớ

1. Mở công cụ `Win32DiskImager`.
2. Chọn tệp hình ảnh `.img`.
3. Chọn đúng ổ đĩa thẻ nhớ cần thực hiện flash.
4. Tiến hành flash tệp `.img` vào thẻ nhớ.

> **Cảnh báo:** Kiểm tra kỹ ổ đĩa trước khi flash để tránh ghi đè nhầm dữ liệu trên thiết bị khác.

<img width="475" height="336" alt="image" src="https://github.com/user-attachments/assets/a60cd69c-863d-4c9e-aaba-1744ce8379dd" />


## 4. Khởi động Trimui bằng thẻ Recovery

1. Cắm thẻ nhớ đã flash vào máy Trimui.
2. Bấm nút nguồn để khởi động thiết bị.
3. Chờ máy tự động nhận diện thẻ Recovery và thực hiện quá trình cài đặt.

Quá trình này có thể mất một khoảng thời gian. Hãy chờ cho đến khi hoàn tất.

## 5. Xóa trạng thái cứu hộ khỏi thẻ nhớ

Sau khi quá trình khôi phục hoàn tất:

1. Tắt nguồn thiết bị Trimui.
2. Tháo thẻ nhớ khỏi máy.
3. Mở công cụ `PhoenixCard.exe`.
4. Thực hiện thao tác xóa thẻ nhớ khỏi trạng thái cứu hộ (Recovery).

## 6. Thực hiện cài đặt ban đầu

Sau khi hoàn tất quá trình khôi phục, hãy thực hiện các bước cài đặt ban đầu cho thiết bị theo hướng dẫn bên dưới:

https://github.com/nvcuong1312/jm/blob/main/TRIMUI_SD_Card_Setup.md

## Hoàn tất

Sau khi thực hiện đầy đủ các bước trên, bộ nhớ trong của máy Trimui sẽ được khôi phục theo firmware Recovery tương ứng với nhà sản xuất.

## Tham gia discord để được nhận thêm hỗ trợ
https://discord.gg/a6xfppEb5C

<img width="176" height="169" alt="image" src="https://github.com/user-attachments/assets/c5a07f9f-8852-4574-9b6c-6d0fb041401b" />

