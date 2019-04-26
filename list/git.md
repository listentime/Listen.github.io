## git基础配置

### 全局配置

```js
git config --global user.eamil "github邮箱"
git config --global user.name "github名称"
```

### 密钥生成

```js
现场演示
windows的密钥文件在user/.ssh //.开头的文件都属于隐藏文件
```



## git基本操作

### 创建本地仓库

```js
//方式一
git clone 远程仓库地址
//方式二
git init //初始化本地仓库
git remote add origin  远程仓库地址
```

### 本地代码推送至远程仓库

```js
在任何时候，push之前一定要pull
git add . //添加所有修改文件
git commit -m "说明" //提交代码至暂存取并说明本次提交

git push origin master //推送代码至主分支
```

### 拉取远程代码至本地

```js
//前提时本地没有仓库
git clone 远程仓库地址
//前提是本地已经有仓库
git pull origin master //拉去远程主分支代码至本地 origin 【分支指向】 master【主分支名称】
```

### 创建新的本地分支

### 当我们对master分支没有操作权限时

```js
//方法一
git branch 分支名称
//方法二 创建分支并切换到新的分支上 推荐使用
git checkout -b 分支名称


```



### 本地多分支之间切换

```js
git checkout 分支名
```



## 完整推送拉去演示

```js
现场演示
主分支在实际开发中是没有权限操作的
创建cjy线上分支
本地创建cjy分支并切换
开发完毕提交至cjy分支
线上操作合并分支//强调领导做的事
```

## 分支合并演示

```js
现场演示 基于无操作权限
创建开发分支dev
编辑提交代码
合并至cjy分支
```

## 冲突演示

```js
现场演示
```

