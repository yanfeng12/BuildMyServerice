### 如何运行程序

所有项目都是可以直接

```
npm install
node app.js
```
来启动项目

## 一。mongoDB 使用4.0以上版本，[安装教程](https://blog.csdn.net/sj2050/article/details/82838882)
### 1、选择complete。
### 2、Run service as Network Service user。
### 3、Data Directory:  D:\data  
### 4、Log Directory:  D:\log(尽量使用根目录)
### 5、去掉Install MongoDB Compass。6、测试[](http://localhost:27017)
## 二。安装grunt [grunt](https://blog.csdn.net/sinat_38992528/article/details/79400595)
## 三。使用bcryptjs代替bcrypt，我的电脑装不上bcrypt。
### 1.bcryptjs是一个第三方密码加密库，是对原有bcrypt的优化，优点是不需要安装任何依赖
### 2.引入bcryptjs库.npm install bcryptjs --save
```
var bcrypt = require('bcryptjs');
```
### 3.同步用法(Sync)
```
//生成hash密码
var bcrypt = require('bcryptjs');
var salt = bcrypt.genSaltSync(10);
var hash = bcrypt.hashSync("B4c0/\/", salt);
// Store hash in your password DB. 
```
```
//密码验证
// Load hash from your password DB. 
bcrypt.compareSync("B4c0/\/", hash); // true 
bcrypt.compareSync("not_bacon", hash); // false 
```
```
//快速生成hash值
var hash = bcrypt.hashSync('bacon', 8);
```
### 4.异步用法(Async)
```
//生成hash密码
var bcrypt = require('bcryptjs');
bcrypt.genSalt(10, function(err, salt) {
    bcrypt.hash("B4c0/\/", salt, function(err, hash) {
        // Store hash in your password DB. 
    });
});
```
```
//密码验证
// Load hash from your password DB. 
bcrypt.compare("B4c0/\/", hash, function(err, res) {
    // res === true 
});
bcrypt.compare("not_bacon", hash, function(err, res) {
    // res === false 
});
 
// As of bcryptjs 2.4.0, compare returns a promise if callback is omitted: 
bcrypt.compare("B4c0/\/", hash).then((res) => {
    // res === true 
});
```
```
//快速生成hash值
bcrypt.hash('bacon', 8, function(err, hash) {
});
```
## 四、[注册用户](http://localhost:3001)，注册后，用Navicat 12 for MongoDB修改用户权限role,role>50为超级管理员.
## 五、登陆后[用户列表页](http://localhost:3001/admin/user/list)
## 六、[电影展示功能](http://localhost:3001/admin/movie/list)
## 七、[电影录入功能](http://localhost:3001/admin/movie/new)
## 八、本项目使用grunt打包，运行时直接grunt
