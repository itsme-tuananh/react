Authentication là cần thiết nếu Content (API Endpoint,...) cần được bảo vệ (không thể truy cập bởi tất cả user)
Quá trình 2 bước
1, Get access/permission
2, Send request to protected resource
Cách Authentication hoạt động
Server-side Session - Lưu trữ unique identifier trên Server, gửi identifier đó tới Client. Client gửi identifier cùng với request tới protected resource
Authentication Token - Tạo (nhưng không lưu) "permission" token trên Server, gửi token tới Client. Client gửi token cùng với request tới protected resource
