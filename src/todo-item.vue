<template>
  <span>
    {{ item.text }}
    <button v-on:click="$emit('remove')">X</button>
  </span>
</template>

<script>
  export default {
    props: {
      item: Object
    }
  }
</script>