---
title: 使用css小记
---

#### 触摸屏当中的元素滚动

如果你需要在触摸屏当中为一些元素设置内滚动，那么你不仅需要 `overflow: scroll / auto` ，还需要 `-webkit-overflow-scrolling: touch`;

```css
.class {
  overflow: auto;
  -webkit-overflow-scrolling: touch;
}
```

#### 移动端页面布局（头部，底部固定，中间由内容撑搞）

可使用 `flex` 布局，尽量不用 `position: fixed`，因为再有动画的时候，会有各种意想不到的 `bug` ，慎用。

```css
.box {
  display: flex;
  flex-direction: column;
}
/* 固高 */
.box-item-height {
  height: xxxrem;
}
/* 撑满剩余的 */
.box-item-overflow {
  flex: 1;
  overflow: auto;
  -webkit-overflow-scrolling: touch;
}
```

#### 隐藏滚动条

有时滚动并不想出现滚动条，可以使用 `-webkit-scrollbar` 实现

```css
::-webkit-scrollbar {
  display: none;
}
```

#### 关于 input placeholder 有时顶部对齐的情况

`input placeholder` 在不同的机器中表现的并不一致（华为机器特别明显），我的解决的方式是：

```css
input::-webkit-input-placeholder {
  line-height: 30px;
}
/* 使用webkit内核的浏览器 */
input:-moz-placeholder {
  line-height: 30px;
}
/* Firefox版本4-18 */
input::-moz-placeholder {
  line-height: 30px;
}
/* Firefox版本19+ */
input:-ms-input-placeholder {
  line-height: 30px;
}
```

#### 文本溢出问题

单行文本溢出处理

```css
.class {
  overflow: hidden;
  white-wrap: nowrap;
  text-overflow: ellipsis;
}
```

多行文本溢出处理

```css
.class {
  overflow: hidden;
  word-break: break-all;
  text-overflow: ellipsis;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 4; //4表示第四行溢出，换成2就是只显示两行，并且第二行显示溢出的三个点点
}
```

#### 禁止用户选中文本

使用 `user-select`

```css
.class {
  user-select: none;
}
```

#### 清除手机 tap 事件后 element 时候出现的一个高亮

```css
* {
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
}
```

#### 使用 CSS `transforms` 或者 `animations` 时可能会有页面闪烁的 bug

```css
.class {
  -webkit-backface-visibility: hidden;
}
```

#### -webkit-touch-callout 禁止长按链接与图片弹出菜单

```css
.class {
  -webkit-touch-callout: none;
}
```

#### 使用硬件加速

有时候动画可能会导致用户的电脑卡顿，你可以在特定元素中使用硬件加速来避免这个问题：

```css
.class {
  transform: translateZ(0);
}
```

后续更新......
