Styled Component - CSS chỉ có phạm vi ảnh hưởng với một Component nhất định mà không ảnh hưởng tới style của Component khác (thực chất là generate Unique CSS Class cho các Component để các style này không trùng nhau)

Có thể định nghĩa nhiều hơn 1 Component trong 1 file
Có thể sử dụng Dynamic Style thông qua prop hoặc dùng ${} trực tiếp trong CSS Rule trong phần định nghĩa Component Style

Để sử dụng CSS Module, cần import 1 Object từ CSS file (với tên file kết thúc bằng .module.css) và mỗi CSS Class trong CSS file sẽ tương ứng với 1 Property của Object đã import. Bản chất của CSS Module cũng là generate Unique CSS Class cho các Component
