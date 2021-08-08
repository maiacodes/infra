<template>
  <div class="block" v-bind:id="'block-' + id" v-bind:style="s">{{emote}}</div>
</template>

<script>
export default {
  name: "Block",
  props: ["id", "color", "emote"],
  computed: {
    s: function () {
      return "background-color: " + this.color;
    }
  }
}
</script>

<style>
.block {
  width: 30px;
  height: 30px;
  text-align: center;
}
</style>
