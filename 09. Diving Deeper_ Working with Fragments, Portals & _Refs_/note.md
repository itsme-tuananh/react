Không thể return hay lưu trữ trong biến nhiều hơn một Root JSX Element => Wrap tất cả Adjacent Element trong một Element duy nhất hoặc sử dụng một Array của các JSX Element => "<div> Soup"

Tạo Wrapper Component - Component chỉ return props.children => Built-in Wrapper Component: <React.Fragment></React.Fragment> hoặc <></> (tùy project setup, <React.Fragment> luôn hoạt động)

Một số HTML Element có thể hoạt động dù về mặt Semantic, "clean HTML structure", không phải là lý tưởng (modal, side-drawer, other dialogs,...) => React Portal: Sắp xếp React Component theo ý muốn nhưng vẫn đảm bảo cấu trúc HTML lý tưởng (Di chuyển HTML Content của Component sang vị trí khác trong rendered DOM)
Cần tạo một nơi để "port" Component đến (thường là một <div> Element) và sử dụng React.createPortal(<Component onSth={props.onSth} />, document.getElementById('someId'))

React Hook chỉ sử dụng được trong Functional Component
ref tham chiếu tới HTML Element được render ở actual DOM
Để thiết lập ref, import useRef, tạo const sthRef = useRef() và tại Element muốn tham chiếu thêm prop ref={sthRef}. ref chứa một Object với thuộc tính current chứa một real DOM Node
Không nên tác động tới DOM Node qua ref (tuy nhiên một vài trường hợp có thể cân nhắc)

Controlled Component - Internal State được quản lí bởi React
Uncontrolled Component - Internal State không được quản lí bởi React (sử dụng ref để tương tác với DOM Element, cụ thể là <input />)
