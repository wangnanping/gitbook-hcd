### 使用 gitbook 创建 hcd 项目文档

- 安装 npm install gitbook -g

* 创建 npm install -g gitbook-cli （查看不需要创建）

* 执行 gitbook install

- 执行 gitbook serve

* 执行 gitbook build ./ ./docs

打包出现如下问题

```javascript

Error: ENOENT: no such file or directory, stat 'G:\gitbook-hcd\docs\gitbook\gitbook-plugin-fontsettings\fontsettings.js'

```
解决办法：<br>
1.关闭杀毒软件 重新build
2.\.gitbook\versions\3.2.3\lib\output\website\copyPluginAssets.js文件 所有confirm改为false

#### 目录
  
 SUMMARY.md 左边导航菜单

 pageList   说明文档页面

 #### [查看地址](https://wangnanping.github.io/gitbook-hcd/pageList/DirectoryList.html)

 #### 打包发布page: gitbook build ./ ./docs