## 过滤器

- 基本概念

  - 概念：本质是一个函数，可以用作常见的文本格式化

  - 过滤器并不能改变数据原有的值

  - 过滤器只能用在插值表达式和v-bind表达式中

  - 过滤器查找遵循就近原则，即先查找私有，在查找全局

- 用法实例
  - 全局过滤器
  ```javascript
  Vue.filter('过滤器名称'，function(过滤值,过滤形式){
    //TODO...
  })
  ```
  - 局部过滤器
  ```javascript
  new Vue({
    filters:{
      '过滤器名称':‘处理函数’
    }
  })
  ```
- 案例（时间过滤器）
  ```javascript
  Vue.filter('dateFormat',function(originVal,pattern){
    const dt = new Date(originVal)
    const y = dt.getFullYear()
    const m = dt.getMonth()+1
    const d = dt.getDate()
    if(pattern === 'yyyy-mm-dd'){
      return `${y}-${m}-${d}`
    }else{
      const hh = dt.getHours()
      const mm = dt.getMinutes()
      const ss = dt.getSeconds()
      return `${y}-${m}-${d} ${hh}:${mm}:${ss}`
    }
  })
  ```

## 生命周期
![logo](/asset/lifecycle.png)

## 操作dom

1. 给要操作得标签设置ref属性

2. 在mounted方法中（vue渲染完毕后，自动触发的方法） 获取要操作得dom

3. 通过this.$refs(是一个对象，含有声明的ref的值)获取要操作的dom

4. 示例
```javascript
let vm = new Vue({
  mounted(){
    this.$refs.ref值.//进行后续操作
  }
})
```
