<template>
  <dialog :class="'gameStart'"></dialog>
  <div :class="'field'">
    <div v-for="row in gameSize">
      <div :class="'row'">
        <div v-for="objects in gameSize">
          <div :class="'field'">
            {{ objects }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
const gameSize = ref<number>(3);

type Tile = {
  isEmpty: boolean;
  isCross: string;
};

const gameMap = ref<Tile[][]>([]);

function generateField() {
  for (let i = 0; i < 3; i++) {
    const rowY = [];
    for (let k = 0; k < 3; k++) {
      const tile = {
        isEmpty: true,
        isCross: '',
      };
      rowY.push(tile);
    }

    gameMap.value.push(rowY);
  }
}
</script>

<style scoped>
.tile {
  border: 0.5px solid black;
  box-sizing: border-box;
  width: 50px;
  height: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 50px;
}

.field {
  display: grid;
  grid-template-columns: (9, 1fr);
  width: 150px;

  /* margin-right: 15.4%; */
}
</style>
