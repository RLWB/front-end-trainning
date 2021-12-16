### useCallback Hook

React `useCallback`Hook 返回一个记忆化的回调函数。

注意：将记忆化视为缓存一个值，这样它就不需要重新计算。

这使我们能够隔离资源密集型函数，以便它们不会在每次渲染时自动运行。

当依赖有更新的时候，才会执行`useCallback` Hook

这可以提高性能。

#### 用法

使用useCallback可以防止组件重新渲染，除非props发生变化。

以下例子，Todos组件不会重新渲染：

index.js:

```jsx
import { useState, useCallback } from "react";
import ReactDOM from "react-dom";
import Todos from "./Todos";

const App = () => {
  const [count, setCount] = useState(0);
  const [todos, setTodos] = useState([]);

  const increment = () => {
    setCount((c) => c + 1);
  };
  const addTodo = useCallback(() => {
    setTodos((t) => [...t, "New Todo"]);
  }, [todos]);

  return (
    <>
      <Todos todos={todos} addTodo={addTodo} />
      <hr />
      <div>
        Count: {count}
        <button onClick={increment}>+</button>
      </div>
    </>
  );
};

ReactDOM.render(<App />, document.getElementById('root'));
```

Todos.js:

```jsx
import { memo } from "react";

const Todos = ({ todos, addTodo }) => {
  console.log("child render");
  return (
    <>
      <h2>My Todos</h2>
      {todos.map((todo, index) => {
        return <p key={index}>{todo}</p>;
      })}
      <button onClick={addTodo}>Add Todo</button>
    </>
  );
};

export default memo(Todos);
```

现在`Todos`组件只会在`todos`prop 改变时重新渲染。

### useMemo Hook

`useMemo`Hook 返回一个记忆值。

注意：将记忆化视为缓存一个值，这样它就不需要重新计算。

当依赖更新的时候就会触发`useMemo` Hook

这可以提高性能.

注意：`useMemo`和`useCallback`Hooks 是相似的。主要区别在于`useMemo`返回一个记忆值并 `useCallback`返回一个记忆函数.

