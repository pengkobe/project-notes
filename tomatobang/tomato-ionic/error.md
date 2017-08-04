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
但是这么的报错，还是要人觉得不明不白，闲逛时看到这篇[文章](http://www.cnblogs.com/eccainiao/p/6892780.html),
其说是 cnpm 惹得祸，于是移除掉 node_modules 里的内容，重新使用 npm 进行安装 