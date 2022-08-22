<template>
  <div>
    <div v-for="item of books" :key="item.title">
      <h2 :id="item.title">
        <a :href="`#${item.title}`" class="header-anchor">#</a>
        {{ item.title }}
      </h2>
      <div class="books-fill">
        <a class="item" :href="children.url" target="_blank" v-for="children of item.children" :key="children.title">
          <div class="img-fill">
            <img :src="`${children.IconUrl?children.IconUrl:GetUrlLeft(children.url)}`" alt="" />
          </div>
          <div class="right">
            <div class="title">{{ children.name }}</div>
            <div class="value">{{ children.value }}</div>
          </div>
        </a>
      </div>
    </div>
  </div>
</template>
<script>
import xxbooks from "./booksData";
export default {
  props: {
    title: {
      type: String,
      required: false,
      value: "",
    },
  },
  data() {
    return {
      count: 1,
    };
  },
  computed: {
    books: () => {
      return xxbooks;
    },
    GetUrlLeft:()=>{
      return (url)=>{
        // return `${url.substring(0,url.indexOf(':'))}://${url.split('/')[2]}`
        return `https://favicon.cccyun.cc/${url}`
      }
    }
  },
  methods: {
    add() {
      this.count++;
    },
  },
};
</script>
<style>
.books-fill {
  padding: 10px 0;
  display: flex;
  justify-content: flex-start;
  flex-wrap: wrap;
}
.item {
  display: flex;
  min-width: 184px;
  width: 184px;
  height: 40px;
  padding: 10px 10px;
  border-radius: 4px;
  border: 1px solid transparent;
  transition: all 0.2s ease-out;
  cursor: pointer;
  text-decoration: none !important;
  line-height: 100%;
}
.item > .img-fill {
  height: 40px;
  width: 40px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.item img {
  display: block;
  height: 24px;
  width: 24px;
}
.item > .right {
  margin-left: 10px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.item > .right .title {
  font-size: 16px;
}
.item > .right .value {
  font-size: 12px;
  color: #909090;
}
.item:hover {
  border: 1px solid #f5f5f5;
  box-shadow: 0 0 8px #ccc;
}
</style>
