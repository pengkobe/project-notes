## 懒加载
死活说找不到模块
按照 https://github.com/ionic-team/ionic/issues/10946 进行修改
```
npm install @ionic/app-scripts@latest.
```
结果报
```
webpackJsonp is not defined
```
这个很好解决,在 index.html 中添加
```
<script src="build/vendor.js"></script>
```
最后，还是死活找不到模块，把 ionic-app-scripts 版本修改到 1.3.2 才解决