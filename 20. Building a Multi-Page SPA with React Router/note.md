Routing - URL thay đổi => Visible Content thay đổi
SPA - Chỉ cần một file HTML ban đầu, URL thay đổi => Visible Content thay đổi nhưng không fetch một file HTML mới

Với mỗi path, render những Component nhất định
<Route path="/path">...</Route>
<BrowserRouter><App /></BrowserRouter>

Thẻ <a> thông thường khi bị click sẽ gửi request để nhận file HTML mới => Page tải lại => Mất State

<Link to="/path">...</Link>

<NavLink activeClassName={...}>...</NavLink> - Thêm CSS Class cho active link với activeClassName

<Route path="/path/:param">...</Route> - Dynamic Route

const param = useParams() - param là một Object với key là Dynamic Segment trong URL dẫn tới Page đó

Mặc định, React Router sẽ hiển thị cùng lúc tất cả các Route match một path nào đó (match = bắt đầu bằng path đó)
<Switch>...</Switch> - Chỉ hiển thị Route đầu tiên (theo thứ tự được sắp xếp trong <Switch>) match path
<Switch><Route path="/path" exact>...</Route></Switch> - Route match toàn bộ path mới được hiển thị

Có thể thêm Route trong Component trong một Route khác (Nested Route). Nếu Component active, Route bên trong nó sẽ được evaluated và hiển thị Content nếu path match (Nested Path)

<Redirect to="/path"> - Thay đổi URL, chuyển hướng tới path trong to prop

<Route path="*">...</Route> - match mọi path => "Not Found" Page

Programmatic (Imperative) Navigation
const history = useHistory() - Thay đổi Browser History => Thay đổi URL
history.push("/path") - Thêm Page mới vào Browser History, điều hướng sang /path (có thể quay lại)
history.replace("/path") - Thay thế Page hiện tại bằng Page mới, điều hướng sang /path (không thể quay lại)

<Prompt when={} message={(location) => ...} /> - Tự động theo dõi nếu điều hướng sang path khác và nếu một điều kiện nào đó thỏa mãn, sẽ hiển thị một warning trước khi cho phép user rời
when={true/false} - Điều kiện để xác định có hiển thị Prompt nếu điều hướng sang path khác hay không
message - Nhận vào một Function return một string sẽ được hiển thị trên Prompt. location là Object chứa thông tin về Page sẽ điều hướng đến

Query Parameter - Tham số đặc biệt ở cuối URL, có dạng "?key=value&...", bổ sung thêm Data cho Page được hiển thị. Query Parameter là optional và không thay đổi việc match Route
const location = useLocation() - Lưu trữ thông tin về URL hiện tại và Page đang được hiển thị
const queryParam = new URLSearchParams(location.search) - Lấy ra Query Parameter dưới dạng Object
queryParam.get('key') - Lấy ra giá trị của value tương ứng với key trong Query Parameter Object

Có thể sử dụng Nested Route để hiển thị Content khác nhau

const match = useRouteMatch() - Lưu trữ thông tin về URL và một số Data khác
history.push({
pathname: ...,
search: ...
})
