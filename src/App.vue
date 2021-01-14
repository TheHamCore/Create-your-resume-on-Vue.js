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
            :placeholder='ee'
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
        :currentType="currentType"
        :currentText="currentText"
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
          textplaceholder: 'Укажите название вакансии, которую Вы ищите'
        },
        {
          label: 'Подзаголовок',
          value: 'app-display-subtitle',
          textplaceholder:'Выберите названия подзаголовка (например: "опыт работы, хобби, личные качества")'
        },
        {
          label: 'Аватар',
          value: 'app-display-avatar',
          textplaceholder: 'Вставьте в поле ссылку на Ваше фото'
        },
        {
          label: 'Текст',
          value: 'app-display-text',
          textplaceholder: 'Напишите о своих достижениях'
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
    explanation (vm) {
      switch(vm.currentType) {
        case 'app-title': 
          return 'Укажите название вакансии, которую Вы ищите';
        case 'app-subtitle': 
          return 'Выберите названия подзаголовка (например: "опыт работы, хобби, личные качества")';
        case 'app-avatar': 
          return 'Вставьте в поле ссылку на Ваше фото';
        case 'app-text': 
          return 'Напишите о своих достижениях';
        default:
          return ''
      }
    }
  },
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
