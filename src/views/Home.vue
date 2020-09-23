<template>
  <div class="home">
    <nav>
      <ul>
        <li
          v-for="(nav, index) in navList"
          :key="index"
          @mouseenter="navEnter(index)"
          :class="{ navHover: hoverIndex === index }"
        >
          {{ nav.title }}
        </li>
      </ul>
    </nav>
    <div class="chat-panel">
      <service-mode></service-mode>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import ServiceMode from "@/components/ServiceMode";
export default {
  name: "Home",
  data() {
    return {
      hoverIndex: -1,
      navList: [
        { title: "单聊模式" },
        { title: "群聊模式" },
        { title: "客服模式" }
      ]
    };
  },
  components: {
    ServiceMode
  },
  methods: {
    navEnter(index) {
      this.hoverIndex = index;
      this.$refs.carousel.goSlide(index);
    }
  }
};
</script>

<style scoped>
ul {
  list-style-type: none;
  text-align: center;
  margin: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
li:hover {
  cursor: pointer;
}
.navHover {
  background-color: aliceblue;
}
.chat-panel {
  height: 1070px;
  width: 650px;
}
</style>
