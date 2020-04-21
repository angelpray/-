# 基本排版

1. 文本颜色，足够高的对比度确保网页阅读无障碍，但会过分强调，原则就是不要影响可读性
2. 字体组，备选字体列表，优先级从左到右，最后一个通常是作为`通用字体族`,一般指的是`serif`,`sans-serif`（无衬线），或者代码的等宽字体`monospace`
3. 基于比例缩放字体大小，`纯四度`数学原则，指的是**上一级标题是下一级标题的字型大小的1.333倍。
4. 设置行高`line-height`，单位设置成无单位的数字，则子元素继承的是一个系数。否则继承的是计算后的像素值。
5. 文本粗细：`400normal`，`700bold`.
6. 控制字母和单词间距：`letter-spacing`,`word-spacing`
7. 文本缩进:`text-indent`，对于相邻的段落，可以设置`p + p`设置相邻落进行缩进。
8. 文本水平排列：`text-align`,设置元素内容的水平对齐方式
9. 多列布局：`column-width`, `column-count`, `column-gap`,最少列宽，最少列数，列距离

# WEB字体

1. 字体格式，基本都支持标准的`WOFF`格式，部分支持`WOFF2`，如果确实需要支持老浏览器的话，需要补充字体格式，比如`SVG/EOT/TTF`
2. `@font-face`规则，通过它可以指定浏览器下载web字体的服务器地址。
3. 每个字体后缀对应的字体格式：woff/woff,woff2/woff2,eot/embedded-opentype,ttf/truetype,svg/svg
```css
/* 使用web字体 */
@font-face {
    font-family: "xxx";
    font-weight: normal;
    src: url("xxx.woff") format("woff"),
         url("xxx.woff2") format("woff2"),
         url("xxx.eot#ie") format("embedded-opentype");
         /* ttf truetype svg svg */
    font-style: normal;
}
```
4. font-family优先正确的粗细值，意思是，只要font-family正确匹配，无论粗细都会匹配。

## web字体性能

1. 浏览器需要下载额外的字体文件，会延长用户等待时间。

2. 如果是自己托管web字体，则要确保设置适当的缓存首部，避免不必要的网络开销。

3. 浏览器加载字体的问题：
   >1. 字体下载完成前暂缓显示文本，IE,SAFARI,CHROME都采用这种方式。FOIT(flash of invisible text)
   >2. 字体下载完成前，浏览器先用一种后备字体显示内容，避免网速慢的问题，但切换字体时会有闪动问题。 FOUT(flash of unstyle text)
4. 使用`web font loader`

# 文本特效

1. 文本阴影，`text-shadow: x y blur color(shadow 1), shadow2`