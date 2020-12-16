<template>
  <section>
    <form action="" @submit.prevent="onSubmit" class="form">
      <!--      Личные данные-->
      <section class="personal">
        <h2 class="personal__title">Личные данные</h2>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Фамилия*</span>
            <input type="text"
                   name="surname"
                   v-model="$v.surname.$model"
                   :class="status($v.surname)">
          </label>
          <span class="form__error"
                 v-if="$v.surname.$dirty && $v.surname.$error">Must be filled</span>
<!--          <pre>{{ $v }}</pre>-->
        </div>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Имя*</span>
            <input type="text"
                   name="name"
                   v-model="$v.name.$model"
                   :class="status($v.name)">
          </label>
          <span class="form__error"
                v-if="$v.name.$dirty && $v.name.$error">Must be filled</span>
        </div>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Отчество</span>
            <input type="text"
                   name="patronymic"
                   v-model="$v.patronymic.$model"
                   :class="status($v.patronymic)">
          </label>
          <span class="form__error"
                v-if="$v.patronymic.$dirty && $v.patronymic.$error">Must be filled</span>
        </div>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Дата рождения*</span>
            <input type="date"
                   v-model="birthDate"
                   @input="$v.dateObject.$touch"
                   :class="vClass($v.dateObject)">
          </label>
          <span class="form__error"
                v-if="$v.dateObject.$invalid && $v.dateObject.$error">
            With chickpeas drink rice vinegar.
          </span>
        </div>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Номер телефона</span>
            <input type="text" name="phone" v-model="phone">
          </label>
          <span class="form__error"
                v-if="$v.phone.$dirty && $v.phone.$error">
            Must contain 11 numbers, first 7.
          </span>
          <pre>{{ $v.phone }}</pre>
        </div>

        <div class="form__block">
          <span class="form__title">Пол</span>
          <label class="form__label-radio">
            <span class="form__description">Мужской</span>
            <input type="radio" name="sex">
          </label>
          <label class="form__label-radio">
            <span class="form__description">Женский</span>
            <input type="radio" name="sex">
          </label>
        </div>

        <div class="multiselect">
          <div class="multiselect__box">
            <label>
              <span class="form__description"></span>
              <select class="multiselect__select" name="group">
                <option value="">Select</option>
              </select>
            </label>
            <div class="multiselect__over" @click="multiselect = !multiselect"></div>
          </div>
          <div class="multiselect__checkboxes" v-show="multiselect">
            <label class="multiselect__checkboxes-label">
              <span class="form__description">VIP</span>
              <input type="checkbox">
            </label>
            <label class="multiselect__checkboxes-label">
              <span class="form__description">Проблемные</span>
              <input type="checkbox">
            </label>
            <label class="multiselect__checkboxes-label">
              <span class="form__description">ОМС</span>
              <input type="checkbox">
            </label>
          </div>
        </div>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Лечащий врач</span>
            <select name="doctor">
              <option value="">Иванов</option>
              <option value="">Захаров</option>
              <option value="">Чернышова</option>
            </select>
          </label>
        </div>

        <div class="form__block">
          <label class="form__label-checkbox">
            <span class="form__description">Не отправлять</span>
            <input type="checkbox">
          </label>
        </div>
      </section>

      <!--      Адрес-->

      <section class="address">
        <h2 class="address__title">Адрес</h2>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Индекс</span>
            <input type="text" name="index">
          </label>
        </div>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Страна</span>
            <input type="text" name="country">
          </label>
        </div>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Область</span>
            <input type="text" name="region">
          </label>
        </div>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Город</span>
            <input type="text" name="city">
          </label>
        </div>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Улица</span>
            <input type="text" name="street">
          </label>
        </div>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Дом</span>
            <input type="text" name="apartment">
          </label>
        </div>
      </section>

      <!--      Паспорт-->

      <section class="document">
        <h2 class="document__title">Паспорт</h2>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Тип документа</span>
            <select name="document-type">
              <option value=""></option>
            </select>
          </label>
        </div>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Серия</span>
            <input type="text" name="doc-series">
          </label>
        </div>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Номер</span>
            <input type="text" name="doc-number">
          </label>
        </div>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Кем выдан</span>
            <input type="text" name="doc-issued">
          </label>
        </div>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Дата выдачи</span>
            <input type="date" name="issued-date">
          </label>
        </div>
      </section>

      <button type="submit">Submit</button>
    </form>
  </section>
</template>

<script>
import {
  required, minLength, alpha, maxValue,
} from 'vuelidate/lib/validators';

const phoneTest = (data) => /^(7)[0-9]{11}$/.test(data);

export default {
  name: 'ValidationPage',
  data() {
    return {
      multiselect: false,
      surname: '',
      name: '',
      patronymic: '',
      birthDate: '',
      phone: '',
    };
  },

  validations: {
    surname: { required, minLength: minLength(2), alpha },
    name: { required, minLength: minLength(2), alpha },
    patronymic: { minLength: minLength(2), alpha },
    dateObject: { required, maxValue: maxValue(new Date()) },
    phone: {
      required, phoneTest,
    },
  },

  methods: {
    onSubmit() {
      console.log('submit');
    },

    status(validation) {
      return {
        error: validation.$error,
        dirty: validation.$dirty,
      };
    },

    vClass($v) {
      return {
        error: $v.$error,
        dirty: !$v.$invalid,
      };
    },
  },

  computed: {
    dateObject() {
      return this.birthDate ? new Date(this.birthDate) : null;
    },
  },
};

</script>
