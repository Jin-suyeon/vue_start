<template>
  <div>
    <div @click="modalOpen = false" class="black-bg" v-if="modalOpen === true">
      <div class="white-bg">
        <img :src="onerooms[userClickIdx].image" />
        <h4>{{ onerooms[userClickIdx].title }}</h4>
        <div>{{ onerooms[userClickIdx].price }}원</div>
        <p>{{ onerooms[userClickIdx].content }}</p>
      </div>
    </div>

    <div class="menu">
      <a v-for="(menu, idx) in menus" :key="idx">{{ menu }}</a>
    </div>

    <Discount />

    <div v-for="(oneroom, i) in onerooms" :key="oneroom.id">
      <img class="room-img" :src="oneroom.image" />
      <h4
        @click="
          modalOpen = true;
          userClickIdx = i;
        "
        class="product-name"
      >
        {{ oneroom.title }}
      </h4>
      <p class="product-price">{{ oneroom.price }}원</p>
    </div>
  </div>
</template>

<script>
import onerooms from "./assets/data.js";
import Discount from "./components/Discount.vue";

export default {
  name: "App",
  data() {
    return {
      menus: ["Home", "Shop", "About"],
      onerooms,
      modalOpen: false,
      userClickIdx: 0,
    };
  },
  methods: {
    increase(idx) {
      this.warn[idx]++;
    },
  },
  components: {
    Discount,
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding-bottom: 30px;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

.product-name {
  margin-bottom: 10px;
  cursor: pointer;
}

.product-price {
  margin-bottom: 10px;
}

button {
  margin-right: 10px;
  padding: 2px 5px;
}

.room-img {
  width: 100%;
  margin: 40px 0;
}

.black-bg {
  position: fixed;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  padding: 20px;
}

.white-bg {
  width: 100%;
  border-radius: 5px;
  background-color: white;
  padding: 40px;
}

.white-bg img {
  width: 100%;
  border-radius: 8px;
  margin-bottom: 40px;
}

.white-bg h4 {
  margin-bottom: 20px;
}

.white-bg div {
  margin-bottom: 20px;
}
</style>
