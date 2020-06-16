```
目录结构如下
|-- DirectoryList
|-- .browserslistrc
|-- .eslintignore
|-- .eslintrc.js
|-- .gitignore
|-- .gitmodules
|-- babel.config.js
|-- cypress.json
|-- dir.text
|-- jest.config.js
|-- package-lock.json
|-- package.json
|-- postcss.config.js
|-- README.md
|-- report.20200224.165403.12516.0.001.json
|-- tsconfig.json
|-- vue.config.js // webpack 打包配置
|-- public
| |-- config.json // 接口，百度密匙 版本号 接口超时 页面初始化等 Json 信息配置
| |-- index.html
| |-- manifest.json
| |-- robots.txt
| |-- web.config
| |-- css
| | |-- template  // 配置5套模版样式
| |-- face_recognition
| |-- img // 图片
| |-- pay
| |-- pdf // PDF 在线查看器
|-- src
| |-- App.vue
| |-- main.ts
| |-- registerServiceWorker.ts // serviceWorker 做缓存加载，暂时关闭
| |-- shims-tsx.d.ts
| |-- shims-vue.d.ts
| |-- types.d.ts // 申明一些静态类型文件
| |-- api // api 服务
| | |-- AuthApiServiceProxy.ts
| | |-- BaseServiceProxy.ts
| | |-- BillApiServiceProxy.ts
| | |-- DataUploadApiServiceProxy.ts
| | |-- DefaultApiService.ts
| | |-- PayCenterApiServiceProxy.ts
| | |-- ServiceProxyConfig.ts
| | |-- SessionStorageApi.ts
| | |-- TaxUploadApiServiceProxy.ts
| | |-- trackService.ts
| |-- assets
| | |-- audio // 消息提醒
| | | |-- reminder.mp3
| | |-- css // 公用样式
| | | |-- heyui_index.css
| | | |-- index.scss
| | | |-- mixin.scss
| | | |-- public.scss
| | | |-- publicColor.scss
| | | |-- transition.scss
| | |-- image
| |-- bus // event-bus
| | |-- index.ts
| |-- business
| | |-- DataHandle // 对特殊类型做处理 如金额类型等，根据后台配置信息做小数点约束
| | | |-- dataHandle.ts
| | | |-- rules.ts
| | |-- Getdate // 公共方法 如 日期处理
| | | |-- getdate.ts
| | |-- Pay // 封装多渠道支付方式 如各大银行
| | |-- main.ts
| | |-- MD5.ts
| |-- carTrackApi
| | |-- carTrackService.ts // 对接百度鹰眼
| | |-- commonfun.ts // 公用方法处理
| |-- components  
| | |-- BaseComponent // 复用小模块功能组件，如按钮、下拉框、输入框、地图、图片......等根据公司业务做二次封装
| | | |-- BaseComponent.ts // 组件小模块功能组件公用方法
| | |-- BatchOperationComponent // 复用批量导入司机证件照组件
| | | |-- 说明文件.text
| | | |-- DialogBatchImg
| | |-- Breadcrumb // 面包屑
| | | |-- index.vue
| | |-- Card // 复用的运单详情组件
| | | |-- BaseCard.ts
| | | |-- card-details
| | |-- ExcelImport // 针对车辆和司机的 复用 excel 表上传 和 批量处理组件
| | | |-- Car
| | | |-- Driver
| | | |-- DriverPay
| | | |-- TransportOrder
| | | |-- UploadXlsx.vue
| | |-- Hamburger
| | | |-- index.vue
| | |-- Page // 复用的页面组件
| |-- icons // 字体图标库
| |-- router // 路由
| |-- store // vuex
| |-- utils // 验证信息
| |-- views // 业务页面 中存在 Html 文件夹 为白名单页面 不需要验证权限
|-- tests  
|-- e2e
| |-- .eslintrc.js
| |-- plugins
| | |-- index.js
| |-- specs
| | |-- test.js
| |-- support
| |-- commands.js
| |-- index.js
|-- unit
|-- .eslintrc.js
|-- example.spec.ts
```
