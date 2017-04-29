## bug 集锦
* ngFor 在数组触发改变后不会更新界面的数据，一说是对象的属性改变不会出发，只有整个对象都改了才会出发，于是有人发明了 hack [方法](http://stackoverflow.com/questions/40829951/angular2-ngfor-onpush-change-detection-with-array-mutations).
```javascript
this.myArray.push(newItem);
this.myArray = this.myArray.slice();
```
