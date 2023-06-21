# Extractring State Logic into a Reducer

Nhiều components update state từ nhiều event handler có thể làm bạn không thể quản lý được. Với case này bạn cần phải di chuyển tất cả các logic update state ra khỏi component và đưa vào một single function, nó gọi là  **reducer**

## Consolidate (củng cố) state logic with a reducer

Khi một component phát triển, số lượng state logic sẽ ở khắp mọi nơi. Để giảm sự phức tạp và giữ tất cả logic ở cùng một nơi để dễ dàng truy cập, bạn có thể di chuyển state logic vào trong một single function từ componnet của bạn, và gọi đó là **reducer**
**Reducer** là một cách khác để handle state. Bạn có thể migrate (di trú, di chuyển) từ `useState` thành `useReducer` với ba bước:

### Step 1: Move from setting state to dispatching actions

Thai thế **setting task** thông quan event handler, bằng `dispatch` action.
Object được pass vào `dispatch` được gọi là `action` object. Mỗi `action` object sẽ có `type` để trình bày *what happened*.

### Step 2: Write a reducer function

**Reducer function** là mnoiw bạn put state logic. Nó có *2 arguments* là **current state** và **action object**, và **return** về **next state**

Bởi vì **reducer function** có một argument là state, nên bạn có thể **khai báo nó bên ngoài component** để code dễ đọc hơn.

### Step 3: Us the reducer from your component

#### App.js
    import { useReducer } from 'react';
    import AddTask from './AddTask.js';
    import TaskList from './TaskList.js';
    import tasksReducer from './tasksReducer.js';

    export default function TaskApp() {
    const [tasks, dispatch] = useReducer(tasksReducer, initialTasks);
    const initialTasks = [
        {id: 0, text: 'Visit Kafka Museum', done: true},
        {id: 1, text: 'Watch a puppet show', done: false},
        {id: 2, text: 'Lennon Wall pic', done: false},
    ];
    let nextId = 3;

    const handleAddTask = text => {
        dispatch({
        type: 'added',
        id: nextId++,
        text: text,
        });
    }

    const handleChangeTask = task => {
        dispatch({
        type: 'changed',
        task: task,
        });
    }

    const handleDeleteTask = taskId => {
        dispatch({
        type: 'deleted',
        id: taskId,
        });
    }

    return (
        <>
        <h1>Prague itinerary</h1>
        <AddTask onAddTask={handleAddTask} />
        <TaskList
            tasks={tasks}
            onChangeTask={handleChangeTask}
            onDeleteTask={handleDeleteTask}
        />
        </>
    );
    }

#### TaskReducer.js
    export default function tasksReducer(tasks, action) {
        switch (action.type) {
            case 'added': {
            return [
                ...tasks,
                {
                id: action.id,
                text: action.text,
                done: false,
                },
            ];
            }
            case 'changed': {
            return tasks.map((t) => {
                if (t.id === action.task.id) {
                return action.task;
                } else {
                return t;
                }
            });
            }
            case 'deleted': {
            return tasks.filter((t) => t.id !== action.id);
            }
            default: {
            throw Error('Unknown action: ' + action.type);
            }
        }
    }


### Comparing `useState` and `useReducer`

[Link](https://react.dev/learn/extracting-state-logic-into-a-reducer#comparing-usestate-and-usereducer)

### Writing reducers well

Nhớ 2 tip khi viết **reducers**

- **Reducer must be pure**, giống như *state update functions*, reducers run during rendering (Actions are queued until the next render)
- **Each action describles a single user interaction, event if leads to multiple changes in the data**

### Writing concise reducers with Immer

[Link](https://react.dev/learn/extracting-state-logic-into-a-reducer#writing-concise-reducers-with-immer)


### Recap

- To convert from `useState` to `userReducer`:

    1. Dispatch actions from event handlers
    2. Write a reducer function that returns the next state for a given state and action
    3. Replace `useState` with `useReducer`

- Reducers yêu cầu bạn phải viết nhiều code hơn, nhưng sẽ giúp bạn trong debugging và testing
- Reducers bắt buộc là một **pure function**
- Mỗi action chỉ trình bày một user interaction
- Sử dụng **Immar** nếu bạn muốn thay đổi phong cách viết reducers