### 初始化
```
npm init vite // 使用 Vite 构建 Vue3 项目
cd geek
npm install // 初始化 npm 配置文件
npm run dev // 启动 Vite 服务器
npm install vue-router@next vuex@next // 安装 Vuex 数据管理，vue-router 路由管理
```

### 规范化目录组织结构
```
├── src
│   ├── api            数据请求
│   ├── assets         静态资源
│   ├── components     组件
│   ├── pages          页面
│   ├── router         路由配置
│   ├── store          vuex数据
│   └── utils          工具函数
```