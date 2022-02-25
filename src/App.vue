<template>
  <div id="app">
    <section>
      <input type="text" v-model="newOptionName" v-on:keyup.enter="addOption">
      <button  @click="addOption">Add</button>
    </section>
    <section>
      <WinWheel :segments="options" :rerender="changed"/>
    </section>
  </div>
</template>

<script>
import WinWheel from "./components/WinWheel.vue";
import { getRandomColor } from "./js/randomColors";

export default {
  name: "app",
  components: {
    WinWheel
},
  data() {
    return {
      options: [      ],
      newOptionName: "",
      changed: false
    };
  },
  methods: {
    addOption() {
      this.options.push({
          textFillStyle: "#000",
          fillStyle: getRandomColor(),
          text: this.newOptionName
        });
      this.changed = true;
      setTimeout(() => this.changed = false, 500);
      this.newOptionName = "";
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
