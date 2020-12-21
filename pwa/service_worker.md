# Service Worker

## service worker 是什么
+ 基于 web worker
+ 必须是 https 访问
+ 增强离线缓存能力，并可以控制缓存内容和版本
+ 可作为浏览器和服务器之间的代理服务器，拦截全站请求
+ 事件驱动，有生命周期
+ 可访问 cache 和 indexedDB
+ 支持推送
+ 没有访问 dom 能力
+ 浏览器在后天独立网页运行的脚本
+ 拦截和处理网络请求，操作缓存
+ 支持 push api 等
+ 后台同步 & 更新缓存

## service worker 有什么用

## service worker 怎么用

## service worker 缺陷


# PWA - Progress Web Apps
### 用户获取 app 路径
+ Native App: 用户 => 应用商店 => 下载安装 => 内容
+ Web App: 用户 => 内容
### Web App劣势
+ 交互卡顿
+ 加载缓慢
+ 离线功能弱

### PWA 的三个特性： 快速、可靠、粘性
### PWA 技术清单
+ web app manifest
+ service worker
+ push api & notification api
+ app shell & app skeleton
+ ...

> PWA 必须是 https（因为基于 service worker）

### pwa 兼容性：Safari已支持

### 打开 web app 的方式
+ 书签、网址收藏
+ 地址栏输入URL
+ 搜索引擎

### web app manifest