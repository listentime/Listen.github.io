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

## 插槽 slot

- 为什么使用插槽

  - 组件其实是对一整套代码的封装（html，css，js）我们现在封装的组件没有灵活性（组件名称标签中间的位置没有用了）插槽的目的就是为了弥补组件标签名称中间的位置

- 插槽的分类

  - 匿名插槽
  - 具名插槽
  - 作用域插槽

  ##       插槽的优点

  - 使封装变得更加灵活

  - 匿名插槽和具名插槽可以直接在父组件内提供一个数据直接显示在自足组件的内部

  - 作用域插槽的优点，就是可以让父子组件分别提供不一样的东西组成一个新的东西

  ## 插槽的使用

  ### 匿名插槽

  - <slot></slot> 标签就是一个插槽

  - 当你自己开始封装组件的时候，直接写在子组件的 template 模版里面的一个标签

  - 会自动吸取你写在组件名称标签对里面的内容

  - 一个匿名插槽可以吸取所有的内容

  - 一个组件的封装里面最好只是出现一个 匿名插槽（出现多个匿名插槽的时候是把所有的内容赋值了两份）

  - 在使用匿名插槽的时候，可以有一个默认值（就写在 slot 标签对里面）

  - 使用场景

    ```txt
    - 匿名插槽(不需要用户特殊填写内容)
       + 多用于封装一些简单的结构和样式使用(尽量不包含结构性质的东西)
       + el-button
       + el-tag
       + ...
    ```

    

  ```html
  <style>
      * {
        margin: 0;
        padding: 0;
      }
  
      .warning {
        background-color: yellow;
      }
  
      .error {
        background-color: red;
      }
  
      .success {
        background-color: green;
      }
  </style>
  <div id="app">
      <com-one>
      	我会被匿名插槽吸走
          <p>我也会被匿名插槽吸走</p>
      </com-one>
  </div>
  <script src="vue.js"></script>
  <script>
  	const comOne = {
      template:'
        <div>
          <h1>我是组件1</h1>
          <h2>
            <slot>我是一个匿名插槽的默认值（默认值会被覆盖）</slot>
          </h2>
        <el-button type="success">提交</el-button>
        <el-button type="error">取消</el-button>
        <el-button type="warning"></el-button>
        </div>'
    }   	
     const elButton = {
      template: `
        <button :class="type">
          <slot>按钮</slot>
        </button>
      `,
      props: ['type']
    }
    new Vue({
      el: '#app',
      data: {
        msg: 'hello Vue!',
        list: [
          1, 2, 3, 4, 5
        ]
      },
      methods: {},
      components: {
        comOne,
        elButton
      }
    })
  </script>
  ```

### 具名插槽

- <slot name="a"></slot>  这个标签就是一个叫做 a 的具名插槽

- 这个插槽会吸取你写在组件名称标签对里面一些 “特定” 的内容

-  “特定” 的内容就是一些指定了名字的标签

- 有一个叫做 slot 的属性，一个可以直接写在元素上的属性，专门用来指定这个元素的所属

- 剧名插槽可以和匿名插槽一起使用，他们互相没有干扰（匿名插槽值吸取非特定元素，具名插槽只吸取属于自己名称元素）

- 没有任何的位置限制

- 当多个插槽内容混在一起使用的时候是没有任何位置关系

- 多个具名插槽之间没有任何影响

- 具名插槽是没有默认值的

- 使用场景

  ```txt
   具名插槽（需要用户多家一个 slot 属性）
     + 多用于一些带有结构的封装的时候使用
     + el-card
     + el-table
     + ...
  ```

  

```html
<div id="app">
    <com-two>
      <!--
        当使用 slot 属性把它变成一个特定的元素以后
        那么就只有特殊的 slot 标签（也就是具名插槽） 可以吸收
        别的插槽不能吸收了
        这个有名字的 p 标签只能被一个叫做 a 的具名插槽吸收
      -->
      <p>{{ msg }}</p>
      <p slot="b"></p>
      <p slot="a">abcd</p>
      <p slot="a">abcd</p>
      <p>我是非特定元素</p>
    </com-two>
    <el-card>
      <h1 slot="title">我是一个标题</h1>
      <ul>
        <li v-for="(item, index) in list" :key="index">{{ item }}	</li>
      </ul>
    </el-card>
</div>
<script src="vue.js"></script>
<script>
  const comTwo = {
    template: /*html*/`
      <div>
        <h1>具名插槽</h1>
        <h2>
          <slot></slot>
        </h2>
        <h3>
          <slot name="a"></slot>
        </h3>
        <h3>
          <slot name="b">asdasdasd</slot>
        </h3>

      </div>
    `
  }
    const elCard = {
    template: `
      <div class="card">
        <header>
          <slot name="title"></slot>
        </header>
        <section>
          <slot></slot>
        </section>
      </div>
    `
  }
  new Vue({
    el: '#app',
    data: {
      msg: 'hello Vue!',
      list: [
        1, 2, 3, 4, 5
      ]
    },
    methods: {},
    components: {
      comTwo,
      elCard
    }
  })
</script>
```

### 作用域插槽

-  slot-scope=“scope” 这个东西叫做作用于插槽

- 自己本身不是一个标签

- 是和匿名插槽还是具名插槽混合使用的一个插槽

- 就是将子组件里面的内容拿到外面来使用

- 直接在子组件内的 slot 标签上动态绑定一个数据

- 使用场景

  ```txt
  + 父组件提供结构
  + 子组件提供数据
  + el-table
   = 自定义列内容的时候
   = 父组件内部提供了列内容的结构
   = 使用的数据是 el-column 这个子组件里面的数据（scope.row.xxx）
  ```

  ```html
  <div id="app">
      <com-three>
        <div slot-scope="scope">
          <!-- scope 是标签上的所有数据的集合 -->
          {{ scope.row }}
        </div>
      </com-three>
  </div>
  <script src="vue.js"></script>
  <script>
    const comThree = {
      template: `
        <div>
          <h1>作用域插槽</h1>
          <h2>
            <slot :row="msg"></slot>
          </h2>
        </div>
      `,
      data () {
        return {
          msg: '我是组件三'
        }
      }
    }
    new Vue({
      el: '#app',
      data: {
        msg: 'hello Vue!',
        list: [
          1, 2, 3, 4, 5
        ]
      },
      methods: {},
      components: {
        comTwo,
        elCard
      }
    })
  </script>
  ```

  