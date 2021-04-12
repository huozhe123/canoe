<template>
    <button
      :class="[
        'c-button',
        type ? `c-button--${type}` : '',
        button
      ]"
    >
      普通按钮
    </button>
</template>

<script lang="ts">
import {defineComponent} from 'vue'
import type {PropType} from 'vue'
// import {isValidComponentSize} from 'utils/validators'
import {ComponentSize} from 'utils/types'

const isValidComponentSize = (val: string) => ['', 'large', 'medium', 'small', 'mini'].includes(val)
type IButtonType = PropType<'primary' | 'success' | 'warning' | 'danger' | 'info' | 'text' | 'default'>

export default defineComponent({
    name: 'c-button',
    data() {
        return {
            
        };
    },
    props: {
      type: {
        type: String as IButtonType,
        default: 'default',
        validator: (val: string) => {
          return [
            'default',
            'primary',
            'success',
            'warning',
            'info',
            'danger',
            'text'
          ].includes(val)
        }
      },
      size: {
        type: String as PropType<ComponentSize>,
        validator: isValidComponentSize,
      },
      icon: {
        type: String,
        default: '',
      },
      loading: Boolean,
      disabled: Boolean,
      plain: Boolean,
      autofocus: Boolean,
      round: Boolean,
      circle: Boolean,
    },
    
    methods: {
        
    },
});
</script>

<style scoped>
  .c-button {
    background: transparent;
    border: 1px solid black;
    line-height: 30px;
    height: 30px;
    cursor: pointer;
  }
  .c-button--primary {
    background: blue;
  }
</style>
