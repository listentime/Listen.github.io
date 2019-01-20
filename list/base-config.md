> webpack简单使用及配置

  1. 在项目目录中初始化项目

  ```javascript
  npm i
  ```
  2. 安装包 npm 

  ```javascript
  npm i webpack webpack-cli //webpack及脚手架
  npm i webpack-dev-server -D  //自动编译

  ```

  3. 打开package.json文件，添加dev节点

  ```javascript
  "scripts":{
    "test":"",
    "dev":"webpack"//以dev命名该脚本
    "dev":"webpack-dev-server"//如果安装了自动编译，则将dev改成此项
  }
  ```

  4. 创建webpack配置文件，webpack.config.js

  ```javascript
  module.exports = {
    mode: "development" //development(开发环境，代码不压缩)  production（生产模式，代码会被压缩）
  }
  ```

