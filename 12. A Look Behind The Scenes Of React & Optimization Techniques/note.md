React - Component (Virtual DOM) & ReactDOM - Real DOM
Re-Evaluating Component !== Re-Rendering the DOM => Real DOM chỉ thay đổi khi có sự khác biệt giữa các Evaluation
Virtual DOM Diffing

Re-Evaluating Parent Component luôn kéo theo Re-Evaluating Child Component dù Child Component không thay đổi (chỉ Re-Evaluating, không Re-Rendering)

Sử dụng React.memo() để so sánh prop giữa các Evaluation của Component, nếu không có sự thay đổi Component sẽ không bị Re-Evaluating. Quá trình này cũng tiêu tốn tài nguyên nhất định. Không nên sử dụng trên tất cả Component mà chỉ sử dụng với một số "Key Component"
React.memo() so sánh (===) nên với các Reference Value, kết quả so sánh ở mỗi lần Re-Evaluating của Parent Component sẽ luôn trả về false (có thay đổi)

useCallback({}, []) - Ngăn chặn Re-Create Object giữa các Component Execution

dependencies của useCallBack() - Thiết lập Closure cho Function. Mỗi khi một giá trị bên ngoài (được sử dụng trong Function thay đổi), Re-Create Function đó

React chỉ tạo state mới ở lần đầu tiên Component được tạo. Sau đó React chỉ cập nhật state này mà không tạo state mới trừ khi Component bị removed khỏi DOM

State Update & Scheduling
Component - Current State => setState() => Scheduled State Change => New State => Re-evaluate Component (re-run Component Function) => Component
Nhiều cập nhật có thể được scheduled tại cùng một thời điểm!

State không được cập nhật ngay lập tức sau khi setState() được thực thi mà thay vào đó schedule một Scheduled State Change
Thứ tự của State Change cho cùng một State luôn được đảm bảo
State Update phụ thuộc vào cùng một State (Previous State Snapshot) => Nên sử dụng Function Form setState(prevState => newState) để cập nhật State dựa trên Previous State Snapshot (đảm bảo luôn sử dụng State mới nhất để cập nhật)
State Update phụ thuộc vào State khác => Sử dụng useEffect() với dependency là State cần cập nhật để cập nhật State (đảm bảo luôn sử dụng State mới nhất để cập nhật)
Cập nhật nhiều State trong cùng một Sync Code Snippet => React gộp thành một State Update => State Batching

useMemo(() => {
return ...
}, [dependency]) - Cho phép ghi nhớ (lưu trữ) bất kì Data nào
