Component - Building Block của UI

Import Library / JS file -> Không cần thêm file extension
Import non-JS file -> Cần thêm file extension

Component trong React về bản chất chỉ là JavaScript function
Custom Component được sử dụng giống như HTML element thông thường, nhưng buộc phải bát đầu bằng một uppercase character để được phát hiện bởi React

Chỉ có thể có một Root Element ở return statement bên trong một Custom Component

Sử dụng className thay vì class bên trong một element trong JSX code

Sử dụng {} syntax để thêm dynamic data vào JSX code

prop - Data mà một Custom Component nhận được từ bên ngoài thông qua custom attribute của nó (thực chất là một object lưu trữ tất cả attribute của Custom Component đó dưới dạng key của nó và giá trị của những attribute đó dưới dạng value của key)

Sử dụng <SelfClosingElement /> khi element không có content giữa openning và closing tag
Pass data giữa các component thông qua prop bằng cách pass data đó qua nhiều bậc của child component (nested component)

Composition - Kết hợp các Component để tạo nên UI
Wrapper Component - Component bao xung quanh các Component khác và phải được thiết lập một số thuộc tính nhất định (bởi Wrapper Component cũng là một Custom Component nên không có các thuộc tính này như các HTML Element được support) như
props.children - Tất cả Content nằm giữa Openning Tag và Closing Tag của một Component
props.className - Tất cả CSS Class được thiết lập ở thuộc tính className của một Component
