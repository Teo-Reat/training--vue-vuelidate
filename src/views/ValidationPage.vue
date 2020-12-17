<template>
  <section>
    <form action="" class="form">
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
                v-if="$v.surname.$dirty && $v.surname.$error">
            Must be filled
          </span>
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
          <pre>{{ $v.name }}</pre>
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
            <input type="text" name="phone" v-model="$v.phone.$model" :class="status($v.phone)">
          </label>
          <span class="form__error"
                v-if="$v.phone.$dirty && $v.phone.$error">
            Must contain 11 numbers, first 7.
          </span>
        </div>

        <div class="form__block">
          <span class="form__title">Пол</span>
          <label class="form__label-radio">
            <span class="form__description-radio">Мужской</span>
            <input class="form__radio" type="radio" name="sex">
          </label>
          <label class="form__label-radio">
            <span class="form__description-radio">Женский</span>
            <input class="form__radio" type="radio" name="sex">
          </label>
        </div>

        <div class="multiselect">
          <div class="multiselect__box">
            <label>
              <span class="form__description"></span>
              <select class="multiselect__select" name="group">
                <option value="">Группа клиентов</option>
              </select>
            </label>
            <div class="multiselect__over" @click="multiselect = !multiselect"></div>
          </div>
          <div class="multiselect__checkboxes" v-show="multiselect">
            <label class="multiselect__checkboxes-label">
              <input class="multiselect__checkbox" type="checkbox" name="group-vip">
              <span class="multiselect__description">VIP</span>
            </label>
            <label class="multiselect__checkboxes-label">
              <input class="multiselect__checkbox" type="checkbox" name="group-problem">
              <span class="multiselect__description">Проблемные</span>
            </label>
            <label class="multiselect__checkboxes-label">
              <input class="multiselect__checkbox" type="checkbox" name="group-oms">
              <span class="multiselect__description">ОМС</span>
            </label>
          </div>
        </div>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Лечащий врач</span>
            <select class="form__select" name="doctor">
              <option value="">Иванов</option>
              <option value="">Захаров</option>
              <option value="">Чернышова</option>
            </select>
          </label>
        </div>

        <div class="form__block">
          <label class="form__label-checkbox">
            <input type="checkbox" name="do-not-send">
            <span class="form__description-checkbox">Не отправлять</span>
          </label>
        </div>
      </section>

      <!--      Адрес-->

      <section class="address">
        <h2 class="address__title">Адрес</h2>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Индекс</span>
            <input type="text"
                   name="index"
                   v-model="$v.index.$model"
                   :class="status($v.index)">
          </label>
          <span class="form__error"
                v-if="$v.index.$dirty && $v.index.$error">Must be filled</span>
        </div>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Страна</span>
            <input type="text"
                   name="country"
                   v-model="$v.country.$model"
                   :class="status($v.country)">
          </label>
          <span class="form__error"
                v-if="$v.country.$dirty && $v.country.$error">Must be filled</span>
        </div>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Область</span>
            <input type="text"
                   name="region"
                   v-model="$v.region.$model"
                   :class="status($v.region)">
          </label>
          <span class="form__error"
                v-if="$v.region.$dirty && $v.region.$error">Must be filled</span>
        </div>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Город*</span>
            <input type="text"
                   name="city"
                   v-model="$v.city.$model"
                   :class="status($v.city)">
            <span class="form__error"
                  v-if="$v.city.$dirty && $v.city.$error">Must be filled</span>
          </label>
        </div>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Улица</span>
            <input type="text"
                   name="street"
                   v-model="$v.street.$model"
                   :class="status($v.street)">
          </label>
          <span class="form__error"
                v-if="$v.street.$dirty && $v.street.$error">Must be filled</span>
        </div>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Дом</span>
            <input type="text"
                   name="apartment"
                   v-model="$v.apartment.$model"
                   :class="status($v.apartment)">
          </label>
          <span class="form__error"
                v-if="$v.apartment.$dirty && $v.apartment.$error">Must be filled</span>
        </div>
      </section>

      <!--      Документ-->

      <section class="document">
        <h2 class="document__title">Паспорт</h2>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Тип документа</span>
            <select class="form__select" name="document-type" v-model="selectDoc">
              <option value="passport">Паспорт</option>
              <option value="birth-doc">Свидетельство о рождении</option>
              <option value="driver-license">Водительское удостоверение</option>
            </select>
          </label>
        </div>

        <!--        Паспорт-->

        <div class="form__passport" v-if="selectDoc === 'passport'">
          <div class="form__block">
            <label class="form__label">
              <span class="form__description">Серия</span>
              <input type="text"
                     name="passport-serial"
                     v-model="$v.passportSerial.$model"
                     :class="status($v.passportSerial)">
            </label>
            <span class="form__error"
                  v-if="$v.passportSerial.$dirty && $v.passportSerial.$error">Must be filled</span>
          </div>

          <div class="form__block">
            <label class="form__label">
              <span class="form__description">Номер</span>
              <input type="text"
                     name="passport-number"
                     v-model="$v.passportNumber.$model"
                     :class="status($v.passportNumber)">
            </label>
            <span class="form__error"
                  v-if="$v.passportNumber.$dirty && $v.passportNumber.$error">Must be filled</span>
          </div>
        </div>

        <!--        Свидетельство-->

        <div class="form__birth-doc" v-if="selectDoc === 'birth-doc'">
          <div class="form__block">
            <label class="form__label">
              <span class="form__description">Серия</span>
              <input type="text"
                     name="birth-doc-serial"
                     v-model="$v.birthDocSerial.$model"
                     :class="status($v.birthDocSerial)">
            </label>
            <span class="form__error"
                  v-if="$v.birthDocSerial.$dirty && $v.birthDocSerial.$error">Must be filled</span>
          </div>

          <div class="form__block">
            <label class="form__label">
              <span class="form__description">Номер</span>
              <input type="text"
                     name="birth-doc-number"
                     v-model="$v.birthDocNumber.$model"
                     :class="status($v.birthDocNumber)">
            </label>
            <span class="form__error"
                  v-if="$v.birthDocNumber.$dirty && $v.birthDocNumber.$error">Must be filled</span>
          </div>
        </div>

        <!--        Водительское удостоверение-->

        <div class="form__driver-license" v-if="selectDoc === 'driver-license'">
          <div class="form__block">
            <label class="form__label">
              <span class="form__description">Серия</span>
              <input type="text"
                     name="driver-license-serial"
                     v-model="$v.driverLicenseSerial.$model"
                     :class="status($v.driverLicenseSerial)">
            </label>
            <span class="form__error"
                  v-if="$v.driverLicenseSerial.$dirty && $v.driverLicenseSerial.$error">
              Must be filled
            </span>
          </div>

          <div class="form__block">
            <label class="form__label">
              <span class="form__description">Номер</span>
              <input type="text"
                     name="driver-license-number"
                     v-model="$v.driverLicenseNumber.$model"
                     :class="status($v.driverLicenseNumber)">
            </label>
            <span class="form__error"
                  v-if="$v.driverLicenseNumber.$dirty && $v.driverLicenseNumber.$error">
              Must be filled
            </span>
          </div>
        </div>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Кем выдан</span>
            <input type="text"
                   name="driver-license-number"
                   v-model="$v.docIssued.$model"
                   :class="status($v.docIssued)">
          </label>
          <span class="form__error"
                v-if="$v.docIssued.$dirty && $v.docIssued.$error">
              Must be filled
            </span>
        </div>

        <div class="form__block">
          <label class="form__label">
            <span class="form__description">Дата выдачи*</span>
            <input type="date"
                   v-model="issuedDate"
                   @input="$v.issuedDateComp.$touch"
                   :class="vClass($v.issuedDateComp)">
          </label>
          <span class="form__error"
                v-if="$v.issuedDateComp.$invalid && $v.issuedDateComp.$error">
            With chickpeas drink rice vinegar.
          </span>
        </div>
      </section>

      <button type="submit">Submit</button>
    </form>
  </section>
