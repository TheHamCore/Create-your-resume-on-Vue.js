<template>
  <div>
    <div class="container column">
      <form class="card card-w30">
        <div class="form-control">
          <label for="type">Тип блока</label>

          <select 
            v-model="currentType"
            id="type" 
          > 
            <option
              v-for="option in optionArray" 
              :key="option.value"
              :value="option.value"
            >
              {{ option.label }}
            </option>
            <!-- <option value="subtitle">Подзаголовок</option>
            <option value="avatar">Аватар</option>
            <option value="text">Текст</option> -->
          </select>
        </div>

        <div class="form-control">
          <label for="value">Значение</label>
          <textarea
            v-model="currentText"
            id="value" 
            rows="7"
            :placeholder='currentOption.text'
          >
          </textarea>
        </div>

        <button
          @click.prevent="addInfo"
          class="btn primary"
          :disabled="hasText"
        >
          Добавить
        </button>
      </form>

      <app-display
        :informationArray="informationArray"
      >
      </app-display>

    </div>
    
    <app-comments></app-comments>
    
  </div>
</template>

<script>
import AppDisplay from './components/App-display'
import AppComments from './components/App-comments'


export default {
  components: {
    AppDisplay,
    AppComments
  },
  data () {
    return {
      informationArray: [],
      currentType: 'app-display-title',
      currentText: '',
      optionArray: [
        {
          label: 'Заголовок',
          value: 'app-display-title',
          text: 'Укажите название вакансии, которую Вы ищите'
        },
        {
          label: 'Подзаголовок',
          value: 'app-display-subtitle',
          text:'Выберите названия подзаголовка (например: "опыт работы, хобби, личные качества")'
        },
        {
          label: 'Аватар',
          value: 'app-display-avatar',
          text: 'Вставьте в поле ссылку на Ваше фото'
        },
        {
          label: 'Текст',
          value: 'app-display-text',
          text: 'Напишите о своих достижениях'
        },
      ]
    }
  },
  methods: {
    addInfo () {
      this.informationArray.push({
        typeValue: this.currentType,
        textValue: this.currentText
      });

      this.currentText = '';
    },
  },
  computed: {
    hasText: vm => vm.currentText.length < 3,
    currentOption: vm => vm.optionArray.find(item => item.value === vm.currentType)
      // return vm.optionArray.find((item) => {
      //   if (item.value === vm.currentType) {
      //     return item
  }
}

</script>

<style>
  .avatar {
    display: flex;
    justify-content: center;
  }

  .avatar img {
    width: 150px;
    height: auto;
    border-radius: 50%;
  }
</style>
