<template>
  <div id="app">
    <h1>infra.</h1>
    <div class="grid-container">
      <Block v-for="id in grid" v-bind:key="id" v-bind:id="id" v-bind:color="greenGrid[id]" v-bind:emote="gridEmote[id]"></Block>
    </div>
  </div>
</template>

<script>
import Block from "@/components/Block";
export default {
  name: 'App',
  data: function () {
    const gridSize = 400;

    let greens = ["#4a6f28", "#5b8731", "#3e5c20", "#527a2d", "#5b8b32"];
    let greenGrid = {};
    for (let i = 0; i < gridSize; i++) {
      greenGrid[i+1] = greens[Math.floor(Math.random()*greens.length)];
    }

    let greenEmotes = ["🌱", "🌳", "🌴", "🌱"]
    let homeEmotes = ["🏚", "🏠", "🏡", "🏠", "🏡", "🏠", "🏡"]
    let chances = {80: [""], 97: greenEmotes, 100: homeEmotes}
    let gridEmote = {};
    for (let i = 0; i < gridSize; i++) {
      const chance = Math.floor(Math.random() * 100)
      for (let prop in chances) {
        if (prop > chance) {
          let j = chances[prop]
          gridEmote[i+1] = j[Math.floor(Math.random()*j.length)];
          break
        }
      }
    }

    return {
      grid: gridSize,
      greenGrid: greenGrid,
      gridEmote: gridEmote,
    }
  },
  components: {
    Block
  }
}
</script>

<style>
.grid-container {
  background-color: #2196F3;
  padding: 50px;
  width: 600px;
  display: grid;
  grid-template-columns: 30px 30px 30px 30px 30px 30px 30px 30px 30px 30px 30px 30px 30px 30px 30px 30px 30px 30px 30px 30px;
  /*grid-template-rows: 30px 30px;*/
  grid-auto-flow: row;
}

body {
  /*background-color: #ffffff;*/
}
</style>
