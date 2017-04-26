# 订阅阅读器测试

##　技术架构

  jasmine.js

## 测试内容及思路

1. 编写测试， `allFeeds` 对象中的每条反馈执行循环操作， 并确保其具有定义的非空 URL。
   - 循环 `allFeeds` 使用`toBeDefined(`)和`not.toBeNull()`，判断源中的`url`和`name`都是被定义且不是空的。
2. 编写测试，对 `allFeeds` 对象中的每条反馈执行循环操作， 并确保其具有定义的非空名称。 
   - 循环 `allFeeds` 使用`toBeDefined()`和`not.toBeNull()`，判断源中的`url`和`name`都是被定义且不是空的。
3. 编写测试，确保菜单 (menu) 元素在默认情况下处于隐藏状态。 并要求分析 HTML 和 CSS，以确定 菜单元素的隐藏/显示是如何实现的。
   - 分析html、css，了解menu的隐藏是由`body`上的`class`控制的，获取body中的class的值，初始化时，获取的值是`menu-hidden`，即默认隐藏`menu`。
4. 编写测试，确保当点击菜单时， 菜单改变其可见性。测试应有两项期望：当点击时，菜单是否显示， 当再次点击时，菜单是否隐藏。
   - 触发菜单图标的点击事件，第一点击后，`body`的`class`值为空，即menu显示 。第二次点击后，`body`的`class`值为“`menu-hidden”`，即menu隐藏。
5. 编写测试，保在调用并执行 `loadFeed` 函数后， 在 `.feed` 容器中至少存在一个 `.entry` 元素。
   - `loadFeed()`是异步调用的，且有一个`callback`函数在所有内容完成后调用，所以结合`beforeEach`,`done`;在`callback`中调用`done`若`loadFeed` 函数被调用而且工作正常，则`feed` 容器元素里面至少有一个 `.entry` 的元素。获取`.entry` 元素数组的长度与0比较大小，大则成功。
6. 编写测试，确保每当 `loadFeed` 函数加载一条新反馈后， 内容会相应更改。
   - 根据上一个测试，将`loadFeed`调用两次，每次调用后，获取`.feed`中的html，两次html内容对比，不相等，即为成功

## 测试结果

   基本完成测试要求

## 测试改进

   异步测试，网络不好时，就会超时，不知道是否还有好的测试方法。