# useReducer

`useReducer` là một React Hook  dùng để add a **redcer** vào component của bạn.

    const [state, dispatch] = useReducer(reducer, initialArg, init?)

## Reference

### useReducer(reducer, initialArg, init?)

Call `useReducer` tại top level của component của bạn để quản lý các state

#### Parameters

- `reducer`: Là một function đặc biệt dùng để update state. Nó bắt buộc là một **pure function**, nó có hai arguments là **state** và **action**, và sẽ reuturn **next state**.
- `initialArg`: Giá trị init state được dùng để calculated. Init state được dùng để calculate và phụ thuộc vào `init` argument.
- **optional** `init`: Là một initial function return về một initial state, inital state được set vào `initialArg`. Nói cách khác inital state là set kết quả của gọi `init(initalArg)`

#### Returns

`useReducer` returns môt array với chính xác 2 giá trị:

1. Current state. Trong lần first reder, nó sẽ set vào `init(initalArg)` hoăc `initalArg` nếu nó không có `init`
2. **Dispatch function** sẽ update giá trị mới cho state và **trigger** một re-render.

#### Caveats

- `useReducer` là một Hook nên bạn chỉ có thể gọi **at the top level of your component** hoặc **your own Hooks**. Bạn không thể gọi trong loop hoặc condition. Nếu cần, bạn buộc phải tạo new component và move state vào trong nó.
- In Strict Mode, React sẽ **call your reducer and initializer twice**, hành động này chỉ có trên development và không có trên production.

### `dispatch` function

`dispatch` là function trong `useReducer` được dùng để update giá trị mới cho state và trigger một re-render. Bạn cần pass hành động (action) duy nhất vào trong `dispatch` function.

React sẽ set và return next state, khi gọi `reducer` function bạn cần cung cấp **current state** và **action** để passed vào `dispatch`

#### Parameters

- `action`: Một hành động để xử lý từ user. Nó có giá trị của bất kỳ kiểu nào. Nhưng để tiện lợi, `action` thường là một object được định nghĩa một `type` property và các lựa chọn thêm properties khác.

#### Returns

`dispatch` function không có giá trị trả về.

#### Caveats

- `dispatch` function **only updates the state variable for the *next render***.
- Nếu giá trị cung cấp là một current state, được xác định bằng `Object.is` comparison, React sẽ **skip re-rendering the component and its children** (optimization).
- React **batches state update**