 # 1. 找到“添加书籍”入口

 在主页面或书籍列表页面，通常会有一个“添加书籍”按钮。
 点击该按钮后，会弹出一个表单或跳转到一个新页面，这个表单就是由 `BookForm.vue` 组件渲染的。

# 2. 了解 BookForm.vue 结构
一个典型的 `BookForm.vue` 组件如下：
<template>
  <form @submit.prevent="bookSubmit(bookTitle, bookAuthor)">
    <input v-model="bookTitle" placeholder="书名" />
    <input v-model="bookAuthor" placeholder="作者" />
    <button type="submit">提交</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      bookTitle: '',
      bookAuthor: ''
    }
  },
  methods: {
    bookSubmit(title, author) {
      // 向父组件发送新书数据
      this.$emit('add-book', { title, author });
      // 或者调用后端API
      // axios.post('/api/books', { title, author })
      // 清空输入框
      this.bookTitle = '';
      this.bookAuthor = '';
    }
  }
}
</script>
 要点说明：
 表单使用 `@submit.prevent`，防止页面刷新并调用 `bookSubmit` 方法。
 输入框通过 `v-model` 实现数据双向绑定。
 `bookSubmit` 方法负责提交数据，并在提交后清空表单。

# 3. 填写书籍信息

 在表单中输入书名和作者。

# 4. 提交表单

 点击“提交”按钮。
 会触发 `bookSubmit` 方法，将新书信息通过事件或 API 发送出去。

# 5. 刷新并查看书籍列表

 如果父组件监听了 `add-book` 事件，会自动将新书添加到列表中。
 如果用的是 API，确保添加成功后刷新书籍列表。

# 6. 父组件示例

假设父组件（如 `BookList.vue`）这样使用 `BookForm.vue`：
<BookForm @add-book="addBookToList" />

<script>
export default {
  data() {
    return {
      books: []
    }
  },
  methods: {
    addBookToList(newBook) {
      this.books.push(newBook);
      // 或者重新从后端获取书籍列表
    }
  }
}
</script>

# 总结

1. 点击“添加书籍”打开表单。
2. 填写书名和作者。
3. 提交表单。
4. 新书会出现在列表中，表单自动清空。