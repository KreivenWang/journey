# 1. 什么是闭包，举例说明 如防抖/节流函数的实现
闭包是 JavaScript 中一个重要的概念，它指的是有权访问另一个函数作用域中的变量的函数。即使该函数已经执行完毕，其作用域内的变量也不会被销毁，而是会被闭包捕获并保留在内存中。闭包是 JavaScript 中的一个小帮手。它是一个函数，可以记住并访问另一个函数的作用域中的变量。即使原来的函数已经执行完毕，这些变量也不会被删除，而是会被闭包保存在内存中。

## 闭包的核心特点：

1. **访问外部函数变量**：闭包可以访问并修改外部函数的变量。
2. **变量值的持久化**：外部函数执行完毕后，其作用域内的变量会被闭包捕获，不会被垃圾回收机制销毁。
3. **私有变量和方法**：闭包可以用来实现私有变量和方法，避免全局污染。

### 防抖（Debounce）函数实现：
防抖函数的作用是在用户频繁触发事件时，只执行最后一次操作。例如，搜索框的实时搜索功能，用户连续输入时不触发搜索，只有停止输入一段时间后才触发。
```javascript
function debounce(func, delay) {
  let timer = null;
  return function() {
    const context = this;
    const args = arguments;
    clearTimeout(timer);
    timer = setTimeout(() => {
      func.apply(context, args);
    }, delay);
  };
}

// 使用示例
const searchInput = document.getElementById('search-input');
searchInput.addEventListener('input', debounce(function() {
  console.log('执行搜索:', this.value);
}, 300));
```

### 节流（Throttle）函数实现：
节流函数的作用是限制函数的执行频率，确保在一定时间内只执行一次。例如，滚动加载、按钮点击防误触等场景。

```javascript
function throttle(func, limit) {
  let inThrottle;
  return function() {
    const context = this;
    const args = arguments;
    if (!inThrottle) {
      func.apply(context, args);
      inThrottle = true;
      setTimeout(() => inThrottle = false, limit);
    }
  };
}

// 使用示例
window.addEventListener('scroll', throttle(function() {
  console.log('滚动事件触发');
}, 500));
```

# 2. 微任务和宏任务
在 JavaScript 事件循环中，宏任务（Macro Task）和微任务（Micro Task）的分类如下：
## 宏任务（Macro Task）
- `setTimeout`
- `setInterval`
- `setImmediate`（Node.js 环境）
- `I/O` 操作（如文件读写、网络请求）
- `UI 渲染`
- `script` 标签内的整体代码（初始执行的同步代码）

## 微任务（Micro Task）
- `Promise.then()`、`Promise.catch()`、`Promise.finally()`
- `async/await` 中 `await` 后面的代码（本质是 Promise 的语法糖）
- `process.nextTick`（Node.js 环境，优先级高于其他微任务）
- `queueMicrotask()`（浏览器环境，用于手动添加微任务）

执行顺序：**先执行同步代码，再清空微任务队列，最后执行一个宏任务并重复此流程**。

# 3. CORS
