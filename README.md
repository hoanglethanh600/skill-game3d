# game3d — Skill dựng web game 3D với phong cách đánh số

Skill cho Muse: dựng web game 3D nhiều người chơi (Three.js + Socket.IO) với **hệ phong cách ĐÁNH SỐ** để gọi bằng mã:

- **Nhân vật NV-01..NV-10** — mô phỏng chân thật, Pixar, chibi, anime cel-shading, bán chân thật, low-poly, voxel, đất sét, tiên hiệp, mô hình thu nhỏ
- **Ngoại cảnh NC-01..NC-07** — chân thật tự nhiên, pastel mềm, sa bàn diorama, voxel, low-poly phẳng, cel-shaded, đất sét
- **Biến thể** — thời gian TG-1..4, thời tiết TT-1..3, mùa/lễ M-1..6
- **Combo CB-01..CB-05** — CB-01 là bản đang chạy thật ở game [Gốc Cây Đầu Làng](https://goc-cay-dau-lang-hoangpro.onrender.com)

Kèm kiến trúc chuẩn đã kiểm chứng (server Node Socket.IO, client 1 file, Three.js vendor local, texture thủ tục, âm thanh WebAudio), quy tắc cứng (joystick không ngược hướng, HUD không chồng lấn trên điện thoại, kiểm chứng 2 client) và đường deploy GitHub + Render miễn phí.

🌐 **Trang giới thiệu + tải gói:** https://skill-game3d.vercel.app

## Cài đặt

1. Tải `skill-game3d.zip` từ trang trên (hoặc mục Releases/tệp trong repo này) và giải nén.
2. Chép thư mục `game3d` vào `~/workspace/custom-skills/` của Muse.
3. Gọi bằng mã số, ví dụ: *"tạo game 3D phong cách NV-05 + NC-06"*, *"đổi game sang CB-02, thêm TG-4"*.

## Cấu trúc repo

- `game3d/` — chính skill (SKILL.md, skill.yaml, reference/styles.json)
- `index.html` — trang giới thiệu (deploy Vercel)
- `skill-game3d.zip` — gói cài đặt sẵn

© By Hoang Kim Long - Email: tonyhoang.oliver@gmail.com
