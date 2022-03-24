Reducer buộc phải là Pure, Side-Effect Free, Synchronous Function
Side-Effect và Async Task được thực thi trong Component hoặc Action Creator

Frontend Code dựa vào Backend Code

Không bao giờ trực tiếp thay đổi Redux State gốc, đặc biệt bên ngoài Reducer Function
Fat Reducer vs Fat Component vs Fat Action
Synchronous, Side-Effect Free Code => Ưu tiên Reducer, tránh Action Creator hoặc Component
Asynchronous, Side-Effect Code => Ưu tiên Action Creator hoặc Component, không bao giờ sử dụng Reducer

"Thunk" - Một Function delay một hành động cho đến sau này => Một Action Creator Function KHÔNG return chính bản thân action mà return một Function khác - thứ mà cuối cùng sẽ return action
Redux khi sử dụng Redux Toolkit chấp nhận Dispatch Function nhận vào Action Creator return Function. Nếu dispatch một action bản chất là một Function, Redux sẽ thực thi Function đó => Có thể dùng một Function return một Function khác làm một action
