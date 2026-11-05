# Bài 1 : Vá lỗ hổng rò rỉ API Key trên GitHub
# Yêu cầu đầu ra
- Do file .gitignore chỉ có ghi node_modules/ và dist/ , không có khai biến .env nên mới bị đẩy lên GitHub
- Hoặc nếu file .env đã được commit trước đó khiến Git theo dõi, thì .gitignore không có tác dụng dấu file, vì .gitignore chỉ áp dụng cho tệp chưa được theo dõi (untracked).
## Cung cấp nội dung tệp .gitignore đã được sửa đúng
```gitignore
node_modules/
dist/
.env
.env.example
```

- .env: chặn tệp chính và các biến thể (.env.local, .env.production,...).
- .env.example: ngoại lệ, cho phép đẩy tệp mẫu chỉ chứa tên biến, không có giá trị thật.

Ví dụ mô tả bên trong .env.example:

.env.example
OPENAI_API_KEY=your_key_here

## Giải thích cơ chế ẩn thông tin trên VS Code.
VS Code đọc .gitignore và làm việc với Git qua Source Control, không thể tự mã hóa , ẩn nội dung tệp.

| Hiện tượng                                                                                                  | Ý nghĩa                                                                                                   |
| ----------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| Làm mờ (Dimming) trong File Explorer :Tên tệp .env hiện sẽ màu xám mờ trong Explorer                        | Tệp khớp quy tắc ignore, Git sẽ bỏ qua                                                                    |
| Tệp nằm trong .gitignore sẽ không xuất hiện trong tab Source Control                                        | Không thể vô tình stage hay commit tài liệu nhạy cảm                                                      |
| Nếu tệp .env chưa được bỏ qua ,tệp sẽ hiện chữ U (Untracked) màu xanh lá hoặc màu xanh dương (M - Modified) | Cảnh báo cho người dùng biết: chưa bị Git nó ignore, git add . sẽ đưa vào commit làm lộ tài liệu nhạy cảm |

