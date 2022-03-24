Side Effect - Tất cả những gì khác Render UI & React to User Input
Những task này thường xảy ra bên ngoài Component Function
useEffect(() => {...}, [ dependencies ]) - Function (chứa Side Effect code) chỉ được thực thi SAU mỗi Component Evaluation NẾU dependencies nhất định thay đổi

Những gì sử dụng trong Side Effect Function (có khả năng thay đổi) => Thêm vào dependencies
Một hành động được thực thi là phản hồi cho một hành động khác => Side Effect => useEffect()

Debouncing - Không thực thi Function sau mỗi keystroke mà chỉ khi User dừng một khoảng thời gian nhất định trong khi typing
return một Function trong useEffect() => Cleanup Function
Cleanup Function chạy trước mỗi lần thực thi Side Effect Function mới và trước khi Component bị removed. Không chạy trước lần thực thi Side Effect Function đầu tiên

useEffect() không có tham số thứ hai => Thực thi mỗi lần Component Function thực thi, sau mỗi Component Render Cycle (bao gồm cả lần đầu tiên Component được mounted)
useEffect() có tham số thứ hai là [] (không có dependencies) => Chỉ thực thi một lần duy nhất khi Component được mounted và rendered lần đầu tiên
useEffect() có dependencies => Thực thi bất cứ khi nào Component được re-evaluated và dependencies thay đổi
Cleanup Function => Thực thi trước mỗi lần thực thi Side Effect Function mới và trước khi Component bị removed. Không chạy trước lần thực thi Side Effect Function đầu tiên
Cleanup Function của useEffect() không có dependencies => Thực thi khi Component bị removed

useReducer() - Quản lí more complex State (khi có các state phụ thuộc vào nhau và/hoặc có các state update phụ thuộc vào state khác)

const [state, dispatchFn] = useReducer(reducerFn, initialState, initFn)
state - state snapshot được sử dụng trong Component re-render/re-evaluation cycle
dispatchFn - Một Function có thể được sử dụng để gửi đi một action mới
reducerFn(prevState, action) => newState - Một Function được triggered tự động mỗi khi một action được gửi đi (thông qua dispatchFn()). Nó nhận vào state snapshot mới nhất và trả về state mới, đã được update
initialState - state ban đầu
initFn - Một Function để set state ban đầu programmatically
reducerFn có thể nằm ngoài Component Function - Tất cả data được yêu cầu và sử dụng bên trong reducerFn sẽ được truyền vào tự động khi nó được thực thi bởi React
action có thể là bất cứ thứ gì: string, number,... nhưng thường là một object có field chứa identifier (thường field đó được đặt tên là type) và có thể chứa thêm extra payload

Tối ưu hóa useEffect() bằng việc xác định cụ thể một cách tối đa dependencies

Sử dụng useReducer() khi có state/data liên quan với nhau hoặc có state update phức tạp

Sử dụng React.createContext() để tạo Context Object, nhận vào Default Context, có thể là bất cứ thứ gì, nhưng thông thường là một Object
const Context = React.createContext({defaultContext}) là một Object chứa Context Component
<Context.Provider> là một Component bao quanh các Component sẽ cần Context chứa trong nó
<Context.Consumer> là một Component bao quanh các Component sẽ lấy data từ nó
<Context.Consumer>
{(context) => {
return (JSX Code (có thể sử dụng context.someProp))
}}
</Context.Consumer>
Default Context chỉ được sử dụng khi dùng Context mà không có <Context.Provider>
<Context.Provider value={{context}}>
Khi đã sử dụng Context có thể loại bỏ việc pass prop thông qua các Component trung gian không cần đến prop đó

const context = useContext(Context)

Nên sử dụng Context khi phải forward cái gì đó qua rất nhiều Component và forward tới một Component thực hiện một điều gì đó thật cụ thể

defaultContext nên có cấu trúc giống với context sẽ được sử dụng
Nên quản lí state và context trong cùng một file, mỗi Component chỉ nên có một nhiệm vụ chính

prop cho configuration, context cho quản lí state giữa các Component

Rules of Hooks
...

const Component = React.forwardRef((props, ref) => {
const insideData = 'insideData'

useImperativeHandle(ref, () => {
return {
outsideName: insideData
}
})
})
=> Expose Functionalities từ một Component tới Parent Component của nó để sau đó sử dụng Component đó trong Parent Component thông qua ref và kích hoạt Functionalities nhất định => Nhưng nên tránh sử dụng một cách tối đa
