<template>
    <div class="avatar">
        <img :src="info">
    </div>
</template>

<script>
export default {
  name: 'App-avatar',
  props: {
    info: {
      type: String
    }
  }     
}
</script>

<style>

</style>