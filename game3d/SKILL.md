---
name: game3d
description: "Game 3D — dựng web game 3D (Three.js + Socket.IO nhiều người chơi) với HỆ PHONG CÁCH ĐÁNH SỐ: nhân vật NV-01..NV-10 (mô phỏng chân thật, Pixar, chibi, anime cel-shading, bán chân thật, low-poly, voxel, đất sét, tiên hiệp, mô hình thu nhỏ), ngoại cảnh NC-01..NC-07 (chân thật tự nhiên, pastel mềm, sa bàn diorama, voxel, low-poly phẳng, cel-shaded, đất sét), biến thể thời gian TG-1..4 / thời tiết TT-1..3 / mùa lễ M-1..6 và combo CB-01..05. Người dùng gọi phong cách BẰNG SỐ (ví dụ 'nhân vật NV-01, cảnh NC-01'). Kèm kiến trúc chuẩn đã kiểm chứng (server Node Socket.IO, client 1 file, Three.js vendor local không phụ thuộc CDN, texture thủ tục, âm thanh WebAudio), quy trình dựng, quy tắc cứng (joystick không ngược hướng, HUD không chồng lấn trên điện thoại, kiểm chứng 2 client + ảnh chụp) và đường deploy GitHub private + Render free. Dùng khi người dùng yêu cầu tạo/sửa web game 3D, game nhiều người chơi, đổi phong cách đồ họa game, hoặc gọi mã NV-/NC-/CB-."
---

# Game 3D — hệ phong cách đánh số + khuôn dựng web game 3D

Skill này phục vụ hai việc: (1) **chọn phong cách bằng số thứ tự** — người dùng chỉ cần gọi mã (ví dụ "làm game NV-05 + NC-06", "đổi sang CB-02"), Muse tra bảng lấy đúng thông số dựng; (2) **dựng web game 3D nhiều người chơi** theo kiến trúc đã kiểm chứng thật ở game Gốc Cây Đầu Làng (Three.js + Socket.IO, live trên Render).

Bản máy đọc được của toàn bộ bảng phong cách nằm ở `reference/styles.json` (code, tên, dấu hiệu, thông số dựng, nội dung phù hợp, combo) — khi cần tra bằng script thì đọc file đó.

## Bảng 1 — Phong cách NHÂN VẬT (NV)

| Mã | Phong cách | Dấu hiệu nhận biết | Ghi chú dựng bằng code |
|---|---|---|---|
| NV-01 | Mô phỏng 3D chân thật | Tỉ lệ người thật (đầu ≈ 1/7,5 thân), da/vải màu tự nhiên, không má hồng | Vật liệu standard + texture thủ tục, nắng thật + bóng mềm |
| NV-02 | Hoạt hình 3D kiểu Pixar | Đầu ≈ 1/5 thân, mặt biểu cảm, màu tươi bóng | Mắt to vừa + điểm sáng, màu bão hoà cao |
| NV-03 | Chibi 3D | Đầu ≈ 1/2,5 thân, mắt rất to long lanh, má hồng, miệng nhỏ | Đầu scale lớn, má hồng là đĩa hồng mờ, tông pastel |
| NV-04 | Anime 3D (cel-shading) | Viền nét đen, tô màu phẳng 2–3 tông, tóc mảng lớn | Toon material + outline mesh |
| NV-05 | Bán chân thật | Đầu ≈ 1/6,5 thân, da mịn lý tưởng hoá, mắt hơi to | Standard material mịn + rim light nhẹ |
| NV-06 | Low-poly tối giản | Khối đa giác ít, mặt phẳng, màu phẳng | Flat shading, không texture — nhẹ nhất |
| NV-07 | Voxel / khối hộp | Toàn thân ghép từ khối vuông | Voxel mesh theo lưới ô |
| NV-08 | Đất sét (clay) | Bề mặt như nặn tay, tỉ lệ mềm | Texture noise mịn, palette đất, sáng ấm |
| NV-09 | Tiên hiệp 3D | Cổ trang, tóc dài, linh khí/hào quang | Phụ kiện kiếm/choàng + hạt phát sáng |
| NV-10 | Mô hình thu nhỏ | Như tượng nhựa nhỏ có đế tròn | Đế dưới chân, vật liệu nhựa bóng nhẹ |

