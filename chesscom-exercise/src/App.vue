<template>
  <div id="app">
    <ChessBoard />
  </div>
</template>

<script>
import ChessBoard from "@/components/ChessBoard.vue";

export default {
  name: "App",
  components: {
    ChessBoard,
  },
};
</script>

<style>
#app {
  font-family: Montserrat, Futura, Avenir, sans-serif;
  text-align: center;
  color: black;
  margin-top: 20px;
}

</style>
