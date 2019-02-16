<template>
  <transition name="Modal">
    <div class="overlay">
      <div class="modal">
        <!--<span v-for="user in users" class="user" :key="user.id">{{user.name}}</span>-->
        <h4>Добавление пользователя</h4>
        <form id="form" v-on:submit.prevent="saveUser">

          <div class="form__element">
            <label>Имя</label><input type="text" v-model="newUser.name" placeholder="">
            <p class="error" v-show="!validation.name">Укажите имя</p>
          </div>

          <div class="form__element">
            <label>Телефон</label><input type="tel" v-model="newUser.phone" placeholder="">
            <p class="error" v-show="!validation.phone">Укажите корректный номер</p>
          </div>

          <select v-model="newUser.boss">
            <option disabled value="">Выберите начальника</option>
            <option v-for="user in users">{{user.name}}</option>
          </select>
          <v-button type="submit">Сохранить</v-button>
        </form>
        <span class="modal__close" v-on:click="closeModal"><svg version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 16 16" style="enable-background:new 0 0 16 16;" xml:space="preserve"><g><g><path class="fill" d="M16,8c0,0.5-0.5,1-1,1H9v6c0,0.5-0.5,1-1,1s-1-0.5-1-1V9H1C0.5,9,0,8.5,0,8s0.5-1,1-1h6V1c0-0.5,0.5-1,1-1s1,0.5,1,1v6h6C15.5,7,16,7.5,16,8z"></path></g></g></svg></span>
      </div>
    </div>
  </transition>
</template>

<script>

  import Button from './Button.vue';
  import Input from './Input.vue';
export default {

  name: 'modal',

  components: {
    'v-button': Button,
    'v-input': Input
  },

  props: ["users"],

  data: function () {
    return {
      newUser: {
        name: '',
        phone: '',
        boss: ''
        },
      }
  },

  computed: {

    validation: function () {
      const phoneRE = /^((\+7|7|8)+([0-9]){10})$/gm;
      return {
        name: !!this.newUser.name.trim(),
        phone: phoneRE.test(this.newUser.phone)
      }
    },
    isValid: function () {
      var validation = this.validation
      return Object.keys(validation).every(function (key) {
        return validation[key]
      })
    }

  },

  methods: {

    saveUser: function () {

      let newUser = {
        name: '',
        phone: '',
        id: ''
      };

      if(this.isValid) {
        newUser = {
          name: this.newUser.name,
          phone: this.newUser.phone,
          boss: this.newUser.boss,
          id: this.newUser.id,
        };

        if(this.newUser.boss) {
          debugger;
          this.$parent.$emit('addUserWithBoss', newUser);
        } else {
          debugger;
          this.$parent.$emit('addUser', newUser);
        }

       this.closeModal();
      }
    },

    closeModal: function () {
      this.newUser.name = '';
      this.newUser.phone = '';
      this.newUser.boss = '';

      this.$parent.$emit('closeModal');
    }
    // isValid: function () {
    //   var validation = this.validation;
    //   return Object.keys(validation).every(function (key) {
    //     /* return validation[key] */
    //     return true
    //   })
    // }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .overlay {
    background-color: rgba(0, 0, 0, 0.5);
    width: 100%;
    height: 100%;
    z-index: 9998;
    position: fixed;
    top: 0;
    left: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: opacity .3s ease;
  }

  .modal {
    box-sizing: border-box;
    background-color: #fff;
    width: 400px;
    min-height: 300px;
    padding: 30px 30px ;
    box-shadow: 0 2px 8px rgba(0, 0, 0, .33);
    transition: all .5s ease;
    position: relative;
  }

  .modal-enter {
    opacity: 0;
  }

  .modal-leave-active {
    opacity: 0;
  }

  .modal-enter .overlay,
  .modal-leave-active .overlay {
    -webkit-transform: scale(1.1);
    transform: scale(1.1);
  }

  .modal__close {
    width: 25px;
    height: 25px;
    position: absolute;
    top: 20px;
    right: 20px;
    transform: rotate(45deg);
    cursor: pointer;
  }

  .modal__close svg .fill {
    fill: #27b99a;
  }

  form {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    align-items: center;
  }

  .form__element {
    width: 100%;
    position: relative;
    display: flex;
    align-items: center;
    margin-bottom: 20px;
  }

  .error {
    position: absolute;
    color: red;
    font-size: 12px;
    top: 35px;
    right: 0;
  }

  label {
    width: 30%;
    text-align: left;
    margin-bottom: 20px;
  }

  input {
    width: 60%;
    padding: 10px 15px;
    margin-bottom: 20px;
  }

  h4 {
    text-align: left;
    margin-top: 0;
  }


</style>
