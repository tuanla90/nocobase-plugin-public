# Cài @tuanla90 plugins vào NocoBase (không cần upload file)

Các plugin trong repo này được đóng gói sẵn (`.tgz` ở `latest/@tuanla90/`). Cài vào **bất kỳ NocoBase 2.x** nào **mà không upload file qua trình duyệt** — server tự tải từ URL. Hợp khi thiết bị/mạng chặn upload `.tgz`, và để share cho instance người khác host.

## ⭐ Cách nhanh nhất — Plugin Hub (cài 1 lần, lo hết)
Cài **Plugin Hub** rồi nó tự cài/cập nhật mọi plugin còn lại từ manifest (`latest/index.json`) — khỏi dán URL 30+ lần.
1. Admin NocoBase → **Plugin manager → Add → URL** → dán:
   `https://raw.githubusercontent.com/tuanla90/nocobase-plugin-public/main/latest/@tuanla90/plugin-hub-0.2.3.tgz`
   → Install → **Enable**.
2. Vào **Settings → Plugin Hub → Kiểm tra ngay** → cài/cập nhật từng cái hoặc **Cập nhật tất cả**.

> Kiểm tra cập nhật hàng tuần — chỉ **báo**, không tự áp dụng.

## Cách thủ công (từng plugin, không cần Hub)
1. Admin NocoBase → **Plugin manager → Add** → nguồn **URL / npm** (KHÔNG chọn Local/Upload).
2. Dán **Install URL** (bảng dưới) → **Install** → **Enable**.
> Trình duyệt chỉ gửi một chuỗi URL; **server** NocoBase tải file. Nếu `@` trong URL lỗi, thay bằng `%40tuanla90`.

## ⚠️ Railway / Docker: bắt buộc volume cho `storage/`
Plugin cài lúc runtime nằm ở `storage/plugins` trên **service NocoBase** (không phải Postgres). Railway filesystem ephemeral → **mount volume vào `/app/nocobase/storage`**, nếu không plugin **mất khi redeploy**.

## Danh sách (6 plugin — sync theo `latest/@tuanla90/`)
| Plugin | Version | Install URL |
|---|---|---|
| app-doctor | 0.3.5 | `https://raw.githubusercontent.com/tuanla90/nocobase-plugin-public/main/latest/@tuanla90/plugin-app-doctor-0.3.5.tgz` |
| column-resize | 0.1.11 | `https://raw.githubusercontent.com/tuanla90/nocobase-plugin-public/main/latest/@tuanla90/plugin-column-resize-0.1.11.tgz` |
| custom-icons | 0.2.9 | `https://raw.githubusercontent.com/tuanla90/nocobase-plugin-public/main/latest/@tuanla90/plugin-custom-icons-0.2.9.tgz` |
| field-order | 0.2.5 | `https://raw.githubusercontent.com/tuanla90/nocobase-plugin-public/main/latest/@tuanla90/plugin-field-order-0.2.5.tgz` |
| hub | 0.2.3 | `https://raw.githubusercontent.com/tuanla90/nocobase-plugin-public/main/latest/@tuanla90/plugin-hub-0.2.3.tgz` |
| perf-guard | 0.1.12 | `https://raw.githubusercontent.com/tuanla90/nocobase-plugin-public/main/latest/@tuanla90/plugin-perf-guard-0.1.12.tgz` |

_Tự sinh từ `latest/@tuanla90/` bởi `build-env/gen-manifest.cjs`. Chạy lại sau mỗi lần rebuild._
