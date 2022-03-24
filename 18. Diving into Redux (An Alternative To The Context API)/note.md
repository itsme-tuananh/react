Cách Redux hoạt động
Chỉ có một Central Data (State) Store cho tất cả App-Wide hay Cross-Component State
Component nhận Data mà nó cần từ Central Data Store thông qua Subscription
Component không trực tiếp thay đổi Data ở Central Data Store
Reducer Function thực hiện việc thay đổi Data ở Central Data Store
Component gửi đi một Action (bản chất là một Object mô tả tiến trình Reducer Function cần thực hiện), Action này được chuyển tới Reducer Function, Reducer Function thay đổi Data dựa theo yêu cầu từ Action

const store = redux.createStore() - Nhận vào một Reducer Function để thiết lập Store ban đầu và thay đổi Data
Reducer Function nhận vào State cũ và Action được gửi đến, trả về State mới (nên là Pure Function)
store.getState() - Lấy State mới nhất
store.subscribe() - Nhận vào Subcriber Function mà Redux sẽ thực thi mỗi khi Data trong Store thay đổi
reducer(state = ..., action) - Có thể thiết lập Default State cho Store
store.dispatch({action}) - Gửi đi một Action tới Reducer để thực thi một tiến trình nhất định

<Provider store={reduxStore}>...</Provider>

useSelector(state => state.aPartOfTheState) - Trả về một phần của State được quản lí trong Redux Store và tự động thiết lập Subscription cho Component sử dụng nó. Component luôn nhận được Data mới nhất và Data trong Store thay đổi, Component được Re-Evaluated

dispatchFn = useDispatch()
dispatchFn({action})

Với Class-based Component, sử dụng connect(mapStateToProps, mapDispatchToProps)(Component) (bản chất là map State và Dispatch Function vào Prop của Component)

Luôn return tất cả State khi cập nhật một State vì Redux overwrite State cũ bằng State mới chứ không merge State mới vào State cũ
Không bao giờ được trực tiếp thay đổi State gốc, luôn return một Object mới
Luôn copy và tạo các Nested Object và Nested Array mới
