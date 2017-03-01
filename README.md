# Git

## 什么是Git?
  - Git是一款源代码管理工具(版本控制工具)
    - 我们写的代码需要使用Git进行管理。
  - 源代码有必要管理起吗？
  - 1.0
  - 2.0 //
  - svn,vss,vcs.... git
  - 有必要，因为人工的去处理不同的版本，做相应备份会很麻烦。
  - Git是linux之父当年为了维护linux---linus之前也是手动维护合并把文件发给Linus
  - linus自己写了一个版本管理的工具(Git)

## Git安装

## 初始化Git仓储/(仓库)
- 这个仓库会存放，git对我们项目代码进行备份的文件
- 在项目目录右键打开 git bash
- 命令: `git init`


## 自报家门
- 就是在git中设置当前使用的用户是谁
- 每一次备份都会把当前备份者的信息存储起来
- 命令:
    + 配置用户名:`git config --global user.name "xiaoming"`
    + 配置邮箱:  `git config --global user.email "xm@sina.com"`


## 把大象放到冰箱要几步
1. 打开冰箱门
2. 放大象
3. 关上冰箱

## 把代码存储到.git仓储中
- 1.把代码放到仓储的门口
    + `git add ./readme.md` 所指定的文件放到大门口
    + `git add ./` 把所有的修改的文件添加到大门口
- 2.把仓储门口的代码放到里面的房间中去
    + `git commit -m "这是对这次添加的东西的说明" `

## 可以一次性把我们修改的代码放到房间里(版本库)
- `git commit --all -m "一些说明"`
    + --all 表示是把所有修改的文件提交到版本库

## 查看当前的状态
- 可以用来查看当前代码有没有被放到仓储中去
- 命令: `git status`

## git中的忽略文件
- .gitignore,在这个文件中可以设置要被忽略的文件或者目录。
- 被忽略的文件不会被提交仓储里去.
- 在.gitignore中可以书写要被忽略的文件的路径，以/开头，
    一行写一个路径，这些路径所对应的文件都会被忽略，
    不会被提交到仓储中
    + 写法
        * ` /.idea  ` 会忽略.idea文件
        * ` /js`      会忽略js目录里的所有文件
        * ` /js/*.js` 会忽略js目录下所有js文件

## 查看日志
- `git log` 查看历史提交的日志
- `git log --oneline` 可以看到简洁版的日志

## 回退到指定的版本
- `git reset --hard Head~0`
    + 表示回退到上一次代码提交时的状态
- `git reset --hard Head~1`
    + 表示回退到上上次代码提交时的状态

- `git reset --hard [版本号]`
    + 可以通过版本号精确的回退到某一次提交时的状态

- `git reflog`
  + 可以看到每一次切换版本的记录:可以看到所有提交的版本号

## 分支
- 默认是有一个主分支master

### 创建分支
- `git branch dev`
    + 创建了一个dev分支
    + 在刚创建时dev分支里的东西和master分支里的东西是一样的

### 切换分支
- `git checkout dev`
    + 切换到指定的分支,这里的切换到名为dev的分支
    `git branch` 可以查看当前有哪些分支


### 合并分支
- `git merge dev`
    + 合并分支内容,把当前分支与指定的分支(dev),进行合并
    + 当前分支指的是`git branch`命令输出的前面有*号的分支
- 合并时如果有冲突，需要手动去处理，处理后还需要再提交一次.

### GitHub
- https://github.com
- 不是git,只是一个网站
- 只不过这个网站提供了允许别通过git上传代码的功能

### 提交代码到github(当作git服务器来用)
- `git push [地址] master`
 + 示例: `git push https://github.com/huoqishi/test112.git master  master`
 + 会把当前分支的内容上传到远程的master分支上

- `git pull [地址] master`
 + 示例: `git pull https://github.com/huoqishi/test112.git master`
 + 会把远程分支的数据得到:(*注意本地-要初始一个仓储!*)

