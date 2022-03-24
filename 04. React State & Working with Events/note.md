Thêm Event Listener cho các built-in HTML Element trong React Component thông qua các props đặc biệt onEvent (onClick,...). Các Event Listener này nhận vào một Function (eventHandler) để handle khi Event xảy ra.

Component Function được thực thi khi Component tương ứng được sử dụng (thường sẽ chỉ được thực thi một lần khi page được load lần đầu và Component <App /> được gọi)

state - Một giá trị được lưu trữ trong Component có thể thay đổi, mà thay đổi của giá trị này dẫn tới việc Component Function phải được thực thi lại
useState() chỉ được sử dụng bên trong Component Function, không phải bên ngoài, không phải bên trong nested function
useState() trả về một Array với 2 phần tử. Phần tử đầu tiên là state với giá trị ban đầu được set bởi tham số truyền vào cho useState(), phần tử thứ hai là một Function đóng vai trò cập nhật giá trị cho state đó
Mỗi khi Function cập nhật giá trị cho một state được gọi, Component Function sẽ được thực thi lại

Mỗi Component dù cùng loại cũng sẽ có state riêng biệt, state là dựa trên từng instance của một Component
Khi state được cập nhật thì chỉ có Component Function mang state đó mới được thực thi lại
Có thể dùng const bởi không bao giờ trực tiếp gán giá trị mới cho state qua toán tử gán (=) mà việc này được React thực hiện
useState() luôn trả về trạng thái mới nhất của một state. Nếu state lần đầu tiên được tạo, useState() sẽ gán giá trị khởi đầu cho nó nhưng những lần sau useState() sẽ không gán lại giá trị ban đầu đó một lần nữa mà chỉ trả về giá trị mới nhất của state đó

Một Component có thể có nhiều hơn 1 state và các state này là hoàn toàn riêng biệt với nhau, việc thay đổi một state sẽ không ảnh hưởng đến các state khác

Khi cập nhật state dựa trên state trước đó, nên sử dụng function form bởi React sẽ luôn pass in trạng thái mới nhất của state vào function đó, khiến việc cập nhật state dựa trên state trước đó chính xác hơn (React không cập nhật state ngay lập tức khi gọi hàm cập nhật state)

Two-Way Binding - Event Listener của một Element làm thay đổi state, đồng thời state thay đổi dẫn tới giá trị của Element đó thay đổi

Child-to-Parent Component Communication (Bottom-up) - Truyền Function được định nghĩa từ Parent Component vào Child Component dưới dạng prop. Function này sẽ được gọi bên trong Child Component và data mà Function này nhận vào từ Child Component đã trở nên khả dụng trong Parent Component

Lifting The State Up - Truyền data từ Child Component lên Parent Component để sử dụng trong Parent Component đó hoặc pass down xuống một Component khác cần data đó. Không nhất thiết luôn phải truyền data lên Root Component mà chỉ cần truyền lên tới một Parent Component gần nhất của Component chứa data và Component cần data đó

Mỗi khi sử dụng Two-Way Binding là sử dụng Controlled Component
Controlled Component - Cả data nhận vào và thay đổi tới data đó đều được xử lí ở Parent Component
Stateful Component vs Stateless Component - Component quản lí state và Component không quản lí state