## Bảng 2 — Phong cách NGOẠI CẢNH (NC)

| Mã | Phong cách | Dấu hiệu nhận biết | Đi cùng đẹp nhất |
|---|---|---|---|
| NC-01 | Chân thật tự nhiên | Vân gỗ/vỏ cây/cỏ/ngói có bề mặt, nắng thật, bóng mềm, sương xa, nước sông động | NV-01 (combo hiện hành) |
| NC-02 | Pastel mềm | Tán cây tròn mềm, màu sáng dịu, mây trắng tròn | NV-03 |
| NC-03 | Sa bàn thu nhỏ (diorama) | Cả cảnh như mô hình trên bàn, nổi khối khi nhìn từ trên | NV-10 |
| NC-04 | Voxel | Đồi/nhà/cây đều khối hộp theo lưới | NV-07 |
| NC-05 | Low-poly phẳng | Cảnh hình học ít mặt, trời gradient | NV-06 |
| NC-06 | Cel-shaded | Mây vẽ, màu tươi, viền nét ở vật chính | NV-04 |
| NC-07 | Đất sét | Nhà/cây như nặn tay, màu đất ấm | NV-08 |

## Bảng 3 — BIẾN THỂ phủ lên mọi phong cách

- **Thời gian:** TG-1 Bình minh (nắng vàng thấp, sương nhẹ) · TG-2 Trưa nắng (mặc định) · TG-3 Hoàng hôn (nắng cam, bóng dài) · TG-4 Đêm trăng (sao + đèn lồng/đèn nhà phát sáng)
- **Thời tiết:** TT-1 Nắng trong (mặc định) · TT-2 Sương sớm (fog dày thấp) · TT-3 Mưa (hạt mưa + đất ướt + tiếng mưa)
- **Mùa / lễ:** M-1 Xuân (hoa nở) · M-2 Hạ (mặc định, xanh đậm) · M-3 Thu (lá vàng, lá rụng) · M-4 Đông (tông lạnh, cây thưa) · M-5 Tết (đèn lồng đỏ, câu đối, đào/mai) · M-6 Trung thu (trăng tròn lớn, rước đèn)

## Bảng 4 — COMBO đã định sẵn (CB)

| Mã | Tên combo | Công thức |
|---|---|---|
| CB-01 | Làng quê chân thật — **hiện hành của Gốc Cây Đầu Làng** | NV-01 + NC-01 + TG-2 + TT-1 + M-2 |
| CB-02 | Làng chibi dễ thương | NV-03 + NC-02 + TG-1 + TT-1 + M-1 |
| CB-03 | Anime học đường | NV-04 + NC-06 + TG-3 + TT-1 + M-1 |
| CB-04 | Sa bàn chiến thuật | NV-10 + NC-03 + TG-2 + TT-1 |
| CB-05 | Cổ tích đất sét | NV-08 + NC-07 + TG-1 + TT-2 |

## Cách gọi dùng

- "Tạo game 3D [thể loại] phong cách NV-xx + NC-yy" → dựng mới theo đúng mã.
- "Đổi game sang CB-0x" / "đổi nhân vật sang NV-xx" → chỉ thay lớp phong cách tương ứng, GIỮ NGUYÊN gameplay, server, dữ liệu.
- Không gọi mã → mặc định **CB-01** cho game mô phỏng làng quê/xã hội; game cho trẻ nhỏ thì CB-02.
- Lịch sử chốt của Gốc Cây Đầu Làng (để không lặp lại đường vòng): NV-06/NC-05 low-poly bị chê xấu → NV-03/NC-02 chibi → người dùng chốt cuối **NV-01/NC-01 mô phỏng chân thật (CB-01)** ngày 2026-11-05.

## Kiến trúc chuẩn (đã kiểm chứng ở bản thật)

