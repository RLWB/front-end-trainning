## React是什么

React 是一个用于构建用户界面的 JavaScript 库，是 Facebook 创建的。[官网](https://reactjs.org/)

<img src="assets/image-20211214213805744.png" alt="image-20211214213805744" style="zoom: 50%;" />

## React历史

React.JS 的当前版本是 V17.0.2（2021 年 12月）。

2013 年 7 月首次向公众发布 (V0.3.0)。

React.JS 于 2011 年首次用于 Facebook 的 Newsfeed 功能。

Facebook 软件工程师 Jordan Walke 创建了它。

当前版本`create-react-app`为 v5.0.0（2021 年 12 月）。

`create-react-app` 包括 webpack、Babel 和 ESLint 等构建工具。



## React的特点

* 声明式

  以声明式编写 UI，可以让你的代码更加可靠，且方便调试。

* 组件化

  构建管理自身状态的封装组件，然后对其组合以构成复杂的 UI。

  由于组件逻辑使用 JavaScript 编写而非模板，因此你可以轻松地在应用中传递数据，并保持状态与 DOM 分离。

* 一次学习，跨平台编写

  无论你现在使用什么技术栈，在无需重写现有代码的前提下，通过引入 React 来开发新功能。

  React 还可以使用 Node 进行服务器渲染，或使用 [React Native](https://reactnative.dev/) 开发原生移动应用。

## React安装

开始学习 React 的最快方法是直接在 HTML 文件中编写 React。

首先包含三个脚本，前两个让我们在 JavaScript 中编写 React 代码，第三个 Babel 允许我们在旧浏览器中编写 JSX 语法和 ES6。

* 通过cdn在线引入

```js
<script crossorigin src="https://unpkg.com/react@17/umd/react.development.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
<script src="https://unpkg.com/@babel/standalone/babel.js"></script>
```

​	上述版本仅用于开发环境，不适合用于生产环境。压缩优化后可用于生产的 React 版本可通过如下方式引用：

```js
<script crossorigin src="https://unpkg.com/react@17/umd/react.production.min.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@17/umd/react-dom.production.min.js"></script>
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
```

* 通过npm使用react

  需要结合browserify 或 webpack模块化构建工具，自行配置开发环境

* 使用creat-react-app快速构建react开发环境

  create-react-app 是来自于 Facebook，通过该命令我们无需配置就能快速构建 React 开发环境。

  create-react-app 自动创建的项目是基于 Webpack + ES6 。

  执行以下命令创建项目：

  ```shell
  npx create-react-app my-app
  cd my-app
  npm start
  ```

  **注意：** 如果您之前已`create-react-app`全局安装，建议卸载该软件包以确保 npx 始终使用最新版本的 `create-react-app`. 要卸载，运行此命令：`npm uninstall -g create-react-app`。

  在浏览器中打开 **http://localhost:3000/** ，结果如下图所示：

  <img src="assets/image-20211214230753560.png" alt="image-20211214230753560" style="zoom:50%;" />

  项目目录结构如下：

  <img src="assets/image-20211214230834432.png" alt="image-20211214230834432" style="zoom:50%;" />



## 渲染html

React 通过使用` ReactDOM.render()`在网页中渲染html，该`ReactDOM.render()`函数接受两个参数，HTML 代码和一个 HTML 元素。该函数的目的是在指定的 HTML 元素内显示指定的 HTML 代码。页面最终渲染在`public`文件夹里的`index.html`内。

## JSX语法

React 使用 JSX （JavaScript XML）来替代常规的 JavaScript。JSX 是一个看起来很像 XML 的 JavaScript 语法扩展。

我们不需要一定使用 JSX，但它有以下优点：

- JSX 执行更快，因为它在编译为 JavaScript 代码后进行了优化。
- 它是类型安全的，在编译过程中就能发现错误。
- 使用 JSX 编写模板更加简单快速。

```jsx
const element = <h1>Hello, world!</h1>;
```

这种看起来可能有些奇怪的标签语法既不是字符串也不是 HTML。

它被称为 JSX， 一种 JavaScript 的语法扩展。 我们推荐在 React 中使用 JSX 来描述用户界面。

JSX 是在 JavaScript 内部实现的。

我们知道元素是构成 React 应用的最小单位，JSX 就是用来声明 React 当中的元素。

与浏览器的 DOM 元素不同，React 当中的元素事实上是普通的对象，React DOM 可以确保 浏览器 DOM 的数据内容与 React 元素保持一致。

要将 React 元素渲染到根 DOM 节点中，我们通过把它们都传递给 ReactDOM.render() 的方法来将其渲染到页面上：

```jsx
var app = <div className="foo" />; 
ReactDOM.render(app, document.getElementById('example'));
```

*注意:*

*由于 JSX 就是 JavaScript，一些标识符像* `class` *和* `for` *不建议作为 XML 属性名。作为替代，React DOM 使用* `className` *和* `htmlFor` *来做对应的属性。*

### js表达式

我们可以在 JSX 中使用 JavaScript 表达式。表达式写在花括号 **{}** 中。实例如下：

```jsx
ReactDOM.render(
    <div>
      <h1>{1+1}</h1>
    </div>
    ,
    document.getElementById('example')
);
```

React 支持`if`语句，但*在*JSX 中不支持。

为了能够在 JSX 中使用条件语句，应该将这些`if` 语句放在 JSX 之外，或者可以使用三元表达式：

也可以写三元运算符

```jsx
ReactDOM.render(
    <div>
      <h1>{i == 1 ? 'True!' : 'False'}</h1>
    </div>
    ,
    document.getElementById('example')
);
```

### 顶级元素

代码块必须包含在一个顶级元素中，所以如果你想写*两个*段落，你必须把它们放在一个父元素中，就像一个`div`元素。

```jsx
const myelement = (
  <div>
    <p>I am a paragraph.</p>
    <p>I am a paragraph too.</p>
  </div>
);
```

*如果 HTML 不正确，或者 HTML 缺少父元素，JSX 将抛出错误。*

或者，您可以使用`Fragment`来包装多行。这将防止不必要地向 DOM 添加额外的节点。

片段看起来像一个空的 HTML 标签：`<></>`。

```jsx
const myelement = (
  <>
    <p>I am a paragraph.</p>
    <p>I am a paragraph too.</p>
  </>
);
```

或者

```jsx
const myelement = (
  <Fragment>
    <p>I am a paragraph.</p>
    <p>I am a paragraph too.</p>
  <Fragment/>
);
```



### 元素必须闭合

JSX 遵循 XML 规则，因此必须正确关闭 HTML 元素。

### 样式

React 推荐使用内联样式。我们可以使用 **camelCase** 语法来设置内联样式. React 会在指定元素数字后自动添加 **px** 。以下实例演示了为 **h1** 元素添加 **myStyle** 内联样式：

```jsx
var myStyle = {
    fontSize: 100,
    color: '#FF0000'
};
ReactDOM.render(
    <h1 style = {myStyle}>Hello world!</h1>,
    document.getElementById('example')
);		
```

### 使用className代替类名class

由于JSX是JavaScript，`class`关键字在js中是保留字，你不能再JSX中使用`class`，该用属性`className`。

JSX 通过使用`className`来解决这个问题。当 JSX 被渲染时，它`className` 会将属性转换为`class`属性。

### 数组

JSX 允许在模板中插入数组，数组会自动展开所有成员：

```jsx
var arr = [
  <h1>Hello</h1>,
  <h2>World!</h2>,
];
ReactDOM.render(
  <div>{arr}</div>,
  document.getElementById('example')
);
```

## React组件

在react中，组件就像返回的html元素的函数。

组件有两种类型，Class组件和Function组件。

*注意：*

*在较旧的 React 代码库中，你可能会发现主要使用 Class 组件。现在官方建议将 Function 组件与 Hooks 一起使用，Hooks 是在 React 16.8 中添加的。*

### class类组件

类组件必须包含该`extends React.Component`语句。该语句创建了对 React.Component 的继承，并使您的组件可以访问 React.Component 的函数。

该组件还需要一个`render()`方法，该方法返回 HTML。

```jsx
class Car extends React.Component {
  render() {
    return <h2>Hi, I am a Car!</h2>;
  }
}
```

### function组件

Function 组件也返回 HTML，其行为方式与 Class 组件大致相同，但 Function 组件可以使用更少的代码编写，更易于理解。

```jsx
function Car() {
  return <h2>Hi, I am a Car!</h2>;
}
```

### 渲染组件

现在你的 React 应用程序有一个名为 Car 的组件，它返回一个 `<h2>`元素。

要在您的应用程序中使用此组件，请使用与普通 HTML 类似的语法： `<Car />`

```jsx
ReactDOM.render(<Car />, document.getElementById('root'));
```

### Props

组件通过`props`传递属性，`props`作为函数参数，发送到组件中。

```jsx
function Car(props) {
  return <h2>I am a {props.color} Car!</h2>;
}

ReactDOM.render(<Car color="red"/>, document.getElementById('root'));
```

### 组件嵌套组件

我们可以在其他组件内部引用组件：

```jsx
function Car() {
  return <h2>I am a Car!</h2>;
}

function Garage() {
  return (
    <>
      <h1>Who lives in my Garage?</h1>
      <Car />
    </>
  );
}

ReactDOM.render(<Garage />, document.getElementById('root'));
```

### 文件组件

建议将组件拆分为单独的文件。为此，可以创建一个`.js`文件。将代码放入其中，通过 `export`	导出：

`Car.js`

```jsx
function Car() {
  return <h2>Hi, I am a Car!</h2>;
}

export default Car;
```

为了能够使用 Car 组件，您必须导入该文件。

```jsx
import React from 'react';
import ReactDOM from 'react-dom';
import Car from './Car.js';

ReactDOM.render(<Car />, document.getElementById('root'));
```



## 事件

就像 HTML DOM 事件一样，React 可以根据用户事件执行操作。

React 具有与 HTML 相同的事件：`click`、`input`、`mouseover`等。

### 添加事件

React 事件是用驼峰式语法编写的：

`onClick` 而不是`onclick`.

React 事件处理函数写在花括号内：

`onClick={shoot}` 而不是 `onClick="shoot()"`.

*React*

```jsx
<button onClick={shoot}>Take the Shot!</button>
```

*HTML*

```html
<button onclick="shoot()">Take the Shot!</button>
```

`组件中`

```jsx
function Football() {
  const shoot = () => {
    alert("Great Shot!");
  }

  return (
    <button onClick={shoot}>Take the shot!</button>
  );
}

ReactDOM.render(<Football />, document.getElementById('root'));
```

### 传递参数

要将参数传递给事件处理程序，请使用箭头函数。

```jsx
function Football() {
  const shoot = (a) => {
    alert(a);
  }

  return (
    <button onClick={() => shoot("Goal!")}>Take the shot!</button>
  );
}

ReactDOM.render(<Football />, document.getElementById('root'));
```

### 事件对象

事件处理函数可以访问触发函数的 React 事件。

```jsx
function Football() {
  const shoot = (a, b) => {
    alert(b.type);
    /*
    'b' represents the React event that triggered the function,
    in this case the 'click' event
    */
  }

  return (
    <button onClick={(event) => shoot("Goal!", event)}>Take the shot!</button>
  );
}

ReactDOM.render(<Football />, document.getElementById('root'));
```

## 条件渲染

在 React 中，您可以有条件地渲染组件。

有几种方法可以做到这一点。

### if语句

我们可以使用`if`JavaScript 运算符来决定渲染哪个组件。

```jsx
function Goal(props) {
  const isGoal = props.isGoal;
  if (isGoal) {
    return <MadeGoal/>;
  }
  return <MissedGoal/>;
}

ReactDOM.render(
  <Goal isGoal={false} />,
  document.getElementById('root')
);
```

### 逻辑`&&`运算符

另一种有条件地渲染 React 组件的方法是使用`&&`运算符。

```jsx
function Garage(props) {
  const cars = props.cars;
  return (
    <>
      <h1>Garage</h1>
      {cars.length > 0 &&
        <h2>
          You have {cars.length} cars in your garage.
        </h2>
      }
    </>
  );
}

const cars = ['Ford', 'BMW', 'Audi'];
ReactDOM.render(
  <Garage cars={cars} />,
  document.getElementById('root')
);
```

如果`cars.length` 等于真，则后面的表达式`&&`将呈现。

### 三元运算符

另一种有条件地呈现元素的方法是使用三元运算符。

```jsx
function Goal(props) {
  const isGoal = props.isGoal;
  return (
    <>
      { isGoal ? <MadeGoal/> : <MissedGoal/> }
    </>
  );
}

ReactDOM.render(
  <Goal isGoal={false} />,
  document.getElementById('root')
);
```



## Lists列表

------

在 React 中，您将使用循环渲染列表。

JavaScript`map()`数组方法通常是首选方法。

```jsx
function Car(props) {
  return <li>I am a { props.brand }</li>;
}

function Garage() {
  const cars = ['Ford', 'BMW', 'Audi'];
  return (
    <>
      <h1>Who lives in my garage?</h1>
      <ul>
        {cars.map((car) => <Car brand={car} />)}
      </ul>
    </>
  );
}

ReactDOM.render(<Garage />, document.getElementById('root'));
```

### key

类似于vue里面的列表循环，react的列表每一项也得需要绑定key，确保key值是项目唯一的字段，可以保证列表高效的更新。



```jsx
function Car(props) {
  return <li>I am a { props.brand }</li>;
}

function Garage() {
  const cars = [
    {id: 1, brand: 'Ford'},
    {id: 2, brand: 'BMW'},
    {id: 3, brand: 'Audi'}
  ];
  return (
    <>
      <h1>Who lives in my garage?</h1>
      <ul>
        {cars.map((car) => <Car key={car.id} brand={car.brand} />)}
      </ul>
    </>
  );
}

ReactDOM.render(<Garage />, document.getElementById('root'));
```