---
permalink: /css/flexbox/
toc: true
---

# flexbox

[Spec 笔记](https://ynotes.github.io/css-flexbox/)

CSS 2 布局模式：

- block
- inline
- table
- positioned

flexbox 是一种新的布局模式。

## terminology

![](https://drafts.csswg.org/css-flexbox/images/flex-direction-terms.svg)

flexbox 相关属性比较多，首先应分清属性是用于 flex container 还是 flex items。

## flex container

### display

```
display: flex | inline-flex
```

### flex-direction

```
Value: row | row-reverse | column | column-reverse
```

指定主轴方向。

初始值为 row，表示与书写方向一致。

### flex-wrap

```
Value: nowrap | wrap | wrap-reverse
```

是否可以换行。

初始值为 nowrap，表示不可换行。

### flex-flow

```
Value: <flex-direction> || <flex-wrap>
Initial: row nowrap
```

这是一个速记属性。

### justify-content

```
Value: flex-start | flex-end | center | space-between | space-around
```

![](https://drafts.csswg.org/css-flexbox/images/flex-pack.svg)

### align-items

```
Value: flex-start | flex-end | center | baseline | stretch
Initial: stretch
```

flex item 可以用 [align-items](#align-items) 覆盖这个属性。

![](https://drafts.csswg.org/css-flexbox/images/flex-align.svg)


### align-content

```
Value: flex-start | flex-end | center | space-between | space-around | stretch
Initial: stretch
```

只有当 flex container 多行时才有效果。

![](https://drafts.csswg.org/css-flexbox/images/align-content-example.svg)


## flex items

flex items

- float 忽略
- position: absolute | fixed，脱离常规流，不参与 flexbox 布局，不过可以用 order。
- margin: auto，在 justify-content, align-self 之前取走空余空间。

### flex

```
Value: none | [ <‘flex-grow’> <‘flex-shrink’>? || <‘flex-basis’> ]
Initial: 0 1 auto
```

这是一个速记属性。

property    | omitted | initial
----------  | :-----: | :-----:
flex-grow   | 1       | 0
flex-shrink | 1       | 1
flex-basis  | 0       | auto

keyword  | value    | description
-------  | -------- | ------------
initial  | 0 1 auto | 不能扩张但可以收缩
auto     | 1 1 auto | 可以扩张也可以收缩
none     | 0 0 auto | 不能扩张也不能收缩
n        | n 1 0    | n 是 `<positive-number>`


### flex-grow

```
Value: <number>
Initial: 0
```

### flex-shrink

```
Value: <number>
Initial: 1
```

### flex-basis

```
Value: content | <‘width’>
Initial: auto
```


### align-self

覆盖 flex container 的 [align-items](#align-items)。

### order

```
Value: <integer>
Initial: 0
```

指定 flex items 的排列次序。值小的排在前面，值一样的按文档的次序排列。

## 资料

- [flexbox bugs](http://philipwalton.com/articles/normalizing-cross-browser-flexbox-bugs/)