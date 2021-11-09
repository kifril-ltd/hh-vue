<template>
  <div>
    <b-container class="my-5">
      <b-row>
        <b-col class="resume-form">
          <ResumeForm />
        </b-col>
        <b-col>
          <ResumeShow 
            :resume="resume"/>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
  import ResumeShow from './ResumeShow.vue'
  import ResumeForm from './ResumeForm.vue'
  export default {
    name: 'Resume',
    components: {
      ResumeShow,
      ResumeForm
    },
    data() {
      return {
        resume: {
          profession: '',
          city: '',
          photo: undefined,
          fio: '',
          phone: '',
          email: '',
          birthday: '',
          education: {
            level: '', 
            university: '',
            faculty: '',
            specialization: '',
            gradYear: '',
          },
          salary: '',
          skills: '',
          description: ''
        },

        phoneRules: [
            {rule: /^\d$/i, message: 'Телефон должен состоять только из цифр'},
            {rule: /^.{6,10}$/i, message: 'Телефон должен содержать от 6 до 10 символов'}
        ],
        educationLevelOptions: [
          { value: null, text: 'Выберете уровень образования' },
          { value: 'Среднее', text: 'Среднее' },
          { value: 'Среднее специальное', text: 'Среднее специальное' },
          { value: 'Неоконченное высшее', text: 'Неоконченное высшее' },
          { value: 'Высшее', text: 'Высшее' },
        ]
      }
    },
    computed: {
      avatar() {
        return this.imageError ? this.defaultAvatar : this.resume.photo;
      },

      phoneCheck() {
        const regex = /^\d{6,10}$/i;
        return regex.test(this.resume.phone)
      }
    }
  }
</script>