- `git clone [地址]`
 + 会得到远程仓储相同的数据,如果多次执行会覆盖本地内容。


 # 流行框架

## ssh方式上传代码
- 公钥 私钥,两者之间是有关联的。
- 生成公钥,和私钥
    + `ssh-keygen -t rsa -C "xiaoming@sina.com"`

## 在push和pull操作进
- 先pull , 再push

- 当我们在push时，加上-u参数，那么在下一次push时
  我们只需要写上`git push`就能上传我们的代码。(加上-u之后，git会把
  当前分支与远程的指定的分支进行关联。git push origin master)

## npm
- node package manager
- 管理项目的依赖包
- 可以用来下载我们需要使用的东西
- 安装后可以通过`npm -v` 查看版本

### npm 使用
- 1.初始化操作
    + `npm init` 会生成一个package.json文件
- 2.下载所需要的包
    + `npm install jquery`  下载jquery
    + 会去 registry.npmjs.org 这个地址下载jquery
    + 会生成一个node_modules目录，下载的内容就放在这个目录

- 3.下载包时，可以加上 `--save` 参数
    + `npm install jquery --save`, 下载之后会在package.json中添加
    当前下载的包的版本信息。

## gulp
[官网](http://www.gulpjs.com)
[中文网](http://www.gulpjs.com.cn)

- 前端自动化构建工具
- js: function(){//},代码压缩,混淆 : var name = 123,var x = 123
- css,
- 合并: 1个js 1kb ,有10个js.

### 5个核心方法
 - gulp.task('任务名',function(){}) // 创建任务。
 - gulp.src('./*.css') 指定想要处理的文件
 - gulp.dest() // 指定最终处理后的文件的存放路径
 - gulp.watch() // 自动的监视文件的变化，然后执行相应任务。
 - gulp.run('任务名')，直接执行相应的任务。


### 安装gulp
- 通过npm安装:`npm install gulp-cli -g`

### gulp使用
- 1.在当前项目中也要安装gulp: `npm install gulp --save`
- 2.还需要在当前项目中新建一个文件: gulpfile.js

```javascript
    var gulp =  require('gulp');

    // 创建任务
    // 第一个参数: 任务名
    // 第二个参数: 回调函数,当我们执行任务时就会执行这个函数
    gulp.task('test', function(){
      console.log(123)
})
```
- 3.执行任务: `gulp 任务名`
    + 示例: `gulp test`

### 对js进行压缩
- `npm install gulp-uglify --save`

### 对js进行合并操作
- `npm install gulp-concat --save`

```javascript
    gulp.task('script', function(){
  // 1.要匹配到要处理的文件
  // 指定指定的文件:参数是匹配的规则
  // 参数也可以是数组，数组中的元素就是匹配的规则
  gulp.src(['./app.js','./sign.js'])
  // concat 的参数是合并之后的文件名字
  .pipe(concat('index.js'))
  .pipe(uglify())
  // dest方法参数，指定输出文件的路径
  .pipe(gulp.dest('./dist'))
})
```

### 对css进行压缩操作
- `npm install gulp-cssnano --save`

```javascript
   // 新建一个任务，对css进行处理
gulp.task('style', function(){
  // 对项目中的2个css文件进行合并，压缩操作
  // 1.匹配到要处理的文件
  gulp.src(['./*.css'])
  // 2.合并文件
  .pipe(concat('index.css'))
  // 3.压缩操作
  .pipe(cssnano())
  // 4.输出到指定目录
  .pipe(gulp.dest('./dist'))
  })
```

### 对html进行压缩
- `npm install gulp-htmlmin --save`
- https://github.com/kangax/html-minifier

```javascript
    // 新建一个任务，对html进行压缩
gulp.task('html', function(){
 // 1.匹配到要处理的文件
 gulp.src(['./index.html'])
 // 2.压缩操作
 .pipe(htmlmin({collapseWhitespace:true}))
 // 3.指定输出目录
 .pipe(gulp.dest('./dist'))
})
```

### gulp.watch
- 监视文件的变化，然后执行相应的任务
- gulp.run, 直接执行指定的任务

```javascript
    // gulp.watch 监视文件变化，执行相应任务
  gulp.task('mywatch', function(){
  // 执行指定的任务
  gulp.run('script')
  // 1.监视js文件的变化，然后执行script任务
  // 第一个参数：要监视的文件的规则
  // 第二个参数：是要执行的任务
  gulp.watch(['./app.js','sign.js'],['script'])
})
```


# Angular

## Angular 与 jQuery
- jQuery: 库
    + 提供了一些已有的方法，我们主动调用它。
    + $('.test').val()

- Angular: 框架
    + 框架提供了一种结构或者模式
    + 我们按照它提供这种结构或者模式去书写代码
    + 框架会帮助我们去剩下的事情

### Angular简介
- 一款非常优秀的前端高级 JS 框架
- 最早由 Misko Hevery 等人创建
- 2009 年被 Google 公式收购，用于其多款产品
- 目前有一个全职的开发团队继续开发和维护这个库
- 有了这一类框架就可以轻松构建 SPA 应用程序
- 其核心就是通过指令扩展了 HTML，通过表达式绑定数据到 HTML。

#### 什么是 SPA
- single page application
- 单页应用程序

### 值+1

### 指令
- 在angular中以ng-开头的html标签属性，称之为指令
- ng-app: 选择angular去管理哪一部分的html代码, 管理的是ng-app所在
   元素的子元素及其本身
- ng-click: 也是用来注册点击事件
- ng-model: 可以指定一个属性值，这个属性就表示当前文本框的value值
- ng-init: 可以对数据进行初始化操作，给一个默认值。

### 模块
- 创建模块:`var app = angular.module('模块名',[])`
- *注意* 如果不依赖其他模块，也需要提供一个空的数组
- 需要在ng-app指令的属性值上写我们的模块名(房子)

### 控制器
- 创建控制器:`app.controller('控制器的名字',function($scope){})`
- 如果要改变页面{{testName}}的值，就直接改变$scope.testName值就可以
- *注意* 要显示数据模型的值,就要在它所在标签或者父标签上加上ng-controller指令
  ng-controller的值就是我们想要显示的数据模型所在控制器的名字
  :ng-controller="window"

### 双向数据绑定
- 数据模型($scope.属性)的改变，会影响内容的显示(文本框的值)
- 我们改变了文本框的值，对应的数据模型发生了改变.
- 这种相互影响的关系就称之为双向数据绑定.

### MVC 思想
- M : Model: 存储，获取数据
- V : View 视图，把数据呈现给用户
- C : Controller 做一些控制和调度的操作


# Angular

## Angular vs jQuery
- 提高了dom操作的效率
- 不推崇dom操作

- angular.element, 使用方式和jquery非常像,jqLite对象
    + 可以把angular.element当作jQuery的$来用，
    + 注意*angular.element 要求传入的参数是一个原生的dom对象，而不是选择器*

### 回顾并总结Angular开发流程
- 1.在html中引入angular.js文件
- 2.在html中加上ng-app指令，告诉angular要管理页面哪一部分代码
- 3.在js中创建模块`angular.module('myApp',[])`,给ng-app指令一个值，
- 这个值就是这个模块的模块名:myApp
- 4.在js中创建控制器`xxx.controller('控制器名字',function($scope){})`,我们需要在页面上加上ng-controller指令，指令的值为控制器的名字
  `ng-controller="控制器名字"`
- 5.建模:根据页面结构，抽象出具体的js对象.
- 6.通过$scope做一些初始化操作`$scope.username="小明"`
- 7.通过`ng-model , ng-click , {{}}` 把$scope的属性在页面展示出来
- 8.在js写一些具体的逻辑

### MVC
- MVC只是一种思想，只是约定了我们代码应该如何去组织
- 让我们代码的每一部分都有一个明确的职责
- 用利于后期的维护性(并不是提高了代码的执行性能,有可能10行代码放到10个方法里,
- 10方法再放到10文件去.)


### $scope

- 视图和控制器之间的数据桥梁
- 用于在视图和控制器之间传递数据
- 用来暴露数据模型（数据，行为）

![$scope](./scope.png)

### ViewModel

- $scope 实际上就是MVVM中所谓的VM（视图模型）
- 正是因为$scope在Angular中大量使用甚至盖过了C（控制器）的概念，所以很多人（包括我）把Angular称之为MVVM框架
- 这一点倒是无所谓，具体看怎么用罢了

## Angular 模块
- angular.module('模块名',[])

### Angular中模块的划分方式
- 1.按照项目的功能去划分模块
- 2.按照项目中文件的类型去划分模块

## Angular 控制器
### 传统的方式创建控制器

```javascript
    // 创建控制器(1.2.x版本)
    // angular会把全局的函数当作控制器
    function demoController($scope){
      $scope.name = '小明'
    }

    function xxx($scope){
      $scope.age = 18
    }
```

### 面向对象的方式创建控制器
```html
<!-- 这里的obj 代表控制器中回调函数new 出的对象 -->
<div ng-controller="demoController as obj">
  <p>{{myname}}</p>
  <p>{{obj.name}}</p>
</div>
```
```javascript
    // 1.创建模块
    var app = angular.module('myApp', [])

    // 2.创建控制器
    // angular会把这二个参数当作构造函数使用
    app.controller('demoController', function($scope){
      $scope.myname='小红'
      this.name = '小明'
    })
```

### 安全的方式创建控制器
- 就是为了避免压缩后代码无法运行

```javascript
    // 把第二个参数改为一个数组,在数组把我们需要的参数的名字写上
    // 回调函数就写在数组的最后一个元素上
    // *注意*：数据中传入的元素的顺序,要和function的中顺序一一对应
    app.controller('demoController',['$scope','$log',function($scope,$log){
      $scope.msg = 'hello World!'
      $log.log('哈哈哈哈！')
    }])
```

## 指令

### ng-bind
- 可以解决表达式闪烁问题:
- `<p ng-bind="msg"> </p>` 浏览器不会把标签的属性显示出来!
- 效果：angular会把ng-bind对应的数据显示到所在标签中间

### ng-cloak
- 可以解决表达闪烁问题:
- `<div class="ng-cloak"><p>{{msg}}</p></div>` 先隐藏后显示
- angular在解析表达式之后会把页面上的ng-cloak样式移除,
     这样ng-cloak对应的样式就不生效了,我们就先给ng-cloak设置display:none;

### ng-repeat
- 能够把一组数据直接渲染到页面上，不需要我们拼接字符串
- 我们希望重复的是哪个元素就把ng-repeat指令加在哪个元素上，不一定是li上
- ng-repeat="item in users" , item对应是遍历users时的第一条数据，users是我们
- 要遍历的数据(是一个数组)

```html
    <!-- ng-repeat 遍历生成数据，类似for in 循环的语法 -->
      <li ng-repeat="item in users" >
        {{item.name}} , {{item.age}}
      </li>
```

#### ng-repeat补充
- ng-repeat 在遍历时会提供以下值:
    + $odd : 为true时，表明当前数据是否是第[奇]数条
    + $even: 为true时，表明当前数据是否是第[偶]数条
    + $first: 为true时，表明当前数据是否是第1条
    + $last: 为true时，表明当前数据是否是最后一条
    + $middle: 为true时，表明当前数据是否是中间的数据

```html
    <!--  $odd, ng-repeat在每次遍历时都提供这样的值，为true表明当前数据是否第奇数条,从索引为0开始判断的 -->
    <!--  $even, ng-repeat在每次遍历时都提供这样的值，为true表明当前数据是否第偶数条,从索引为0开始判断的 -->
      <li class="{{ $odd ?'red':'green'}}" ng-repeat="item in data">
        {{item.name}},{{item.age}}
      </li>
```

### ng-class
- ng-class 可以帮助我们控制元素的class样式，
- ng-class 可以独立在其他元素上使用，并非一定要和ng-repeat结合

```html
    <!--  ng-class,动态的添加class样式,
      以对象的形式书写，angular会把属性值为true的属性名当作样式添加到class
      class="green" -->
    <li ng-class="{red:item.age>=20, green:item.age>=10&&item.age<20,blue:item.age<10}" ng-repeat="item in data">
      {{item.name}},{{item.age}}
    </li>
```

### ng-show/ng-hide
- 控制元素的显示与否,ng-show与ng-hide作用是相反的(只是设置display:none来隐藏元素)

```html
    <!-- ng-show,控制元素的显示或隐藏,值为true时显示，为false隐藏-->
    <p ng-show="isShowing">我是中国人，我爱自己的祖国!</p>
    <!-- ng-hide 值为true时，隐藏当前元素 -->
    <p ng-hide="true">我是小明!</p>
```

### ng-if
- 控制元素的显示与否:*值为false时，元素会从dom移除*

```html
    <!-- ng-if，也能控制元素的显示或隐藏,为true时显示,为false时【会将当前dom元素移除】 -->
    <p ng-if="true">我是中国人，我爱自己的祖国!</p>
    <h1>ng-if="false"</h1>
    <p ng-if="false">我是中国人，我爱自己的祖国!</p>
```

### ng-switch
- 当ng-switch-when 对应的值等于ng-switch对应值时，当前dom元素就显示

```html
    <div ng-switch="name">
      <div ng-switch-when="小明">
        我是小明，我在这里！
      </div>
      <div ng-switch-when="小红">
        我是小红!
      </div>
    </div>
```

### 其他常用指令
- ng-checked：
  + 单选/复选是否选中,（单向数据绑定:界面操作不会影响数据模型的值）   ng-model:双向数据绑定
- ng-selected：
  + 是否选中
- ng-disabled：
  + 是否禁用
- ng-readonly：
  + 是否只读

### 常用事件指令

不同于以上的功能性指令，Angular还定义了一些用于和事件绑定的指令：

- ng-blur：失去焦点
- ng-focus： 获得焦点
- ng-change：内容改变
- ng-copy：复制
- ng-click: <div ng-click="aa()"></div>
- ng-dblclick：双击
- ng-submit：  form表单提单

### 指令的其他使用方式

data-xxx,在使用angular指令时，只需要在原先的指令前加上data-前缀。
如: data-ng-app,data-ng-click
x-ng-app,x-ng-click


# Angular

## 自定义指令
- 自定义指令无外乎增强了HTML,提供了额外的功能。
- 内部指令基本能满足我们的需求。
- 少数情况下我们有一些特殊的需要，可以通过自定义指令的方式实现

## 创建自定义指令
- *注意: 名字要符合驼峰合法*

```javascript
    // 1.创建模块对象
    var app = angular.module('directiveApp', [])

    // 2.创建自定义指令
    // 第一个参数：是指令的名字,必须是驼峰命名法
    //             使用时把大写改成小写，在原来大写前加上-
    // 第二个参数：和控制器的第二个参数类似!
    app.directive('myBtn', [function(){
      // 在这里直接return 一个对象就可以了
      return {
        // template属性，是封装的ui
        template:'<div><button>我是按钮</button></div>'
      }
    }])
```

### 自定义指令中回调里返回的对象的属性
- template: 需要提供一个html字符串,最终会被添加到当前页面使用了自定义指令的位置
- templateUrl:需要提供一个html文件路径，angular会发请求，请求对应的文件，
 把文件内容作为模板插入到自定义指令中间
            : 也可以提供一个script标签的id, angular会把script标签中的内容作为
              模板插入到自定义指令中间,*注意* 要改变script标签的type="text/ng-template"

- restrict: 也是需要提供一个字符串，限制自定义指令的使用形式
    + A : Attribute 表示只能以属性的形式使用
    + C : Class     表示只能以类样式名的形式使用
    + E : Element   表示只能以自定义标签的形式使用
    + ACE : 如果希望多种方
    + 式合适，就把对应值组合在一起。

- replace：需要提供一个布尔值，为true时，模板会被用来替换自定义指令所在标签，
        * 否则是插入到自定义指令中间

- transclude: 需要一个布尔值, 为true时会将自定义标签中的内容插入到模板中，
        * 拥有ng-transclude 指令的标签中间

- scope：需要一个对象: 可以用来获取自定义指令的属性值,
    -  给当前对象添加一个属性(如:tmp),属性值以@开头，后面跟上自定义指令的属性名
       然后就可以在模板中使用{{tmp}} 来得到对应的属性值
       + `scope: { tmp:'@mystyle'}`  {{tmp}}
       + `scope: { mystyle:'@'}`     {{mystyle}}

- link: 需要一个function 这是function在angular解析到相应指令时就会执行一次,
    + scope      ：类似于$scope,只不过scope的属性只能在模板中使用
    + element    : 自定义指令所在标签对应的对象(jqLite)
    + attributes : 包含了自定义指令所在标签的必有属性

## todomvc案例

### todomvc功能分析
1. 任务的展示
2. 添加任务
3. 删除任务
4. 修改任务内容
5. 切换任务完成与否的状态
6. 批量切换任务完成与否的状态
7. 显示未完成的任务数
8. 清除所有已完成任务
    - 注意： 在循环删除数组长度，会导致循环条件改变，也会导致元素原来的索引改变
9. 切换显示不同状态的任务

## 过滤器(filter)
- 格式化数据
- 过滤数据(filter)

```html
    <ul>
        <!--  如果指定一个布尔值，或者字符串就是全文匹配 -->
      <!-- 会到对应的todos中寻找，如果当前元素有completed属性且值 为true就会被显示出来。（只会到completed属性中寻找） -->
      <li ng-repeat="item in todos | filter : {completed:true} ">
        {{item.name}},{{item.completed}}
      </li>
    </ul>
```


```html
  <h1>currency</h1>
  <!-- 在数据模型后加上|  再加上过滤器的名字
        也可以在过滤器名字后指定参数，参数是写在冒号后面的-->
  <p>{{money | currency : '￥'}}</p>

  <h1>date</h1>
  <p>{{myDate | date : 'yyyy年MM月dd日 HH:mm:ss'}}</p>
```

- limitTo

```html
    <h1>limitTo</h1>
  <!-- 第一个参数，表明显示多少个字，第二个参数表示，从第几个字开始显示(索引从0开始) -->
  <p>{{msg | limitTo : 5 : 2}}...</p>
```

- orderBy 及 json

```html
<h1>json</h1>
 <!--  格式化显示json数据，参数指定缩近的长度 -->
 <pre>{{myJson | json : 8}}</pre>
  <h1>orderBy</h1>
  <!-- 对数据进行排序，参数，给+号就按正序排，- 就按倒序排 -->
  <span ng-repeat="item in arr | orderBy:'-'">{{item }}，</span>
```

- 在js中使用过滤器

```javascript
    <!-- $filter 需要在控制器的回调中传入 -->
    // 可以调用不同的过滤器得到相应的结果
      // 参数是一个过滤器的名字
      // 返回值是一个方法
      //        : 第一个参数是需要处理的数据
      //        : 后面的参数是当前过滤器本身需要的参数
     $scope.result =  $filter('currency')($scope.money,'￥')
```


# Angular

## todomvc使用filter过滤器来切换不同状态任务的显示
- arr=[{a:3,b:4},{a:5}]
- 数据模型 | filter : {a:3}

## $watch 监视数据模型的变化

```javascript
    $scope.name = '小明'
      $scope.age = 18

      // $watch可以用来监视数据模型的变化
      // 第一个参数: 数据模型对应的名字(字符串形式)
      // 第二个参数: 相应的数据模型变化就会调用 这个函数
      // 默认会直接执行一次回调函数
      $scope.$watch('name',function(now,old){
        // 第一个参数是变化后的值
        // 第二个参数是变化前的值
        // console.log(now,old)
      })
```
- 也可以监视方法的返回值

```javascript
    $scope.getAge = function(){
        return $scope.age
      }

      // 也能够监视$scope.属性中的方法的返回值
      $scope.$watch('getAge()',function(now,old){
        console.log(now,old)
      })
```

## 服务
- 创建服务

```javascript
    // 1.创建服务模块
  var app = angular.module('service',[])

  // 2.创建服务
  // 第一个参数：服务的名字
  // 第二个参数里的function:
  //    angular会把这个function当作构建函数，angular会帮助我们new这个构建函数，然后得到一个对象。A,B
  app.service('MyService', [function(){
    this.name = '小明'
  }])
```

- 使用服务

```javascript
    // 1.创建模块
  var app = angular.module('todosApp', ['service'])
  // 2.创建控制器
  app.controller('todosController', [
    'MyService'
    , function(MyService){
    // 这个MyService就是，对应的'MyService'时的回调函数new出的对象
    console.log(MyService)
}])
```

## 路由
- 根据url中不同的锚点值，在页面显示不同的内容！

### 路由使用

```javascript
    // 1.创建模块
    var app = angular.module('myApp', ['ngRoute'])

    // 2.配置路由规则(约定什么样的锚点值，对应什么样的内容)
    // 第一个参数与controller第二个参数类似
    app.config(['$routeProvider',function($routeProvider){

      // 第一个参数：对应的url中锚点值
      // 当angular检测到url中锚点变为/ali里，就会把template对应的内容插入到页面拥有ng-view指令的标签中
      $routeProvider.when('/ali',{
        template:'<div>阿里在二楼!</div>',
        // 指定一个控制器的名字,
        // 当前url中锚点值为/ali时就会执行控制器中的回调函数
        // 我们可以直接在template/templateUrl对应的模板中使用该控制器中对应的$scope属性值
        controller:'demoController'
        //templateUrl
      })
      .when('/baidu',{
        template:'<div>百度在1楼</div>'
      })
    }])
```

### 路由参数
- 在原有规则中可以加冒号:,
- 表示:号后的内容是可以变的(但是必须要有)
    + 如果加上问号，就能够匹配到了
- 在控制器中可以通过$routeParams得到myname对应的值

```javascript
    $routeProvider.when('/company/:myname？')
```

### otherwise
- 当不匹配when方法对应的规则时，就会匹配otherwise对应的规则


## webapi
- I/O
-  // url

## api
-
- console.log('小明') //小明
- I/O     docuemnt.getGetElementById('')

## 豆瓣API

- ng-src 指令: 用来取代src

### $http
- 发请求

```javascript
    http.get('./in_theaters/data.json')
      .then(function(res){
        // 成功的回调函数
        // console.log(res.data)
        $scope.data = res.data
      })
```


# Angular

## 跨域
- img  src可以指向一个跨域的资源
- link
- video audio .

- script: src 一般指向一个js文件
- a.com 请求b.com/tmp.js文件

-A 版本：
- 假设tmp.js 内容为: var data = 123
<script src="b.com/tmp.js"></script>
<script>
    console.log(data)
</script>

-B 版本
- 假设tmp.js 内容为: var data = {name:'小明',age:18}
<script src="b.com/tmp.js"></script>
<script>
    console.log(data)
</script>

-C 版本
- 假设tmp.js 内容为:  test({name:'小明',age:18})
<script>
    function test(data){
        console.log(data)
    }
</script>
<script src="b.com/tmp.js"></script>

## 正在热映

## 分页

## 即将上映

## Top250


## 合并重复的功能





## loading

## 导航焦点切换
## 搜索模块
## 详细页
