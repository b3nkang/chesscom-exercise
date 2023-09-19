<template>
    <div class="chessboard">
      <div v-for="(row, rowIndex) in board" :key="rowIndex" class="chessboard-row">
        <div
          v-for="(cell, colIndex) in row"
          :key="colIndex"
          :class="['chessboard-cell', (rowIndex + colIndex) % 2 === 0 ? 'white' : 'black']"
        >
          {{ cell }}
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "ChessBoard",
    data() {
      return {
        board: [
          ['R', 'N', 'B', 'Q', 'K', 'B', 'N', 'R'],
          ['P', 'P', 'P', 'P', 'P', 'P', 'P', 'P'],
          [' ', ' ', ' ', ' ', ' ', ' ', ' ', ' '],
          [' ', ' ', ' ', ' ', ' ', ' ', ' ', ' '],
          [' ', ' ', ' ', ' ', ' ', ' ', ' ', ' '],
          [' ', ' ', ' ', ' ', ' ', ' ', ' ', ' '],
          ['p', 'p', 'p', 'p', 'p', 'p', 'p', 'p'],
          ['r', 'n', 'b', 'q', 'k', 'b', 'n', 'r'],
        ],
      };
    },
  };
  </script>
  
  <style scoped>
  .chessboard {
    display: inline-block;
    border: 1px solid #333;
  }
  
  .chessboard-row {
    display: flex;
  }
  
  .chessboard-cell {
    width: 50px;
    height: 50px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 24px;
  }
  
  .white {
    background-color: #fff;
  }
  
  .black {
    background-color: #333;
    color: #fff;
  }
  </style>
  