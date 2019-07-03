# rnBundlePro
##### 初始化项目
```
react-native init rnBundlePro
react-native run-ios
```
##### 打包iOS应用程序
* 在ios目录下新建bundle目录
* 在rnBundlePro目录下运行打包命令(此时会在bundle目录下生成一个index.ios.jsbundle文件)
```
react-native bundle --entry-file index.js --platform ios --dev false --bundle-output ./ios/bundle/index.ios.jsbundle --assets-dest ./ios/bundle
```
* 在package.json中添加编译命令，以后打包可以直接运行npm run bundle-ios即可
```
{
    "scripts":{
        "bundle-ios":"node node_modules/react-native/local-cli/cli.js bundle --entry-file index.js  --platform ios --dev false --bundle-output ./ios/bundle/index.ios.jsbundle --assets-dest ./ios/bundle"
    }
}
```
* [在XCode中集成](https://www.jianshu.com/p/5bdce8da4d88)添加bundle目录，然后修改AppDelegate.m中加载包的方式
```
这里需要注意，
1、修改文件后，运行react-native run-ios会报错（稍后插入报错截图）
解决办法是index.js要对应index.jsbundle
若bundle目录下的文件名为index.ios.jsbundle,
我的rnBundlePro项目的入口文件index.js文件名就要改成index.ios.js
2、react-native run-ios运行连接是开发环境，打的不是内置包，此时需要使用npm start运行（没搞懂什么是内置包）

```