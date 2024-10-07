<template>
    <button
      type="button"
      tabindex="-1"
      class="arrow-button"
      v-bind="$attrs"
      v-on="$listeners"
    >
      <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg" :fill=color :stroke=color stroke-width="2">
        <path :d="arrowPath" />
      </svg>
    </button>
</template>

<script>
const TYPES = {
  left: 'left',
  right: 'right',
  up: 'up',
  down: 'down'
}

const SVG_PATHS = {
  [TYPES.left]: 'M15.293 3.293 6.586 12l8.707 8.707 1.414-1.414L9.414 12l7.293-7.293-1.414-1.414z',
  [TYPES.right]: 'M7.293 4.707 14.586 12l-7.293 7.293 1.414 1.414L17.414 12 8.707 3.293 7.293 4.707z',
  [TYPES.up]: 'M12 6.586L3.293 15.293l1.414 1.414L12 9.414l7.293 7.293 1.414-1.414L12 6.586z',
  [TYPES.down]: 'M12 17.414L3.293 8.707l1.414-1.414L12 14.586l7.293-7.293 1.414 1.414L12 17.414z',
}

const DEFAULT_TYPE = TYPES.left

export default {
  name: 'VBArrowButton',

  inheritAttrs: false,

  props: {
    type: {
      type: String,
      default: 'right',
      validator: (value) => {
        return Object.keys(TYPES).includes(value)
      }
    },
    color: {
      type: String,
      default: 'dodgerblue',
    },
  },

  computed: {
    arrowPath () {
      return SVG_PATHS[this.type] || SVG_PATHS[DEFAULT_TYPE]
    }
  }
}
</script>

<style lang="scss" scoped>
.arrow-button {
  border: none;
  background: white;
  padding: 0;
  cursor: pointer;
  width: 18px;
  height: 18px;
}
</style>
