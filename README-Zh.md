# pumelo-select

> A Vue Select Component By Pumelo

English document see => README.md

### 演示
https://pumelotea.github.io/pumelo-select-preview/

### 特性:  
  1. 纯数据驱动
  2. 支持vue指令:v-model
  3. 支持数据双向绑定
  4. 支持change事件
  5. 支持禁用组件
  6. 提供搜索入口
  7. 支持数据分组
  
  
### 用法

选择组件导入，这里有2个组件，一个是基本的，一个是分组的
```javascript
import SelectX from '@/components/Select'
import GroupSelectX from '@/components/GroupSelect'

```

注册组件，如下
```javascript
components: {
  SelectX,GroupSelectX
}
```

创建数据结构，这里基本的选择框和分组选择框有一些不同。

Select的数据结构
```javascript
[{value:'1',text:"Some Text"}]

```
GroupSelect的数据结构
```javascript
[{group:'groupName',data:[{value:'1',text:"Some Text"}]}]
```


在模板代码中使用，如下
```javascript
   <select-x :data="list" v-model="selectedVal"></select-x>
   <group-select-x :data="list1" v-model="selectedVal1"></group-select-x>
```

### 怎么使用 @change 事件?
change事件比较简单，你可以定义一个方法，如下
```javascript
onChange:function (data) {
  console.log(data)
}
```
然后绑定在@change 或者 v-on:change

### 怎么禁用选择框?
使用 :disable="true" 在组件上，默认是不禁止的

### 怎么使用搜索入口?
搜索入口提供了一个输入框来输入搜索关键字，通过@on-search事件回传输入的关键字，因此你可以定义一个方法来接收该值
```javascript
searchCallback:function(data){
  console.log(data)
  this.searchKey=data
}
```
```javascript
<select-x :data="list" v-model="selectedVal" @on-search="searchCallback"></select-x>
```
收到值后，你应该实现自己的搜索逻辑，然后改变搜索框的数据列表。it's open.

### 样式 
你可以修改控件的样式，控件本身没有多少样式，但是依赖了极其少了的bootstrap.css 和其他的一些css样式。  
当你引入到你的项目中时，为了保证样式的统一，我更加希望你去直接修改控件的样式。甚至修改控件。

### 反馈 & Bugs
这个控件会存在一些问题，如果你发现了，请发送邮件到(535553297#qq.com,replace '#' to '@')   
感谢你的支持。
