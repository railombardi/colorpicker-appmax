<template>
  <div :class="$style.colorPicker">
    <div
      :class="$style.colorDiv"
      :style="`background-color:${selectedColor}`"
    >
      <span :class="$style.selectedColorIndicator">{{selectedColor}}</span>
    </div>
    <div :class="$style.colorsList">
      <div
        v-for="color in colorPickerOptions"
        :key="color"
        :class="$style.colorOption"
        :style="`background-color:${color}`"
        @click="selectColor(color)"
      />
    </div>
    <div :class="$style.restoreDiv">
      <span @click="restore" :class="$style.restoreButton"> Restore default </span>
    </div>
  </div>

</template>
<script>
export default {
  props: {
    colorPickerOptions: {
      type: Array,
      default: () => [],
    },
    initialSelectedColor: {
      type: String,
      default: 'black',
    },
  },
  created() {
    this.selectedColor = this.initialSelectedColor;
  },
  data() {
    return {
      selectedColor: null,
    };
  },
  methods: {
    selectColor(colorName) {
      this.selectedColor = colorName;
    },
    restore() {
      this.selectedColor = this.initialSelectedColor;
    },
  },
};
</script>

<style lang="scss" module>
.colorPicker {
  display: grid;
  grid-template-rows: 70% 20% 10%;
  height: 450px;
  width: 400px;
  align-items: center;
  box-shadow: 4px 3px 21px 8px rgba(0,0,0,0.75);
}
.colorDiv {
  display: flex;
  align-items: flex-end;
  justify-content: center;
  height: 100%;
}
.selectedColorIndicator {
  margin-bottom: 20px;
  background-color: grey;
  color: black;
  padding: 0 30px;
}
.colorsList {
  display: grid;
  grid-template-columns: repeat(auto-fill, 50px);
  column-gap: 25px;
  padding: 0 25px;
}
.colorOption{
  width: 50px;
  height: 50px;
  cursor: pointer;
}
.restoreButton{
  border: 2px solid grey;
  border-radius: 10px;
  padding: 5px;
  background-color: grey;
  color: black;
  cursor: pointer;
}
</style>
