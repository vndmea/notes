# Service Worker
> service worker 是一种特殊的 worker，独立于网页主线程，必要时和主线程通信，2014年5月由 W3C 提出，前身是 AppCache(2012年，声明式，缓存策略有限，基本不受开发者控制)。是浏览器在独立于当前网页的后台实现一些不依赖页面或用户交互的脚本。特性包括消息推送，geofencing等，还可以拦截和处理网络请求，以编程方式管理被缓存的响应。

### service worker 检查
+ chrome://serviceworker-internals/
+ chrome://inspect/#service-workers

## service worker 是什么
+ 基于 web worker
+ 必须是 https 访问（本地环境除外）
+ 增强离线缓存能力，并可以控制缓存内容和版本
+ 可作为浏览器和服务器之间的代理服务器，拦截全站请求
+ 事件驱动，有生命周期
+ 可访问 cache 和 indexedDB
+ 支持推送
+ 不能直接访问/操作 dom ，使用 Promise/ Fetch API/ Cache API
+ 需要时直接唤醒，不需要时自动休眠
+ 离线缓存内容开发者可控
+ 一旦被安装则永远存活，除非手动卸载
+ 广泛使用 Promise
+ 浏览器在后天独立网页运行的脚本
+ 拦截和处理网络请求，操作缓存
+ 支持 push api 等
+ 后台同步 & 更新缓存

## service worker 有什么用
+ 使用拦截和处理网络请求的能力实现离线应用
+ 使用后台运算和页面通信实现后台数据处理

## service worker 生命周期
```
 no service worker => installing => error
                                 => activated => idle <=> terminated
                                                      <=> fetch/message

 register => install => error
                     => waiting => (activated，新的安装完成后会暂时处于等待状态) 
                     => activated => idle  <=> terminated
                                           <=> active
``` 

## service worker 缺陷


# PWA - Progress Web Apps
> pwa 是一种 web app 新模型，是一个渐进式的 web app，通过一系列新的 web 特性，配合优秀的 ui 交互设计， 逐步增强 web app 的用户体验。
### 用户获取 app 路径
+ Native App: 用户 => 应用商店 => 下载安装 => 内容
+ Web App: 用户 => 内容
### Web App劣势
+ 交互卡顿
+ 加载缓慢
+ 离线功能弱

### PWA 的三个特性： 快速、可靠（无网络）、融入（添加到手机桌面，全屏，推送）

### lighthouse 工具 > pwa
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
+ 作用
  + 有唯一的图标和名称与其他站点区分·
  + 控制从主屏幕启动时的内容，避免生硬的过度
  + 隐藏浏览器相关的UI
+ 属性
  + name
  + short_name
  + display: fullscreen, minimal-ui, standalone, browser
  + start_url
  + icons
  + background_color: 启动画面背景颜色
  + theme_color: 启动画面状态栏、地址栏颜色   
  > 兼容方案：通过 meta/link声明私有属性
+ 网站显示应用安装横幅条件
  + 部署 manifest.json 且正确配置属性
  + 注册 Service Worker
  + 支持 HTTPS
  + 用户同一浏览器间隔少于5分钟内访问
  > 注意：Safari不支持应用安装横幅

### 性能优化手段
+ CDN 分发
+ CSS Sprite
+ Compress / Gzip
+ Async / Defer
+ HTTP Cache
> 加快资源加载速度，减少白屏时间

### 原理
```
pages <=> Service worker <=> Server
                         <=> CacheStorage
```