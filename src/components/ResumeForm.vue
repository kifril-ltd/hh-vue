<template>
 
   
          <b-card border-variant="danger">
            <b-form>
              <b-card header="Основная информация" class="mb-2">
               
               <BInput 
                  id="fio-input"
                  label="ФИО"
                  placeholder="Введите свое ФИО"
                  :value="resume.fio"
                  @input="this.resume.fio = $event"
                  
                />

                <b-form-group id='city' label="Город:" label-for="city-input">
                  <b-form-input id="city-input" v-model="resume.city" placeholder="Город" required>
                  </b-form-input>
                </b-form-group>

                <b-form-group id='birthday' label="Дата рождения:" label-for="birthday-input">
                  <b-form-input id="birthday-input" v-model="resume.birthday" placeholder="Дата рождения" type="date"
                    required>
                  </b-form-input>
                </b-form-group>

                <b-form-group id='photo' label="Ссылка на фото:" label-for="photo-input">
                  <b-form-input id="photo-input" v-model="resume.photo" placeholder="Ссылка на фото" type="url"
                    required>
                  </b-form-input>
                </b-form-group>
              </b-card>

              <b-card header="Контакты" class="mb-2">
                <!-- <BInput
                  id="phone-input"
                  label="Телефон"
                  placeholder="Введите свой номер телефона"
                
                /> -->
              


                <b-form-group id='email' label="Email:" label-for="email-input">
                  <b-form-input id="email-input" v-model="resume.email" placeholder="Email" type="email" required>
                  </b-form-input>
                </b-form-group>
              </b-card>
              <b-card header="Образование" class="mb-2">
                <b-form-group id='education' label="Образование:" label-for="education-input">
                  <b-form-select v-model="resume.education.level" :options="educationLevelOptions"></b-form-select>
      
                </b-form-group>

                <b-form-group id='profession' label="Профессия:" label-for="profession-input">
                  <b-form-input id="profession-input" v-model="resume.profession" placeholder="Профессия" required>
                  </b-form-input>
                </b-form-group>
              </b-card>
              <b-card header="Работа">
                <b-form-group id='salary' label="Желаемая зарплата:" label-for="salary-input">
                  <b-form-input id="salary-input" v-model="resume.salary" placeholder="Желаемая зарплата" type="number"
                    required>
                  </b-form-input>
                </b-form-group>

                <b-form-group id='skills' label="Ключевые навыки:" label-for="skills-input">
                  <b-form-input id="skills-input" v-model="resume.skills" placeholder="Ключевые навыки" required>
                  </b-form-input>
                </b-form-group>

                <b-form-group id='description' label="O себе:" label-for="description-input">
                  <b-form-textarea id="description-input" v-model="resume.description" placeholder="О себе..." rows="3"
                    max-rows="6"></b-form-textarea>
                </b-form-group>
              </b-card>
            </b-form>
          </b-card>
       
</template>

<script>
  import BInput from './BInput.vue'
  export default {
    name: 'ResumeForm',
    components: {
      BInput
    },
    data() {
      return {
        resume: {
          profession: '',
          city: '',
          photo: undefined,
          fio: '123',
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