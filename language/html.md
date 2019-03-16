# html编码风格规范

## DOCTYPE声明
html文件第一行必须是
``` html
<!DOCTYPE html>
```
细节可以去看[W3C相关约定](https://www.w3.org/TR/2014/REC-html5-20141028/syntax.html#the-doctype)

## 语言
这个属性视情况而定，此属性意义在于告诉浏览器本html页面内容所用的语言，表现之一是， 内容为中文但是声明为 `en`， 浏览器可能会提示你要不要翻译改页面而不管真的需不需要翻译
``` html
<html lang="zh-CN">
```

## charset
使用 `UTF-8`， 不要使用其他写法比如 `utf8` 等。
``` html
<meta charset="UTF-8">
```

## 标签闭合
- 标签不要省略其闭合标签  
  

``` html
<!-- 不推荐写法 -->
<p>this is an element

<!-- 推荐写法 -->
<p>this is an element</p>
```
- 自闭的标签不写 `/`  
  
``` html
<!-- 不推荐写法 -->
<br />

<!-- 推荐写法 -->
<br>
```

## 标签嵌套
一般建议存在标签嵌套就换行，如果有内部标签内容很少，写在单行不超过60个字符的(非硬性标准)，可以考虑单行写完。主要衡量标准是一眼看得完，不用去拖动IDE的滚动条(那些IDE编辑器特别宽的请放弃思考务必换行)。

## 表格
一个要求
- table下记得使用thead 和 tbody

## 注释
- 注释务必单行不要内联
- 注释前后留空格
- 注释内部不要有连续的`-`
``` html
<!-- my comment -->
```

- 模块注释  
模块开始： `<!-- S Module Name -->`  
模块结束： `<!-- E Module Name -->`  
模块注释之间留一空行  

``` html
<!-- S Comment Text A -->
<div>
    ...
</div>
<!-- E Comment Text A -->

<!-- S Comment Text B -->	
<div>
    ...
</div>
```


## 文件模板
如果有了正式的种子项目，这些就不用太在意了  
移动端  
  
``` html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, shrink-to-fit=no" >
<meta name="format-detection" content="telephone=no" >
<title>移动端HTML模版</title>
</head>
<body>

</body>
</html>
```
PC端  
  
``` html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="keywords" content="your keywords">
<meta name="description" content="your description">
<meta name="author" content="author,email address">
<meta name="robots" content="index,follow">
<meta http-equiv="X-UA-Compatible" content="IE=Edge,chrome=1">
<meta name="renderer" content="ie-stand">
<title>PC端HTML模版</title>
</head>
<body>

</body>
</html>
```



## 其他
这些约定我感觉不是特别重要，属于那种个人认为遵循了挺好但是自己又懒得其执行的。有不同意见可以一起讨论修正。
- 标签的语义： 比如文本内容就使用`p`, `article`, `hx`等标签，而不要全部 `div` 了事。

