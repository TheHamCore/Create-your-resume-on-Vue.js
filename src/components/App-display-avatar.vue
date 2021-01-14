<template>
    <div class="avatar">
        <img :src="info">
    </div>
</template>

<script>
export default {
  name: 'App-display-avatar',
  props: {
    info: {
      type: String
    }
  }     
}
</script>

<style>

</style>