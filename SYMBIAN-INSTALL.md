# Cài đặt và sử dụng game Symbian trong JM

Cập nhật: 2026-10-29. Hướng dẫn theo mã nguồn JM hiện tại, dùng engine EKA2L1
native ARM64. Đường dẫn trong tài liệu tính từ thư mục **JM trên thẻ nhớ**.

## 1. Chuẩn bị

Bạn cần có:
- Firmware hoặc data thiết bị phù hợp với game.
- File game Symbian/N-Gage.

Game Symbian native cần firmware thiết bị. Không dùng bộ chạy Java J2ME để mở
file SIS. Cùng mang tên Symbian nhưng S60, UIQ và các thế hệ khác nhau có thể
không chạy được cùng một bản game.

Cấu trúc chính:

```text
JM/
├── games/symbian/                       # File game và shortcut
├── scripts/
│   ├── run-symbian.sh
│   ├── scan-symbian.sh
│   ├── prepare-symbian.sh
│   └── manage-symbian.sh
└── emulators/symbian/
    ├── eka2l1/
    │   ├── eka2l1_jm                    # Engine native
    │   ├── eka2l1_install               # Công cụ cài/đăng ký firmware
    │   ├── lib/
    │   ├── resources/
    │   ├── patch/
    │   ├── compat/
    │   └── scripts/
    ├── roms/                           # ROM/RPKG đầu vào
    ├── data/                           # Firmware đã cài, game và save
    └── runtime/                        # Cấu hình và log engine
```

Giữ nguyên các thư viện và tài nguyên đi kèm runtime. Khi chép bằng máy tính,
không làm mất quyền thực thi của binary và script trên hệ thống đích.

## 2. Cài firmware từ ROM và RPKG

Ví dụ bộ firmware Nokia 5320, mã `RM-409`:

```text
JM/emulators/symbian/roms/rm-409/
├── 5320.rom
└── 5320.RPKG
```

Mỗi thư mục mã thiết bị cần **đúng một file `.rom` và một file `.rpkg` cùng bộ
firmware**. Tên thư mục phải tương ứng mã thiết bị; nên dùng chữ thường như ví dụ.

1. Mở JM, nhấn **Y → Firmware manager** trong Game / Settings.
2. Nhấn **X** để quét lại nếu vừa chép firmware.
3. Dùng lên/xuống chọn thiết bị, trái/phải chọn hành động **Install**.
4. Nhấn **A** và chờ thao tác hoàn tất.
5. Nhấn **B** để quay về Settings.

Không mở game trong khi đang cài firmware. Nếu báo thiếu cặp ROM/RPKG hoặc mã
thiết bị không khớp, kiểm tra lại bộ đầu vào trước khi tiếp tục.

## 3. Dùng data đã cài sẵn

Nếu đã có data EKA2L1, không nhất thiết phải có lại ROM/RPKG đầu vào. Data đầy đủ
của một thiết bị cần ROM và ổ Z tương ứng, ví dụ:

```text
JM/emulators/symbian/data/
├── devices.yml                          # Registry nếu đã có
├── roms/rm-409/SYM.ROM
└── drives/z/rm-409/...
```

### JM chưa có data

Chép **nội dung bên trong** thư mục data nguồn vào `JM/emulators/symbian/data/`.
Tránh tạo nhầm `data/data/` hoặc để nguyên thư mục ngoài mang tên model.

### JM đã có thiết bị hoặc save

Chỉ bổ sung cây ROM/ổ Z của thiết bị mới và giữ `devices.yml` đang dùng. Nếu bộ
nguồn có ổ C/D/E dùng chung, không chép đè chúng lên dữ liệu đang sử dụng. Một số
bộ dùng ổ riêng tại `drives/<mã-thiết-bị>/`; cần giữ đúng cấu trúc của bộ đó.

Sau khi chép, mở **Y → Firmware manager**, nhấn **X** để quét. Thiết bị đầy đủ
chưa đăng ký sẽ hiện **Ready to register**. Chọn **Install** để thêm vào registry.
Nếu đã được đăng ký và sẵn sàng, chỉ cần chọn firmware đó cho game.

## 4. Thêm game

Chép game vào:

```text
JM/games/symbian/
```

Các định dạng launcher hiện nhận:

