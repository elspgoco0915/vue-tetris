<script lang="ts" setup>
// 3-1 で作成したテトリスのフィールドを定義するコード
const row = 20;
const column = 10;

const field = new Array(row);

for (let i = 0; i < row; i++) {
  const fieldColumn = new Array(column).fill(0);
  field[i] = fieldColumn;
}

// 画面最上部の左端に縦の I-テトリミノを配置する
field[0][0] = 1;
field[1][0] = 1;
field[2][0] = 1;
field[3][0] = 1;

const classBlockColor = (x: number, y: number): string => {
  const type = field[y][x];
  if (type > 0) {
    switch (type) {
      case 1:
        return "block-i";
      case 2:
        return "block-o";
      case 3:
        return "block-s";
      case 4:
        return "block-z";
      case 5:
        return "block-j";
      case 6:
        return "block-l";
      case 7:
        return "block-t";
      default:
        return "";
    }
  }
};
</script>

<template>
  <h1>プレイ画面</h1>
  <h2>ユーザ名: {{ $route.query.name }}</h2>

  <div class="container">
    <table class="field" style="border-collapse: collapse">
      <tr v-for="(row, y) in field" :key="y">
        <td class="block" v-for="(col, x) in row" :key="() => `${x}${y}`">
          {{ col }}
        </td>
      </tr>
    </table>
  </div>
</template>

<style lang="scss" scoped>
// .container {
//   display: flex;
//   justify-content: center;
//   align-items: stretch;
// }

// .field {
//   border: ridge 0.4em #2c3e50;
//   border-top: none;
// }

.block {
  width: 1em;
  height: 1em;
  border: 0.1px solid #95a5a6;
}

/*
   各テトリミノに対応した色を扱うクラス定義
   .block-i, .block-o のようにクラスが定義される
  */
&-i {
  background: #3498db;
}
&-o {
  background: #f1c40f;
}
&-t {
  background: #9b59b6;
}
&-j {
  background: #1e3799;
}
&-l {
  background: #e67e22;
}
&-s {
  background: #2ecc71;
}
&-z {
  background: #e74c3c;
}
</style>

