<template>
  <div class="sidebar">
    <h2>Clicked Squares</h2>
    <ul>
      <li v-for="(square, index) in clickedHistory" :key="index">
        {{ square }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    clickedHistory: Array, 
  },
};
</script>

<style scoped>
.sidebar {
  background-color: #f5f5f5;
  padding: 20px;
  width: 25%;
  box-sizing: border-box;
  text-align: center;
}

.sidebar h2 {
  margin-top: 0;
  font-size: 99%;
}

.sidebar ul {
  list-style: none;
  padding: 0;
}

.sidebar li {
  margin-bottom: 10px;
}
</style>
