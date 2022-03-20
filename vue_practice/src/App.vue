<template>
  <h2>Book Collection</h2>
  <div v-if="showBook">
    <ul v-for="book in filteredBook" :key="book">
    <li :class="{fav:book.isFav}" @click="favHandler(book)">
      <p>Book Name - {{ book.title }}</p>
      <p>Author Name - {{ book.author }}</p>
      <p>Published Date - {{ book.date }}</p>
      <img :src="require(`@/assets/imgs/${book.img}`)" alt="book" width="300">
      <hr>
    </li>
  </ul>
  </div>
  <button @click="showBook = !showBook">
    <span v-if="showBook">Hide</span>
    <span v-if="!showBook">Show</span>
  </button>

  <br>
  <hr>

  <!-- Mouse Event -->
  <div class="box" @mouseover="mouseOverHandler($event, '\ntest mouse over')">Mouseover</div>
  <div class="box">Mouseleave</div>
  <div class="box">Double Click</div>
</template>

<script>
export default {
  data() {
    return {
      books: [
        {
          title: 'book-1',
          author: 'mgmg',
          date: 2022,
          isFav: true,
          img: 'book_1.jpg'
        },
        {
          title: 'book-2',
          author: 'agag',
          date: 2021,
          isFav: true,
          img: 'book_2.jpg'
        },
        {
          title: 'book-3',
          author: 'kgkg',
          date: 2020,
          isFav: true,
          img: 'book_3.jpg'
        }
      ],
      showBook: true,
    }
  },
  methods: {
    favHandler(book) {
      book.isFav = !book.isFav;
    },
    mouseOverHandler(event, testPara) {
      console.log('mouse over is working\n', event.type, testPara);
    }
  },
  computed: {
    filteredBook() {
      return this.books.filter(book => {
        return book.isFav;
      });
    }
  }
}
</script>

<style>
  .fav {
    background-color: rgb(87, 87, 87);
    color: white;
  }

  li {
    list-style: none;
  }

  .box {
    display: inline-block;
    padding: 50px;
    margin: 5px;
    background-color: burlywood;
    color: white;
  }
</style>