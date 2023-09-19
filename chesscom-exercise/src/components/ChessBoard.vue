<template>
  <div class="chessboard-container">
    <div class="chessboard">
      <div 
        v-for= "(row,rowIndex) in board"
        :key="rowIndex"
        class="chessboard-row"
        :style="{height:chessboardCellHeight+'px' }"
      >
        <div
          v-for= "(cell, colIndex) in row"
          :key="colIndex"
          :class="['chessboard-cell', (rowIndex +colIndex)% 2 === 0 ? 'white':'black', 
                    clickedSquares.includes(squareLabel(rowIndex, colIndex)) ? 'clicked':'']"
          @click="handleSquareClick(rowIndex, colIndex)"
        >
          {{ cell }}
        </div>
      </div>
    </div>
    <SideBar :clickedHistory= "clickedHistory" />
  </div>
</template>

<script>
import SideBar from "@/components/SideBar.vue";

export default {
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
      clickedSquares: [],
      clickedHistory: [],
    };
  },
  methods: {
    handleSquareClick(rowIndex, colIndex) {
      const square = this.squareLabel(rowIndex, colIndex);
      if (!this.clickedSquares.includes(square)) {
        this.clickedSquares.push(square);
        this.clickedHistory.push(square); 
        setTimeout(() => {
          this.clickedSquares= this.clickedSquares.filter((sq) =>sq!== square);
        }, 500);
      }
    },
    squareLabel(rowIndex, colIndex) {
      const rowLabel = String.fromCharCode(97 + colIndex); 
      const colLabel= 8 - rowIndex; 
      return `${rowLabel}${colLabel}`;
    },
  },
  components: {
    SideBar,
  },
};
</script>


<style scoped>
.chessboard-container {
  display: flex;
  flex-direction: row;
  /*flex-wrap: wrap;*/
  justify-content: center;
  gap: 20px;
  padding: 0 15vw 0 15vw;
}

.chessboard {
  display: flex;
  flex-direction: column;
  flex-grow: 1;
}

.chessboard-row {
  display: flex;
  flex-grow: 0;
}

.chessboard-cell {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 24px;
  padding: 0; 
  width: 100%; 
  aspect-ratio: 1;
}

.white {
  background-color: rgb(237, 237, 237);
}

.black {
  background-color: rgb(44, 44, 44);
  color: rgb(237, 237, 237);
}

.clicked {
  background-color: #7db4ff;
  color: rgb(237, 237, 237);
  transition: background-color 0.4s;
}

@media (max-width: 768px) {
  .chessboard-container {
    flex-direction: column;
    align-items: center;
  }
  .chessboard {
    width: 100%; 
    max-width: none;
  }
  .sidebar {
    width: 100%;
  }

}

</style>
