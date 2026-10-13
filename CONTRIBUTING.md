# Hướng dẫn đóng góp (Contributing Guide)

Cảm ơn bạn đã quan tâm đến `hello-oss-doc`! Tài liệu này hướng dẫn cách báo lỗi, gửi pull request và quy tắc đặt tên commit.

---

## 1. Cách báo lỗi (Reporting Issues)

Nếu bạn phát hiện lỗi, nội dung sai hoặc muốn đề xuất cải tiến, hãy mở một **Issue** trên GitHub.

### Trước khi tạo Issue

- Tìm kiếm trong [danh sách issue hiện có](https://github.com/roonau12-creator/-hello-oss-doc/issues) để tránh trùng lặp.
- Đảm bảo bạn đang dùng phiên bản mới nhất của dự án.

### Khi tạo Issue, hãy cung cấp

1. **Tiêu đề** ngắn gọn, mô tả rõ vấn đề.
2. **Mô tả chi tiết** — chuyện gì đang xảy ra và bạn mong đợi điều gì.
3. **Các bước tái hiện** (nếu là lỗi kỹ thuật):
   ```
   1. Chạy lệnh `npm run build`
   2. Mở file X
   3. Thấy lỗi Y
   ```
4. **Môi trường** — hệ điều hành, phiên bản Node.js, v.v.
5. **Screenshot hoặc log** nếu có.

### Nhãn Issue thường dùng

| Nhãn | Ý nghĩa |
|------|---------|
| `bug` | Lỗi cần sửa |
| `documentation` | Vấn đề về tài liệu |
| `enhancement` | Đề xuất cải tiến |
| `question` | Câu hỏi, cần làm rõ |
| `good first issue` | Phù hợp cho người mới đóng góp |

---

## 2. Cách gửi Pull Request (PR)

### Quy trình

1. **Fork** repository về tài khoản GitHub của bạn.

2. **Clone** fork về máy:
   ```bash
   git clone https://github.com/<your-username>/-hello-oss-doc.git
   cd -hello-oss-doc
   ```

3. **Tạo branch mới** từ `main` (không làm việc trực tiếp trên `main`):
   ```bash
   git checkout -b feat/ten-tinh-nang
   # hoặc
   git checkout -b fix/mo-ta-loi
   ```

4. **Thực hiện thay đổi** và commit theo [quy tắc đặt tên commit](#3-quy-tắc-đặt-tên-commit) bên dưới.

5. **Đồng bộ với upstream** trước khi push:
   ```bash
   git remote add upstream https://github.com/roonau12-creator/-hello-oss-doc.git
   git fetch upstream
   git rebase upstream/main
   ```

6. **Push branch** lên fork của bạn:
   ```bash
   git push origin feat/ten-tinh-nang
   ```

7. **Mở Pull Request** trên GitHub:
   - Chọn base: `roonau12-creator/-hello-oss-doc` → `main`
   - Điền tiêu đề và mô tả đầy đủ (xem mẫu bên dưới).

### Mẫu mô tả Pull Request

```markdown
## Tóm tắt thay đổi
<!-- Mô tả ngắn gọn bạn đã làm gì -->

## Lý do / Liên kết Issue
Closes #<số issue>

## Các thay đổi chính
- [ ] Thay đổi A
- [ ] Thay đổi B

## Kiểm tra
- [ ] Đã chạy `npm run build` thành công
- [ ] Đã kiểm tra trên trình duyệt / môi trường phù hợp
```

### Tiêu chí để PR được chấp nhận

- Không có conflict với branch `main`.
- Tuân thủ quy tắc đặt tên commit.
- Mô tả PR rõ ràng, liên kết Issue liên quan (nếu có).
- Không phá vỡ build hiện tại (`npm run build` phải pass).

---

## 3. Quy tắc đặt tên Commit

Dự án tuân theo chuẩn **[Conventional Commits](https://www.conventionalcommits.org/)**.

### Cú pháp

```
<type>(<scope>): <subject>
```

- **type**: loại thay đổi (bắt buộc)
- **scope**: phạm vi ảnh hưởng, ví dụ tên file/module (tùy chọn)
- **subject**: mô tả ngắn gọn, **không viết hoa chữ đầu**, **không có dấu chấm cuối**

### Các type hợp lệ

| Type | Dùng khi |
|------|---------|
| `feat` | Thêm tính năng mới |
| `fix` | Sửa lỗi |
| `docs` | Thay đổi tài liệu |
| `style` | Định dạng code (không ảnh hưởng logic) |
| `refactor` | Tái cấu trúc code |
| `test` | Thêm hoặc sửa test |
| `chore` | Công việc bảo trì, cấu hình |
| `ci` | Thay đổi CI/CD pipeline |
| `revert` | Hoàn tác commit trước đó |

### Ví dụ commit hợp lệ

```
feat(auth): thêm chức năng đăng nhập bằng GitHub
fix(navbar): sửa lỗi menu không đóng trên mobile
docs(readme): cập nhật hướng dẫn cài đặt
chore: nâng cấp dependency lên phiên bản mới
refactor(api): tách logic xử lý lỗi thành module riêng
```

### Ví dụ commit không hợp lệ

```
# ❌ Không rõ ràng
update stuff
fix bug
asdfgh

# ❌ Viết hoa chữ đầu của subject
feat: Thêm tính năng mới

# ❌ Thiếu type
thêm tính năng đăng nhập

# ❌ Có dấu chấm cuối
fix: sửa lỗi overflow.
```

### Commit có breaking change

Thêm `!` sau type hoặc ghi `BREAKING CHANGE:` trong phần body:

```
feat!: thay đổi cấu trúc API response

BREAKING CHANGE: trường `data` đổi thành `result` trong tất cả response.
```

---

## Câu hỏi?

Nếu bạn cần hỗ trợ, hãy mở một Issue với nhãn `question` hoặc liên hệ qua [GitHub Discussions](https://github.com/roonau12-creator/-hello-oss-doc/discussions).
