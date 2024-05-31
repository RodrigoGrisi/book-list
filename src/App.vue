<script setup>
import { reactive, ref } from "vue";
import Books from "./components/Books.vue";
import BookProgress from "./components/BookProgress.vue";

let books = reactive([
  {
    id: 1,
    title: "History of Europe",
    cover:
      "https://printpress.cmsmasters.net/default/wp-content/uploads/sites/11/2019/05/printpress-product-6-540x861.jpg",
    isRead: true,
    isbn: "0-395-8956-8",
    author: "Daniel Trejo",
  },
  {
    id: 2,
    title: "Penguin Classics",
    cover:
      "https://printpress.cmsmasters.net/default/wp-content/uploads/sites/11/2019/05/printpress-product-2-540x861.jpg",
    isRead: false,
    isbn: "0-395-3052-8",
    author: "Henry Eliot",
  },
  {
    id: 3,
    title: "Becoming",
    cover:
      "https://printpress.cmsmasters.net/default/wp-content/uploads/sites/11/2019/05/printpress-product-7-540x861.jpg",
    isRead: false,
    isbn: "0-395-5269-8",
    author: "Michelle Obama",
  },
  {
    id: 4,
    title: "Sonnets",
    cover:
      "https://printpress.cmsmasters.net/default/wp-content/uploads/sites/11/2019/05/printpress-product-5-540x861.jpg",
    isRead: false,
    isbn: "0-395-07157-8",
    author: "Daniel Trejo",
  },
]);
let showAddbook = ref(false);

function toggleIsRead(id) {
  books.forEach((book) => {
    if (book.id === id) {
      book.isRead = !book.isRead;
    }
  });
}
</script>

<template>
  <div v-if="!showAddbook" class="container">
    <h1>📖 Meus Livros</h1>
    <div class="header-btns">
      <button class="btn" >Adicionar Livro +</button>
    </div>

    <div class="books-container">
      <Books @toggleIsRead="toggleIsRead" :books="books" />
      <BookProgress :books="books" />
    </div>
  </div>

  <div v-else>
  <AddBook/>
  </div>
</template>
