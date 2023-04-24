
---
date: 2023-04-23T02:14:08+08:00
description: '跟著線上教學學習React'
# featured_image: "/images/Pope-Edouard-de-Beaumont-1844.jpg"
featured_image: '/images/code.jpeg'
# images: ['/images/Golang.png']
tags: ['React']
categories: 'React'
title: '學習React'
comment: true
---

> 跟著影片學習 React，之前買了課程一直沒有上課，最近無聊回來看一下課程，順便紀錄一下，以下附上課程連結。
[Epic React | ](https://youtu.be/yyUHQIec83I)

其實 useState 是用 useReducer 函數寫出來，下面會列出一些 useReducer 不常見的用法，最後才是介紹中最標準的用法。

## useReducer用法一: 直接傳入最新值

拿計數器的範例來當例子，原本使用 useState，現在我們改成useReducer。
useReducer後面要帶上兩個參數:

```js
const [state, newState] = useState(initialState);
const [reducer, dispatch] = useReducer(reducerFunction, initialState);
```

第一個是一個 **Ruducer函數**，這個Reducer函數會去處理 React 的資料。

```js
function reducerFunction(state, action)
```
Reducer 函數會有兩個參數，第一個參數會是畫面 State 更新前當下 State 的值，
React 已經處理好我們可以直接拿到，而第二個參數則是讓使用者傳入
（透過 useReducer 回傳後陣列內的第二個值(index=1)的函數呼叫時傳入)，
通常我們會稱作 action ，這個 action 可以以是數值（純值、物件），也可以是函數。

第二個參數則是放入 **初始值** 也就是原本 useState 中傳入的參數。
而會傳的陣列，陣列內的第一個元素是state，也就是當前的資料的數值，第二個函數是去
呼叫我們傳入 useReducer 內的第一個參數函數，通常我們會稱這個回傳的函數是 dispatch 函數。
可以在呼叫 dispatch 函數時傳入一個參數，而這個傳入的參數就會變成 Reducer函數的第二個參數 (action)。


```jsx
import * as React from 'react'

function countReducer(state, newValue) {
    return newValue
}

function Counter({ initialCount = 0, step = 1 }) {
  const [state, setState] = React.useReducer(countReducer, initialCount)

  const increment = () => setState(state + step)

  return <button onClick={increment}>{count}</button>
}

function App() {
  return <Counter />
}

export default App
```
上面的範例是直接將當下的資料去加上計數的結果直接帶入返回的 dispatch 函數中（在這裡是 setState) ，可以知道呼叫 dispatch函數
其實是執行 countReducer 函數，並且把 dispatch 傳入的參數當成 Reducer 的第二個參數的值。接著 Reducer 返回的值將會更新畫面。