| Định dạng | Cách sử dụng |
| --- | --- |
| `.sis`, `.sisx` | Chép nguyên gói cài đặt. JM tự cài vào firmware được chọn ở lần mở đầu tiên. |
| `.zip`, `.7z` | Archive thẻ game N-Gage có cấu trúc phù hợp; không phải mọi archive đều là game có thể cài. |
| `.n-gage` | Chỉ dùng khi nội dung là archive thẻ được bộ đọc hiện tại hỗ trợ. Đổi đuôi file không chuyển đổi được định dạng bên trong. |
| `.eka2l1` | Shortcut mô tả firmware, UID hoặc đường dẫn gói game; xem mục 9. |

Launcher quét file ngay trong `games/symbian/`, không quét game đặt sâu trong
các thư mục con. Chuyển sang bộ lọc **Symbian** trong Game / Settings để tìm game.
Nếu chưa xuất hiện sau khi chép, mở lại launcher để quét danh sách mới.

### N-Gage đời đầu

ZIP/7z cần chứa cây dữ liệu thẻ như sau; giữ cả thư viện và dữ liệu đi kèm:

```text
system/
├── apps/<mã-game>/...
└── libs/...
```

Chọn firmware **Nokia N-Gage hoặc N-Gage QD** phù hợp. JM đọc ZIP/7z trực tiếp,
không cần giải nén thủ công. Việc archive có `system/apps/` là một dấu hiệu cấu
trúc, chưa đủ để khẳng định mọi file bên trong hợp lệ hoặc game chạy được.

Game N-Gage 2.0 không nên được coi là thẻ N-Gage đời đầu chỉ vì có đuôi `.n-gage`.

## 5. Chọn đúng firmware và mở game

1. Chọn game trong launcher.
2. Nhấn **X: Game info** để đọc các yêu cầu được khai báo trong gói.
3. Nhấn **B** để quay lại, sau đó **Y → Firmware**.
4. Dùng trái/phải chọn thiết bị đã cài phù hợp.
5. Đóng Settings và nhấn **A: Play**.

JM lưu lựa chọn firmware riêng cho game. Lần mở đầu tiên có thể mất thêm thời
gian để khởi tạo dữ liệu hệ thống và cài game. Các lần sau dùng lại ứng dụng
đã cài nếu còn hợp lệ. Đừng chạy đồng thời hai engine trên cùng data.

### Đánh giá yêu cầu của game

| Thông tin đọc được | Cách hiểu |
| --- | --- |
| S60 1st/2nd/3rd/5th Edition | Chọn firmware đúng họ và thế hệ; chỉ khớp chữ “Symbian” là chưa đủ. |
| UIQ hoặc Sony Ericsson P80x/P9xx | Cần firmware UIQ phù hợp; firmware Nokia S60 không thay thế được. |
| Product ID của một model | Ưu tiên đúng model đó và kiểm tra thêm yêu cầu phiên bản. |
| Không có model hoặc độ phân giải | Không có nghĩa game tự thích ứng với mọi thiết bị. |

Ví dụ đã đọc từ các file người dùng cung cấp trong quá trình phát triển:

- Bản Asphalt 2 dùng dữ liệu ảnh cố định **352×416** đã bị lỗi với E63
  **320×240**; người dùng xác nhận khởi động được khi chuyển sang firmware N80.
  Gói chỉ khai báo S60v3 nên metadata không nêu đầy đủ khác biệt này.
- `3d_motoracer-255884.sis` khai báo `SonyEricssonP80xPlatformProductID`,
  UID `0x101F80BE`: đây là bản dành cho P80x/UIQ, không phải bản Nokia S60.

Các ví dụ này áp dụng cho đúng bản file đã kiểm tra, không phải mọi game cùng tên.

## 6. Điều khiển và menu trong game

Trong chế độ Keypad, mặc định:

| Điều khiển | Tín hiệu gửi cho game |
| --- | --- |
| D-pad | Phím hướng của điện thoại |
| Joystick trái | Lên = 2, trái = 4, phải = 6, xuống = 8 |

Nhấn rồi thả **Menu** để mở menu game. Chọn **Swap D-pad / stick** để hoán đổi
hai ánh xạ. Lựa chọn được lưu trong `JM/emulators/config/symbian-controls.cfg`.
Điều hướng menu và hộp thoại vẫn dùng phím hướng.

- Trong menu: **A** chọn, **B** quay lại.
- **Giữ Menu + Down** để đóng game về JM.
- **Input: Keypad/Touch** chuyển chế độ nhập; Touch dùng con trỏ khi game cần.
- **Settings / config → Map controls** ánh xạ lại nút vật lý nếu cần.
- **Settings / config → Firmware → Save and restart game** đổi firmware rồi mở
  lại game. Chỉ đổi dòng Firmware chưa đủ để thay thiết bị đang chạy.

