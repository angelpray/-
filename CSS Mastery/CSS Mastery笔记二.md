# 选择符

## 元素选择符

1. 通配选择符 `*`

2. 类型选择符 `E`

3. ID选择符 `#id`

4. 类选择符 `.class`

## 关系选择符

1. 后代选择符 `E F`，选择所有符合条件的后代，包括儿子，孙子，孙子的孙子。与与子选择符`E > F`不同。

2. 子选择符 `E > F`，选择他的直接子元素，不会选择孙辈。

3. 相邻选择符 `E + F`，选择紧贴在E元素之后的一个F元素，元素E和F必须同属一个父级。

4. 兄弟选择符 `E ~ F`，选择E元素后面的所有兄弟元素F，元素E和F必须同属一个父级，与相邻选择符`E + F`不同。

## 属性选择符

1. `E[att]`

2. `E[att='val']`

3. `E[att~='val']`，选择具有att属性且值为用空格分隔的字词列表，其中一个等于val的E元素。（包含了只有一个值且该值等于val的情况）

4. `E[att^='val']`，选择具有att属性且以val开头的字符串的E元素。

5. `E[att$='val']`，选择具有att属性且以val结尾的字符串的E元素

6. `E[att*='val']`，选择具有att属性且字符串包含val的E元素

7. `E[att|='val']`，选择具有att属性，并且值为val或者val-的E元素

## 伪类选择符

- 伪类选择符的语法是一个以一个冒号开头，用于选择元素的特定状态或关系。

### 超链接伪类

- `:link,:visited,:hover,:focus,:active`

### 结构化伪类

- `:nth-child(n)`
- `:nth-last-child(n)`
- `:first-child`
- `:last-child`
- `:only-child`
- `:nth-of-type(n)`
- `:nth-last-of-type(n)`
- `:first-of-type`
- `:last-of-type`
- `:only-of-type`

### 表单伪类

- `E:checked`，处于选择状态的元素E，用于input type为radio与checkBox时。
- `E:enabled`，处于可用状态的元素E。
- `E:disabled`，处于不可用状态的元素E。

### 其他伪类

- `E:target`，匹配相关URL指向的E元素。也就URL后面跟着的锚点#，指向文档内的某个具体元素。锚点#与id绑定。


## 伪元素选择符

- 区别于伪类选择符，使用的是双冒号语法
- `::first-letter`
- `::first-line`
- `::before`
- `::after`
- `::placeholder`
- `::selection`

# 层叠

- 层叠机制为CSS规则赋予了不同的重要程度。
- 重要性程度从高到低：标注为!important的作者样式，作者样式，用户样式，浏览器默认样式。
- 在此基础上，规则再按选择符的特殊性进行排序。

# 特殊性

- 规则的特殊性越高，则优先级越高。

- 规则的特殊性对应a,b,c,d四个级别：行内样式a，ID选择符的数目为b，类选择符\伪类选择\属性选择符为c，类型选择符\伪元素选择符的数目为d。（a,b,c,d对应于十进制0,0,0,0）

# 继承

- 继承不同于层叠，继承是有些父级属性会被他们的后代所继承。
- 通用选择符会覆盖继承的属性

# 应用样式的方式

## link和style

- style，直接放在head部分
- link元素，rel属性为stylesheet
- @import url("/c/modules.css")
- 使用link或者style在HTML中添加多个样式表或者样式块时，他们的声明次序就是他们在HTML源码中出现的次序。

## 性能

- 度量web性能的一个重要指标就是网页内容实际显示在屏幕上需要多久。【渲染时间】

- 让浏览器渲染内容就需要先加载HTML和CSS，那么让浏览器最快下载HTML和全部CSS很重要。

1. 减少HTTP请求，因为每一个文件都需要发送一个HTTP请求，很浪费时间。

2. 压缩很缓存内容，压缩CSS，设置CSS文件缓存时间。

3. 避免JS阻塞浏览器，一种方法是script标签放到body最后位置，另一种是使用script的async和defer属性。async和defer都是异步加载，但前者下载后就会立即执行，后者则在HTML解析后执行。（async经常出错，建议用defer）

