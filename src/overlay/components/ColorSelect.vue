<template>
  <div class="color-selector">
    <ul class="list-group">
      <li class="rounded-circle" @click.prevent="changeColor(c)" :class="{ active: selectedColor === c }" v-for="c in colors" :key="c" :style="{ 'background-color': c }">
        &nbsp;
      </li>
    </ul>
  </div>
</template>

<script>
import { colors } from '../../utils/color';

export default {
  name: 'ColorSelect',
  props: ['color'],
  data() {
    return {
      colors: colors,
      selectedColor: this.color,
    };
  },
  methods: {
    changeColor(color) {
      this.selectedColor = color;
      this.$emit('update:color', this.selectedColor);
    },
  },
};
</script>

<style scoped lang="scss">
.color-selector {
  margin: 5px 5px 5px 0;

  ul.list-group {
    flex-direction: row;
    li {
      display: inline;
      width: 25px;
      height: 25px;
      margin: 2px;
      &.active {
        border: 2px solid black;
      }
    }
  }
}
</style>
