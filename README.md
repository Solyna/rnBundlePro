# rnBundlePro
>##### 初始化项目
```
react-native init rnBundlePro
react-native run-ios
```
---
>##### 打包iOS应用程序
1. 在ios目录下新建bundle目录
2. 在rnBundlePro目录下运行打包命令(此时会在bundle目录下生成一个index.ios.jsbundle文件)
```
react-native bundle --entry-file index.js --platform ios --dev false --bundle-output ./ios/bundle/index.ios.jsbundle --assets-dest ./ios/bundle
```
3. ackage.json中添加编译命令，以后打包可以直接运行npm run bundle-ios即可
```
{
    "scripts":{
        "bundle-ios":"node node_modules/react-native/local-cli/cli.js bundle --entry-file index.js  --platform ios --dev false --bundle-output ./ios/bundle/index.ios.jsbundle --assets-dest ./ios/bundle"
    }
}
```
4. XCode中集成](https://www.jianshu.com/p/5bdce8da4d88)添加bundle目录，然后修改AppDelegate.m中加载包的方式
>注意两点
```
1. 修改文件后（操作见下图），运行react-native run-ios
此时注意一下文件名要对应：
rnBundlePro项目的入口文件  对应于   bundle目录下的文件名为index.ios.jsbundle   
               index.js  --->    index.jsbundle
            index.ios.js --->    index.ios.jsbundle
不同的对应关系文件名，AppDelegate.m中的名字也要改为对应的
2. react-native run-ios运行连接是开发环境，打的不是内置包，此时需要使用npm start运行
```
> 在Xcode中修改AppDelegate.m文件
![修改示意图](http://pu3lpqiql.bkt.clouddn.com/WechatIMG11.jpeg
)
> 需要运行npm start错误截图
![错误图片](http://pu3lpqiql.bkt.clouddn.com/WechatIMG299.jpeg)
> 目录结构
![目录结构](http://pu3lpqiql.bkt.clouddn.com/WechatIMG12.jpeg)


