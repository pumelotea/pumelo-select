# pumelo-select

> A Vue Select Component By Pumelo

### Feature:  
  1. pure data-drive component
  2. support vue instruction: v-model
  3. support data two-way binding
  4. support change event
  5. support disabled attribute
  6. provide search entry
  7. support data group
  
  
### Useage

import component by your choose,there are two components
```javascript
import SelectX from '@/components/Select'
import GroupSelectX from '@/components/GroupSelect'

```

register it in vue instance like 
```javascript
components: {
  SelectX,GroupSelectX
}
```

create data struct in vue instance,there are some diff in Select and GroupSelect

Select data struct
```javascript
[{value:'1',text:"Some Text"}]

```
GroupSelect data struct
```javascript
[{group:'groupName',data:[{value:'1',text:"Some Text"}]}]
```


use it in template code like
```javascript
   <select-x :data="list" v-model="selectedVal"></select-x>
   <group-select-x :data="list1" v-model="selectedVal1"></group-select-x>
```

### How to use @change event?
the change event is easy,you should define a function like
```javascript
onChange:function (data) {
  console.log(data)
}
```
then bind on @change  or v-on:change

### How to disable select?
use :disable="true" ,disabled default value is false

### How to use search entry?
the search input provide @on-search event,you can bind your function like  
```javascript
searchCallback:function(data){
  console.log(data)
  this.searchKey=data
}
```
```javascript
<select-x :data="list" v-model="selectedVal" @on-search="searchCallback"></select-x>
```
you should implement what logic you want. it's open.

### Style 
you can change style if you this style not ok, edit the component by your self.

### Feedback & Bugs
maybe the component have some bugs,if have can you send me a email(535553297#qq.com,replace '#' to '@') as soon as ?   
thanks for your support.
