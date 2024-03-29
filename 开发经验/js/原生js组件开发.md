# 原生js组件开发

## why 原生js？

复用及其简单，只需在需要使用的场景引入一个js文件即可。

这个js文件负责渲染dom节点+处理交互逻辑。

## 如何进行原生js开发

html：只是做测试用。让元素能够渲染出来。

js：负责所有的渲染和逻辑。

css：处理元素的样式。

### 示例

```js
// 创建 chatbox 的函数
function createChatBox() {
  // 创建 chatbox div
  var chatBox = document.createElement('div');
  chatBox.id = 'chatBox';
  chatBox.style.width = '300px';
  chatBox.style.height = '400px';
  chatBox.style.border = '1px solid black';
  chatBox.style.overflow = 'auto';
  
  // 创建 input 元素
  var input = document.createElement('input');
  input.id = 'chatInput';
  input.type = 'text';
  input.style.width = '300px';
  
  // 创建发送按钮
  var button = document.createElement('button');
  button.id = 'sendButton';
  button.innerText = '发送';

  // 将 input 和 button 添加到 chatbox 中
  chatBox.appendChild(input);
  chatBox.appendChild(button);

  // 将 chatbox 添加到页面中
  document.body.appendChild(chatBox);

  // 给按钮添加点击事件，将输入的文本添加到 chatbox 中
  button.addEventListener('click', function() {
    var text = input.value;
    if (text) {
      var message = document.createElement('p');
      message.innerText = text;
      chatBox.appendChild(message);
      input.value = '';
      chatBox.scrollTop = chatBox.scrollHeight;
    }
  });
}

// 调用函数创建 chatbox
createChatBox();

```

### 常用函数

#### 获取dom元素

```js
var element = document.getElementById("myElementId"); // 根据ID获取元素

var elements = document.getElementsByClassName("myClassName"); // 根据类名获取元素

var elements = document.getElementsByTagName("myTagName"); // 根据标签名获取元素

var element = document.querySelector(".myClassName"); // 使用CSS选择器获取第一个匹配的元素

var elements = document.querySelectorAll(".myClassName"); // 使用CSS选择器获取所有匹配的元素
```

#### 添加dom元素

```js
var newElement = document.createElement("div"); // 创建一个新的div元素

newElement.innerHTML = "Hello, world!"; // 设置新元素的内容

document.body.appendChild(newElement); // 将新元素添加到body中

var parentElement = document.getElementById("parentElement");
parentElement.insertBefore(newElement, parentElement.firstChild); // 在指定元素前插入新元素
```

#### 事件处理

```js
var button = document.getElementById("myButton");

// 使用addEventListener添加事件
button.addEventListener("click", function() {
  alert("Button was clicked!");
});

// 直接在元素的on事件属性上设置处理函数
button.onclick = function() {
  alert("Button was clicked!");
};
```

对DOM的操作可能会影响性能，因此应尽量减少不必要的DOM操作，并使用优化的方法，例如使用`documentFragment`进行批量操作，使用`addEventListener`代替直接设置on事件属性等。







