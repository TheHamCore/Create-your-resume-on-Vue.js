<template>
    <div class="card card-w70">
        <h3 v-if="informationArray.length === 0">Добавьте первый блок, чтобы увидеть результат</h3>
        
        <div v-else v-for="(info, i) in informationArray" :key="i">
          <app-title v-if="info.typeValue === 'title'" :title="info.textValue"></app-title>
          <app-avatar v-else-if="info.typeValue === 'avatar'" :avatar="info.textValue"></app-avatar>
          <app-subtitle v-else-if="info.typeValue === 'subtitle'" :subtitle="info.textValue"></app-subtitle>
          <app-text v-else-if="info.typeValue === 'text'" :text="info.textValue"></app-text>
        </div>
    </div>
</template>

<script>
import AppTitle from './App-title'
import AppSubtitle from './App.subtitle'
import AppAvatar from './App-avatar'
import AppText from './App-text'

export default {
  name: 'App-display',
  components: {
    AppTitle,
    AppSubtitle,
    AppAvatar,
    AppText
  },
  props: {
    informationArray: {
      type: Array,
      required: true
    },
    currentType: {
      type:String
    }
  },
}
</script>

<style>

</style>