## 内置对象
  
### Math

  > 常用方法

```javascript
//绝对值
Math.abs(num)

//向上取整
Math.ceil(num)

//向下取整
Math.floor(num)

//返回多个数字的最大值
Math.max(num)

//返回多个数字的最小值
Math.min(num)

//返回一个0-1的随机数
Math.random()

//四舍五入
Math.round(num)

//返回一个数的整数部分
Math.trunc(num)
```

### Date

  > Date起始于1970年1月1日

```javascript
//创建当前时间
 var dt = new Date()

//获取年
 var year = dt.getFullYear()

//获取月
 var month = dt.getMonth()+1

//获取日
 var day = dt.getDate()

//获取时
 var h = dt.getHours()

//获取分
 var m = dt.getMinutes()

//获取秒
 var s = dt.getSeconds()
```

### Array

  > 常用方法

```javascript
//返回数组的长度
arr.length

//返回一个截取的数组
arr.slice(2,4)

//对数组进行排序
arr.sort()

// 数组反转
arr.reverse()

//判断数组类型
Array.isArray(arr)

//等效于arr instanceof Array

//判断数组中是否包含这个值
arr.includes(5)

//如果存在,则返回第一个元素的下标,否则返回-1
arr.indexOf(5)

//如果存在,则返回最后一个元素的下标,否则返回-1
lastIndexOf(5)
```

> 数组遍历

```javascript
//循环遍历
arr.forEach( x => console.log(x) )

//对数组进行遍历测试,通过返回true,否则false
arr.every( x => x>0 )

//对数组进行遍历测试,通过返回false,否则true
arr.some( x => x>0 )

//过滤数组,通过则返回当前元素
arr.filter( x => x>5 )

//找到数组中满足条件,的第一个元素的值
arr.find( x => x>5 )

//满足条件,则返回第一个元素的下标,否则返回0
arr.findIndex( x => x>5 )

//对每一个元素调用函数并返回新数组
arr.map( x => x+1 )

//对所有元素求和
arr.reduce( (x,y) => x+y )
//也可以拼接字符串
arr.reduce( (x,y) => x+","+y )
```

> 数组操作

```javascript
//删除数组中最后一个元素,并返回该元素
arr.pop()

//删除数组中第一个元素,并返回该元素
arr.shift()

//将指定元素添加到数组的开头
arr.unshift()

//将元素追加到数组的最后
arr.push()

// 从索引为2的位置删除一项
arr.splice(2, 1)

// 在索引为2的位置插入10
arr.splice(2, 0, 10)

// 从索引为2的位置删除一项再插入10
arr.splice(2, 1, 10)

//把若干参数合并为数组
Array.of(1,2,3)

//合并两个数组并返回
arr1.concat(arr2)

//把字符串拆分成伪数组
Array.from("string")

//让数组以指定字符拼接
arr.join("-")

//把数组转换成字符串
arr.toString()

//可以转换时间,数字,字符串
arr.toLocaleString()
```

### String

  > 查找获取

```javascript
// 获取字符串的长度
'hello'.length

// 获取指定索引的字符
'hello'.charAt(3)

// 获取指定字符首次出现的索引
'hello'.indexOf('l')

// 获取指定字符最后出现的索引
'hello'.lastIndexOf('l')

// 查找指定字符出现的位置
'hello'.search('l')
```

  > 截取字符串

```javascript
// 截取指定索引字符串
'hello'.slice(0, -3)

// 截取指定长度的字符串
'hello'.substr(1, 3)

// 截取指定索引字符串
'hello'.substring(1, 3)
```

  > 替换转换

```javascript
// 对指定字符串进行替换
'hello'.replace('l', 'o')

// 把字符串分割成数组
'hello word'.split(' ')

// 大写转换小写
'HELLO'.toLowerCase()

// 小写转换大写
'hello'.toUpperCase()

// 大写转换小写(根据地区)
'HELLO'.toLocaleLowerCase()

// 小写转换大写(根据地区)
'hello'.toLocaleUpperCase()

// 把指定索引的字母转换成编码
'hello'.codePointAt(0)

// 把编码转换成字母
String.fromCodePoint(65)
```

  > 拼接填充

```javascript
// 拼接字符串
'hello'.concat('wo', 'rd')

// 以指定长度在后面进行重复填充
'hello'.padEnd(10, '-')

// 以指定长度在前面进行重复填充
'hello'.padStart(10, '-')

// 将字符串重复整数次
'hello'.repeat(2)
```

  > 判断

```javascript
  // 判断是否包含指定字符
'hello'.includes('ll')

// 判断是否已指定字符开头
'hello'.startsWith('he')

// 判断是否以指定字符结尾
'hello'.endsWith('lo')
```

  > 截取

```javascript
// 去除两边空格
'hello'.trim()

// 去除左边空格
'hello'.trimLeft()

// 去除右边空格
'hello'.trimRight()
```

### RegExp

#### 如何实例

  > First

```javascript
/*
* 第一个参数为`正则表达式`
* 第二个参数为`修饰符`
*/

// 正则表达式写在注释符号中
var reg = new RegExp(/\bis\b/, 'g')

// 也可以写在字符串中
var reg = new RegExp('\\bis\\b', 'g')
```

  > Second

```javascript
// 也同样写在注释符号中
var reg = /\bis\b/

// 修饰符直接写在最后即可
var reg = /\bis\b/g
```

#### 如何使用

  > test方法

```javascript
var reg = /\bis\b/
// 返回类型为 boolean 值, true表示通过验证
reg.test('she is a girl, he is a boy')
```

  > exec方法

```javascript
var reg = /([1]+)([2]+)([3]+)/
// 返回值是一个数组
var res = reg.exec('112233')
// 可以得到匹配出来的结果
console.log(res)
```

#### 修饰符

  - g 全文匹配
  - i 忽略大小写
  - m 多行匹配

#### 元字符

  - \d 匹配任意一个数字 等同于[0-9]
  - \D 匹配任意一个非数字
  - \s 匹配任意一个空格
  - \S 匹配任意一个非空
  - \w 匹配任意一个非特殊符号 等同于[0-9a-zA-Z] _属于非特殊符号
  - \W 匹配任意一个特殊符号

  - [] 匹配中括号范围内的一个

```javascript
  // 匹配任意一个数字
/[0-9]/

// 匹配任意一个字母
/[a-zA-Z]]/

// 匹配.jpg
/[.]jpg/
```
  - | 表示或者

```javascript
// 匹配任意数字或字母中的一个
/[0-9]|[a-zA-Z]/
```
  - () 提升优先级或者分组
  
```javascript
// 匹配 10-20 之间的数字
/(1[0-9])|[2][0]/
```
  - ^ 表示以什么开始

```javascript
// 匹配以数字开头
/^[0-9]/

// 匹配非数字
/[^0-9]/
```
  - $ 表示以什么结尾

```javascript
// 匹配以数字结尾
/[0-9]$/
```