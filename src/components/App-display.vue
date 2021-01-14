<template>
    <div class="card card-w70">
        <h3 v-if="informationArray.length === 0">Добавьте первый блок, чтобы увидеть результат</h3>
        
        <div v-else v-for="info in informationArray" :key="info.id">
          <component 
            :is="info.typeValue" 
            :info="info.textValue"
          ></component>
          <!-- <app-title v-if="info.typeValue === 'title'" :title="info.textValue"></app-title>
          <app-avatar v-else-if="info.typeValue === 'avatar'" :avatar="info.textValue"></app-avatar>
          <app-subtitle v-else-if="info.typeValue === 'subtitle'" :subtitle="info.textValue"></app-subtitle>
          <app-text v-else-if="info.typeValue === 'text'" :text="info.textValue"></app-text> -->
        </div>
    </div>
</template>

<script>
import AppDisplayTitle from './App-display-title'
import AppDisplaySubtitle from './App-display-subtitle'
import AppDisplayAvatar from './App-display-avatar'
import AppDisplayText from './App-display-text'

export default {
  name: 'App-display',
  components: {
    AppDisplayTitle,
    AppDisplaySubtitle,
    AppDisplayAvatar,
    AppDisplayText
  },
  props: {
    informationArray: {
      type: Array,
      required: true
    }
  },
}
</script>

<style>

</style>