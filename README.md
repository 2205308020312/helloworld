# helloworld
作业

## 安装与部署说明
# 环境准备：
确保本地已安装以下工具：
Node.js (推荐版本>= 16.x)
npm (Node.js 自带) 或 yarn

# 依赖安装：
1.克隆项目仓库：
git clone https://github.com/your-repo/books-management-system.git
cd books-management-system

2.安装项目依赖：
npm install

# 开发环境启动
启动开发服务器：
npm run serve

# 访问应用：
打开浏览器访问 http://localhost:8080
开发服务器支持热更新，修改代码后页面会自动刷新

# 生产环境部署
1.构建生产环境代码：
npm run build

2.构建产物说明：
构建后的静态文件会生成在 dist 目录下;
包含 HTML、CSS、JavaScript、图片等资源;
所有资源已进行压缩和优化

3.部署到 Web 服务器：
将 dist 目录下的所有文件复制到你的 Web 服务器根目录，例如：
Nginx;
Apache;
云服务提供商（如 AWS S3、阿里云 OSS）

## 配置说明
# 环境变量
项目使用 .env 文件配置环境变量：

.env.development：开发环境配置
.env.production：生产环境配置
API 接口地址
如需修改 API 接口地址，可在 .env 文件中修改 VUE_APP_API_BASE_URL 变量。
## 常见问题解答
1. 安装依赖时出现网络问题
问题现象：npm install 或 yarn install 过程中下载依赖失败
解决方案：
使用国内镜像源：

npm install --registry=https://registry.npmmirror.com

或配置 npm 镜像：

npm config set registry https://registry.npmmirror.com

2. 启动开发服务器失败
问题现象：执行 npm run serve 后浏览器无法访问 http://localhost:8080
解决方案：
检查端口是否被占用：

netstat -tulpn | grep :8080

修改端口：在 vue.config.js 中添加以下配置：

module.exports = {
  devServer: {
    port: 8081 // 修改为其他端口
  }
}

3. 构建后页面空白
问题现象：生产环境部署后页面空白，控制台报错
解决方案：
检查 vue.config.js 中的 publicPath 配置是否正确：

module.exports = {
  publicPath: process.env.NODE_ENV === 'production' ? '/' : '/'
}

确保服务器配置正确，支持单页面应用路由
4. 依赖版本冲突
问题现象：安装依赖时出现版本冲突错误
解决方案：
删除 node_modules 和 package-lock.json（或 yarn.lock）
重新安装依赖：

npm install


5. ESLint 检查失败
问题现象：开发过程中代码无法通过 ESLint 检查
解决方案：
自动修复可修复的错误：

npm run lint -- --fix


修改 .eslintrc.js 配置文件调整规则