- **Server:** Node.js + Express + Socket.IO (`server.js`), phòng chơi cố định, đồng bộ vị trí/chat/biểu cảm theo thời gian thực, bảng xếp hạng lưu file `data/scores.json`.
- **Client:** MỘT file `public/index.html` (logic + giao diện), Three.js để trong `public/vendor/three.module.js` — **vendor local, không phụ thuộc CDN**, không có internet vẫn chạy.
- **Đồ họa bằng code:** nhân vật và cảnh dựng từ hình khối + **texture thủ tục vẽ bằng canvas** (gỗ, vỏ cây, cỏ, ngói, da, vải) — không tải model/texture ngoài, không tài nguyên trả phí.
- **Âm thanh:** tổng hợp **WebAudio** trong code (chim hót, gió qua lá, bước chân theo nhịp di chuyển, nước gần sông, tiếng báo chat/tương tác) — chỉ phát sau thao tác "Vào làng" (đúng chính sách autoplay), có tắt/chỉnh âm lượng trong Cài đặt.
- **Điều khiển:** máy tính WASD + click-đi-tới + kéo xoay camera; điện thoại joystick cảm ứng + nút tương tác.

## Quy tắc cứng

- **Joystick KHÔNG được ngược hướng:** đẩy trái → nhân vật đi trái THEO HƯỚNG NHÌN MÀN HÌNH ở mọi góc xoay camera (lỗi này người dùng đã bắt gặp thật trên bản live ngày 2026-11-05 — nguyên nhân thường gặp là mapping trục ngang không theo camera yaw). Bắt buộc kiểm chứng bằng test mô phỏng 4 hướng joystick + đối chiếu hướng dịch chuyển trên màn hình, và kiểm tra WASD/click không bị đảo theo.
- **HUD không chồng lấn trên màn hình dọc:** thanh trên, khung danh sách người chơi và hàng nút dưới phải co/xếp lại theo chiều ngang điện thoại; kiểm chứng bằng ảnh chụp viewport điện thoại thật (lỗi đã gặp: khung tên làng đè nút chức năng, nút Rời làng đè khung người chơi).
- **Chữ luôn trên nền đậm có khung** (quy tắc web chung của người dùng), bố cục full chiều ngang; dòng bản quyền cuối trang đúng mẫu chuẩn: "© By Hoang Kim Long - Email: tonyhoang.oliver@gmail.com" (không năm, tên không dấu trong dòng này).
- **Một lần đổi phong cách = một lần deploy:** khi có nhiều việc dồn (đổi đồ họa + sửa điều khiển + âm thanh...), gộp vào MỘT commit rồi push một lần để dịch vụ chỉ deploy lại một lượt.
- **Kiểm chứng trước khi báo xong:** chạy thử 2 client đồng thời (người thứ hai vào là người đầu thấy ngay; di chuyển/chat/biểu cảm truyền đúng; thoát thì số online giảm), chụp ảnh trong game (cận cảnh nhân vật + toàn cảnh + viewport điện thoại), mở link công khai kiểm tra đã cập nhật bản mới.

## Deploy

- Repo GitHub **private**, commit ký **bắt buộc** `hoanglethanh600 <196003470+hoanglethanh600@users.noreply.github.com>` (sai tác giả là Vercel/Render phía người dùng bị chặn âm thầm ở một số dịch vụ).
- Render: Blueprint từ `render.yaml` (runtime node, plan free, build `npm install`, start `npm start`) — push `main` là tự deploy. Gói Free sẽ ngủ khi không ai vào (lần mở đầu sau nghỉ chậm ~50 giây) và dữ liệu file (điểm) reset khi dịch vụ khởi động lại — phải nói rõ giới hạn này khi giao.

## Muse local adaptation (created 2026-11-05, not upstream)

- Skill này do Muse tạo tại chỗ cho người dùng Hoàng Kim Long theo yêu cầu "Tạo skill game3d với số thứ tự phong cách" (2026-11-05), chưng cất từ dự án thật Gốc Cây Đầu Làng (`~/workspace/goc-cay-multiplayer/`, live https://goc-cay-dau-lang-hoangpro.onrender.com, repo private `hoanglethanh600/goc-cay-dau-lang`).
- Hệ mã NV/NC/TG/TT/M/CB là quy ước riêng của skill này để người dùng gọi phong cách bằng số; khi thêm phong cách mới, cấp mã tiếp theo trong bảng tương ứng và cập nhật cả `reference/styles.json`.
