分别从前端常见的 Vue.js、React.js 以及后端 Django（包含前端页面导航相关部分） 框架的角度，说明如何在页面间导航以及扩展新页面：

Vue.js：
1. 页面间导航：
    - 使用 `<router-link>` 组件：在模板中，例如 `<router-link to="/home">首页</router-link>`，`to` 属性指定目标页面的路径，点击该链接会进行页面跳转。
    - 编程式导航：在 Vue 组件的方法中，使用 `this.$router.push('/目标页面路径')` 来实现导航，例如 `this.$router.push('/about')` 会导航到 `/about` 页面；`this.$router.replace('/目标页面路径')` 也可用于导航，但它不会向历史记录中添加新条目。
2. 扩展新页面：
    - 创建新的 Vue 组件：在 `src/components` 目录下创建新的 `.vue` 文件，例如 `NewPage.vue`，编写模板、脚本和样式。
    - 配置路由：在 `src/router/index.js` 文件中，导入新组件并添加新的路由配置，如 `import NewPage from '../components/NewPage.vue';`，然后在 `routes` 数组中添加 `{ path: '/newpage', name: 'NewPage', component: NewPage }`。
    - 添加导航链接：在需要导航到新页面的地方，添加 `<router-link to="/newpage">新页面</router-link>`。

   React.js：
1. 页面间导航：
    - 使用 `<Link>` 组件（来自 `react-router-dom`）：例如 `<Link to="/home">首页</Link>`，点击该链接会进行页面跳转。
    - 编程式导航：在函数组件中，通过 `useHistory` hook 获取 `history` 对象，然后使用 `history.push('/目标页面路径')` 进行导航，如 `const history = useHistory(); history.push('/about');`。
2. 扩展新页面：
    - 创建新的 React 组件：在 `src` 目录下的合适文件夹中创建新的 `.js` 或 `.jsx` 文件，编写组件代码。
    - 配置路由：在路由配置文件（如 `src/App.js` 中使用 `react-router-dom` 的 `BrowserRouter` 和 `Routes`、`Route` 组件）中，导入新组件并添加新的路由，如 `<Route path="/newpage" element={<NewPage />} />`。
    - 添加导航链接：在需要导航到新页面的地方，添加 `<Link to="/newpage">新页面</Link>`。

 Django（包含前端页面导航相关部分）：
1. 页面间导航：
    - 在 HTML 模板中，使用 `<a>` 标签：例如 `<a href="{% url '目标页面的名称' %}">目标页面</a>`，`{% url '目标页面的名称' %}` 会生成对应视图函数的 URL。
    - 编程式导航：在 Django 视图函数中，使用 `redirect` 函数，如 `from django.shortcuts import redirect; return redirect('/目标页面路径')`。
2. 扩展新页面：
    - 创建新的视图函数：在 `views.py` 文件中编写新的视图函数，例如 `def new_page(request): return render(request, 'new_page.html', {})`。
    - 配置 URL：在 `urls.py` 文件中，导入新的视图函数并添加新的 URL 配置，如 `from. import views; urlpatterns = [path('newpage/', views.new_page, name='newpage')]`。
    - 创建 HTML 模板：在 `templates` 目录下创建 `new_page.html` 文件，编写页面内容。
    - 添加导航链接：在需要导航到新页面的模板中，添加 `<a href="{% url 'newpage' %}">新页面</a>`。
