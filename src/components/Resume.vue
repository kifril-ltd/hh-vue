<template>
  <div>
    <b-container class="my-5">
      <b-row>
        <b-col class="resume-form">
          <b-card border-variant="danger">
            <b-form>
              <b-form-group id='profession' label="Профессия:" label-for="profession-input">
                <b-form-input id="profession-input" v-model="resume.profession" placeholder="Профессия" required>
                </b-form-input>
              </b-form-group>

              <b-form-group id='city' label="Город:" label-for="city-input">
                <b-form-input id="city-input" v-model="resume.city" placeholder="Город" required>
                </b-form-input>
              </b-form-group>

              <b-form-group id='photo' label="Ссылка на фото:" label-for="photo-input">
                <b-form-input id="photo-input" v-model="resume.photo" placeholder="Ссылка на фото" type="url" required>
                </b-form-input>
              </b-form-group>

              <b-form-group id='ФИО' label="ФИО:" label-for="fio-input">
                <b-form-input id="fio-input" v-model="resume.fio" placeholder="ФИО" required>
                </b-form-input>
              </b-form-group>

              <b-form-group id='phone' label="Номер телефона:" label-for="phone-input">
                <b-form-input id="phone-input" v-model="resume.phone" placeholder="Номер телефона" type="tel" required>
                </b-form-input>
              </b-form-group>

              <b-form-group id='email' label="Email:" label-for="email-input">
                <b-form-input id="email-input" v-model="resume.email" placeholder="Email" type="email" required>
                </b-form-input>
              </b-form-group>

              <b-form-group id='birthday' label="Дата рождения:" label-for="birthday-input">
                <b-form-input id="birthday-input" v-model="resume.birthday" placeholder="Дата рождения" type="date"
                  required>
                </b-form-input>
              </b-form-group>

              <b-form-group id='education' label="Образование:" label-for="education-input">
                <b-form-input id="education-input" v-model="resume.education" placeholder="Образование" required>
                </b-form-input>
              </b-form-group>

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
            </b-form>
          </b-card>
        </b-col>
        <b-col class="resume-display">
          <b-card border-variant="danger">
            <b-row>
              <b-col cols="4" class="m-2">
                <b-avatar rounded="lg" size="200px" :src="avatar"></b-avatar>
              </b-col>
              <b-col>
                <h2>Основная информация</h2>
                <b-row class="mb-3">ФИО: {{ resume.fio }}</b-row>
                <b-row class="mb-3">Город: {{ resume.city }}</b-row>
                <b-row>Дата рождения: {{ resume.birthday }}</b-row>
              </b-col>
            </b-row>
            <b-card header="Контакты" class="mb-2">
              <b-row class="mb-3">Телефон: {{ resume.phone }}</b-row>
              <b-row>Email: {{ resume.email }}</b-row>
            </b-card>
            <b-card header="Образование" class="mb-2">
              <b-row class="mb-3">Университет: {{ resume.education }}</b-row>
              <b-row>Профессия: {{ resume.profession }}</b-row>
            </b-card>
            <b-card header="Работа">
              <b-row class="mb-3">Желаемая зарплата: {{ resume.salary }}</b-row>
              <b-row class="mb-3">Ключевые навыки: {{ resume.skills }}</b-row>
              <b-row>О себе: {{ resume.description }}</b-row>
            </b-card>
          </b-card>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
  export default {
    name: 'Resume',
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
          education: '',
          salary: '',
          skills: '',
          description: ''
        },
        imageError: false,
        defaultAvatar: require('@/assets/avatar.png')
      }
    },
    computed: {
      avatar() {
        return this.imageError ? this.defaultAvatar : this.resume.photo
      }
    }
  }
</script>

<style scoped>
  .resume-photo {
    width: 250px;
    height: auto;
  }
</style>