Ánh xạ nút số/softkey khác còn phụ thuộc `input.cfg` và `keymap.cfg` đang sử dụng.

## 7. Xem thông tin và lỗi lần chạy gần nhất

Nút **X: Game info** chỉ hiện khi game đang chọn là Symbian, kể cả trong bộ lọc
All. Dùng lên/xuống để cuộn, trái/phải để chuyển trang, B hoặc X để đóng.

Màn hình có thể hiển thị:

- Firmware đang chọn, tên và kích thước file, định dạng nhận diện từ header.
- Tên game, phiên bản, UID, nhà phát hành, ngôn ngữ nếu đọc được.
- Các yêu cầu nền tảng, model và component được khai báo trong SIS/SISX.
- Với ZIP: một phần danh sách ứng dụng/installer và dấu hiệu cấu trúc thẻ.
- Với 7z: thông tin container; màn hình hiện chưa giải mã danh sách file bên trong.
- Kết quả khởi động gần nhất của **đúng game và firmware đang chọn**: thời điểm,
  giai đoạn lỗi, mã thoát, thông báo runtime và một phần chẩn đoán engine.

Đường dẫn lịch sử:

```text
JM/games/symbian/.metadata/.symbian-runs/<FIRMWARE>/<tên-file-game>.last.log
```

Mỗi cặp game/firmware giữ kết quả gần nhất. Đổi firmware sẽ xem lịch sử của
firmware mới; chưa chạy thì báo chưa có lịch sử. Lịch sử không tự phục hồi cho
các lần chạy trước khi tính năng này được bổ sung.

Log chung của engine nằm tại:

```text
JM/emulators/symbian/runtime/EKA2L1/EKA2L1.log
```

Log chung có thể được thay thế khi mở game tiếp theo; nên dùng bản lịch sử theo
game/firmware để đối chiếu.

| Kết quả | Ý nghĩa |
| --- | --- |
| Exit code 0 | Runtime không báo lỗi qua mã thoát; chưa khẳng định game chơi hoàn chỉnh được. |
| Exit code 75 | Yêu cầu restart, không phải lỗi khởi động. |
| `KERN-EXEC 3` / Access violation | Game truy cập bộ nhớ không hợp lệ; chưa đủ để kết luận chọn sai firmware. |
| `Symbian is busy` | Có tiến trình khác đang dùng data; đóng tiến trình đó rồi thử lại. |

## 8. Sự cố thường gặp

| Hiện tượng | Kiểm tra |
| --- | --- |
| Không thấy game | Đúng thư mục, đúng đuôi hỗ trợ, file không nằm trong thư mục con; mở lại launcher. |
| Không có firmware để chọn | Cài hoặc đăng ký thiết bị trong Firmware manager; kiểm tra ROM/ổ Z có đủ không. |
| Không cài được archive | Kiểm tra cấu trúc thẻ game; archive chứa installer khác hoặc dữ liệu không đầy đủ có thể không được hỗ trợ. |
| Cài được nhưng mở là thoát | Xem Game info, nền tảng/model, độ phân giải bản game và log của firmware đó. |
| Game yêu cầu 2/4/6/8 | Dùng joystick trái hoặc bật Swap để D-pad gửi phím số. |
| Báo thiếu engine/installer | Chép đủ runtime EKA2L1 của bản JM tương ứng. Firmware không thay thế được engine. |

**Reinstall/Remove firmware có thể xóa ứng dụng và save trong ổ đĩa riêng của
thiết bị đó.** Sao lưu data trước khi dùng các thao tác này; không dùng Reinstall
như một bước mặc định mỗi khi game bị lỗi.

## 9. Shortcut `.eka2l1` khi cần chọn UID

Phần lớn gói một ứng dụng có thể mở trực tiếp. Với gói có nhiều ứng dụng, dùng
shortcut để chỉ rõ UID. Ví dụ `JM/games/symbian/TenGame.eka2l1`:

```ini
device=RM-409
package=TenGame.sisx
app=0x12345678
```

Thay mã firmware, tên gói và UID bằng giá trị thực của game. Đường dẫn `package`
tương đối được tính từ thư mục chứa shortcut.

Nếu ứng dụng đã cài trên firmware đó, có thể dùng shortcut chỉ có:

```ini
device=RM-409
app=0x12345678
```

Shortcut không chứa `package=` không cung cấp lại metadata yêu cầu của gói SIS
gốc. Không nhập UID ví dụ ở trên nếu chưa xác định UID thật.
