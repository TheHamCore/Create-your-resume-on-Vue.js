<template>
    <div class="avatar">
        <img :src="avatar">
    </div>
</template>

<script>
export default {
  name: 'App-avatar',
  props: {
    avatar: {
      type: String
    }
  }     
}
</script>

<style>

</style>