# base-css

完整版在 master 分支维护, 首页优化精简在 mini 分支维护

`git checkout mini`

## USAGE

为保持主流浏览器体积最小, 拆分 IE6-8 为独立版本(`base.ie.css`)

```
<!-- for IE6-8 -->
<!--[if lt IE 9]>
    <link rel="stylesheet" href="base.css">
<![endif]-->
<!--[if gte IE 9]><!-->
    <link rel="stylesheet" href="base.ie.css">
<!--<![endif]-->
```

## BUILD & OUTPUT

`npm i && grunt`

最终产出在 dist 目录, 分为 4 份文件

base.rtl.css

base.ltr.css

base.ie.rtl.css

base.ie.ltr.css

## COMPACT DETAIL

### 1. 不常用的 form 控件 reset

```
input[type="search"] {
    -webkit-appearance: textfield;
    -webkit-box-sizing: content-box;
    -moz-box-sizing: content-box;
    box-sizing: content-box;
}

input[type="search"]::-webkit-search-decoration,input[type="search"]::-webkit-search-cancel-button {
    -webkit-appearance: none;
}
```

### 2. html5 标签兼容

```
audio,canvas,video {
    display: inline-block;
    *display: inline;
    *zoom: 1;
}

audio:not([controls]) {
    display: none;
    height: 0;
}
```

### 3. 过旧的样式属性兼容

```
.unselect,i,.i,.icon {
    -moz-user-select: -moz-none;
    -khtml-user-select: none;
    -webkit-user-select: none;
    -o-user-select: none;
    user-select: none;
}
```

### 4. IE Hack

```
_zoom:expression(function(el) {
    document.execCommand('BackgroundImageCache',false,true);el.style.zoom = "1";
}(this));
```

### 5. kill jQuery-UI

待定, 依赖自定义网址重构

### 6. 不常用的工具类

```
sup,.sup {
    top: -0.5em;
}

sub,.sub {
    bottom: -0.25em;
}
```

### 7. 冗余代码

```
@charset "utf-8";
...
@charset "utf-8";
```

## TEST

`/test/index.html`