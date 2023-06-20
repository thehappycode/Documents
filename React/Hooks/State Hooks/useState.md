# useState

`useState` là một React Hook dùng để thêm một **state variable** vào component của bạn.

    const [state, setState] = useState(initialState);

## Reference

### `useState(initialState)`

    useState(initialState)

Khai báo `useState` ở vị trí trên cùng trong component của bạn.

#### Parameters

- `initialState`: Giá trị được khởi tạo, nó có thể nhận bất kỳ kiểu dữ liệu nào, nhưng nếu nó là một function thì bắt buộc là một **pure function**, React sẽ initial function khi initial component và store kết quả trả về khi inital state.

#### Returns

Trả về một array gồm 2 giá trị:

1. Current state
2. **set function** dùng để update state và **trigger** một re-render

### Caveats

- `useState` chỉ gọi *at the top level of your component*. Bạn không thể gọi `useState` trong **loops or conditions**. Nếu bạn muốn goi trong  **loops or conditions** thì hãy tạo mới một new component và di chuyển state vào trong nó.
- Trong *Strict Mode*, React sẽ **call your initializer function twice**. Hành động này chỉ xảy ra trên *development* và không có trên *production*. Nếu bạn *initializer function is pure* thì sẽ không có hành động này.

### `set` function, like `setSomething(nextState)`

`set` functions sẽ trả về `useState` đã được update một giá trị mới cho state và trigger a re-render. Bạn có thể pass một next state hoặc một function.

    const [name, setName] = useState('Edward');

    const handleClick() => {
        setName('Taylor');
        setAge(a => a + 1);
        // TODO ...
    }

#### Parameters

- `nextState`: là giá trị của next state. Nó có kiểu bất kỳ, hoặc một **special behavior of functions**

    - Nếu `netxtState` là một function, React đưa function vào một **queue** và re-render component. Trong quá trình re-render, React sẽ calculate next state trong **queue** từ previous state

#### Returns

`set` function không return giá trị.

### Caveats

- `set` function **chỉ update giá trị của biến state trong lần next render**.
- React **batches state updates**. Nó sẽ update screen **sau tắt cả các event handler đã chạy xong**. Trong quá trình update nextState không thay đổi trạng thái cho đến khi next render. Khắc phục bằng cách sử dụng nextState là một function (không khuyến khích dùng)