</template>

<script>
import {
  required, minLength, maxLength, alpha, maxValue, numeric, alphaNum, or,
} from 'vuelidate/lib/validators';

const phoneTest = (data) => /^(7)[0-9]{11}$/.test(data);
const cyrillic = (val) => /^[а-яё]*$/i.test(val);
const cyrillicNum = (val) => /^[а-яё0-9]*$/i.test(val);

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
      index: '',
      country: '',
      region: '',
      city: '',
      street: '',
      apartment: '',
      selectDoc: 'passport',
      passportSerial: '',
      passportNumber: '',
      birthDocSerial: '',
      birthDocNumber: '',
      driverLicenseSerial: '',
      driverLicenseNumber: '',
      docIssued: '',
      issuedDate: '',
    };
  },

  validations: {
    surname: {
      required, minLength: minLength(2), alphaPlusCyrillic: or(alpha, cyrillic),
    },
    name: {
      required, minLength: minLength(2), alphaPlusCyrillic: or(alpha, cyrillic),
    },
    patronymic: { minLength: minLength(2), alphaPlusCyrillic: or(alpha, cyrillic) },
    dateObject: { required, maxValue: maxValue(new Date()) },
    phone: { required, phoneTest },
    index: { minLength: minLength(6), maxLength: maxLength(6), numeric },
    country: { minLength: minLength(2), alphaPlusCyrillic: or(alpha, cyrillic) },
    region: { minLength: minLength(2), alphaPlusCyrillic: or(alpha, cyrillic) },
    city: { required, minLength: minLength(2), alphaPlusCyrillic: or(alpha, cyrillic) },
    street: { minLength: minLength(2), alphaPlusCyrillic: or(alpha, cyrillic) },
    apartment: { alphaPlusCyrillicPlusNumbers: or(alphaNum, cyrillicNum) },
    passportSerial: { minLength: minLength(4), maxLength: maxLength(4), numeric },
    passportNumber: { minLength: minLength(6), maxLength: maxLength(6), numeric },
    birthDocSerial: {
      minLength: minLength(2),
      maxLength: maxLength(2),
      alphaPlusCyrillicPlusNumbers: or(alphaNum, cyrillicNum),
    },
    birthDocNumber: { minLength: minLength(8), maxLength: maxLength(8), numeric },
    driverLicenseSerial: { minLength: minLength(2), maxLength: maxLength(2), alpha },
    driverLicenseNumber: { minLength: minLength(8), maxLength: maxLength(8), numeric },
    docIssued: { alphaPlusCyrillic: or(alpha, cyrillic) },
    issuedDateComp: { required, maxValue: maxValue(new Date()) },
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

    issuedDateComp() {
      return this.issuedDate ? new Date(this.issuedDate) : null;
    },
  },
};

</script>
