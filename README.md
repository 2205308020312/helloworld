From the perspectives of frontend frameworks like Vue.js and React.js, as well as the backend framework Django (including frontend page navigation-related parts), here’s how to navigate between pages and extend new pages:

 Vue.js:
1. Navigating Between Pages:
   - Using the `<router-link>` component: In the template, for example, `<router-link to="/home">Home</router-link>`, the `to` attribute specifies the path of the target page. Clicking this link will navigate to the page.
   - Programmatic navigation: In Vue component methods, use `this.$router.push('/target-page-path')` to navigate. For example, `this.$router.push('/about')` will navigate to the `/about` page. `this.$router.replace('/target-page-path')` can also be used for navigation, but it won’t add a new entry to the history.
2. Extending New Pages:
   - Create a new Vue component: Create a new `.vue` file in the `src/components` directory, such as `NewPage.vue`, and write the template, script, and styles.
   - Configure routing: In the `src/router/index.js` file, import the new component and add a new route configuration, such as `import NewPage from '../components/NewPage.vue';`, then add `{ path: '/newpage', name: 'NewPage', component: NewPage }` to the `routes` array.
   - Add a navigation link: Wherever navigation to the new page is needed, add `<router-link to="/newpage">New Page</router-link>`.

React.js:
1. Navigating Between Pages:
   - Using the `<Link>` component (from `react-router-dom`): For example, `<Link to="/home">Home</Link>`. Clicking this link will navigate to the page.
   - Programmatic navigation: In functional components, use the `useHistory` hook to get the `history` object, then use `history.push('/target-page-path')` to navigate, such as `const history = useHistory(); history.push('/about');`.
2. Extending New Pages:
   - Create a new React component: Create a new `.js` or `.jsx` file in an appropriate folder under `src`, and write the component code.
   - Configure routing: In the routing configuration file (e.g., using `BrowserRouter`, `Routes`, and `Route` components from `react-router-dom` in `src/App.js`), import the new component and add a new route, such as `<Route path="/newpage" element={<NewPage />} />`.
   - Add a navigation link: Wherever navigation to the new page is needed, add `<Link to="/newpage">New Page</Link>`.

 Django (Including Frontend Page Navigation):
1. Navigating Between Pages:
   - In HTML templates, use the `<a>` tag: For example, `<a href="{% url 'target-page-name' %}">Target Page</a>`. `{% url 'target-page-name' %}` will generate the URL for the corresponding view function.
   - Programmatic navigation: In Django view functions, use the `redirect` function, such as `from django.shortcuts import redirect; return redirect('/target-page-path')`.
2. Extending New Pages:
   - Create a new view function: Write a new view function in the `views.py` file, such as `def new_page(request): return render(request, 'new_page.html', {})`.
   - Configure URLs: In the `urls.py` file, import the new view function and add a new URL configuration, such as `from . import views; urlpatterns = [path('newpage/', views.new_page, name='newpage')]`.
   - Create an HTML template: Create a `new_page.html` file in the `templates` directory and write the page content.
   - Add a navigation link: In the template where navigation to the new page is needed, add `<a href="{% url 'newpage' %}">New Page</a>`.