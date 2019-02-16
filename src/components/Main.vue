<template>
    <div class="wrapper">

        <v-button class="" v-on:click.native="showModal = true">Добавить</v-button>
        <table>
            <tr>
                <th v-on:click="sortByName()">Имя</th>
                <th v-on:click="sortByPhone()">Телефон</th>
            </tr>
            <template v-for="user in users" class="user" >
                <tr :key="user.id">
                    <td>{{user.name}}</td>
                    <td>{{user.phone}} <v-button class="remove" v-on:click.native="removeUser(user)"><svg version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 22 22" style="enable-background:new 0 0 22 22;" xml:space="preserve"><g><g><path class="fill" d="M16.1,3.6h-1.9V3.3c0-1.3-1-2.3-2.3-2.3h-1.7C8.9,1,7.8,2,7.8,3.3v0.2H5.9c-1.3,0-2.3,1-2.3,2.3v1.3c0,0.5,0.4,0.9,0.9,1v10.5c0,1.3,1,2.3,2.3,2.3h8.5c1.3,0,2.3-1,2.3-2.3V8.2c0.5-0.1,0.9-0.5,0.9-1V5.9C18.4,4.6,17.4,3.6,16.1,3.6z M9.1,3.3c0-0.6,0.5-1.1,1.1-1.1h1.7c0.6,0,1.1,0.5,1.1,1.1v0.2H9.1V3.3z M16.3,18.7c0,0.6-0.5,1.1-1.1,1.1H6.7c-0.6,0-1.1-0.5-1.1-1.1V8.2h10.6L16.3,18.7L16.3,18.7z M17.2,7H4.8V5.9c0-0.6,0.5-1.1,1.1-1.1h10.2c0.6,0,1.1,0.5,1.1,1.1V7z"></path></g><g><g><path class="fill" d="M11,18c-0.4,0-0.6-0.3-0.6-0.6v-6.8c0-0.4,0.3-0.6,0.6-0.6s0.6,0.3,0.6,0.6v6.8C11.6,17.7,11.4,18,11,18z"></path></g><g><path class="fill" d="M8,18c-0.4,0-0.6-0.3-0.6-0.6v-6.8C7.4,10.2,7.7,10,8,10c0.4,0,0.6,0.3,0.6,0.6v6.8C8.7,17.7,8.4,18,8,18z"></path></g><g><path class="fill" d="M14,18c-0.4,0-0.6-0.3-0.6-0.6v-6.8c0-0.4,0.3-0.6,0.6-0.6c0.4,0,0.6,0.3,0.6,0.6v6.8C14.6,17.7,14.3,18,14,18z"></path></g></g></g></svg></v-button></td>
                </tr>
                <template v-if="user.slaves">
                    <tr v-for="slave in user.slaves" class="slave">
                        <td><svg version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 482.9 482.9" style="enable-background:new 0 0 482.9 482.9;" xml:space="preserve"><g><g><path d="M239.7,260.2c0.5,0,1,0,1.6,0c0.2,0,0.4,0,0.6,0c0.3,0,0.7,0,1,0c29.3-0.5,53-10.8,70.5-30.5c38.5-43.4,32.1-117.8,31.4-124.9c-2.5-53.3-27.7-78.8-48.5-90.7C280.8,5.2,262.7,0.4,242.5,0h-0.7c-0.1,0-0.3,0-0.4,0h-0.6c-11.1,0-32.9,1.8-53.8,13.7c-21,11.9-46.6,37.4-49.1,91.1c-0.7,7.1-7.1,81.5,31.4,124.9C186.7,249.4,210.4,259.7,239.7,260.2z M164.6,107.3c0-0.3,0.1-0.6,0.1-0.8c3.3-71.7,54.2-79.4,76-79.4h0.4c0.2,0,0.5,0,0.8,0c27,0.6,72.9,11.6,76,79.4c0,0.3,0,0.6,0.1,0.8c0.1,0.7,7.1,68.7-24.7,104.5c-12.6,14.2-29.4,21.2-51.5,21.4c-0.2,0-0.3,0-0.5,0l0,0c-0.2,0-0.3,0-0.5,0c-22-0.2-38.9-7.2-51.4-21.4C157.7,176.2,164.5,107.9,164.6,107.3z"/><path d="M446.8,383.6c0-0.1,0-0.2,0-0.3c0-0.8-0.1-1.6-0.1-2.5c-0.6-19.8-1.9-66.1-45.3-80.9c-0.3-0.1-0.7-0.2-1-0.3c-45.1-11.5-82.6-37.5-83-37.8c-6.1-4.3-14.5-2.8-18.8,3.3c-4.3,6.1-2.8,14.5,3.3,18.8c1.7,1.2,41.5,28.9,91.3,41.7c23.3,8.3,25.9,33.2,26.6,56c0,0.9,0,1.7,0.1,2.5c0.1,9-0.5,22.9-2.1,30.9c-16.2,9.2-79.7,41-176.3,41c-96.2,0-160.1-31.9-176.4-41.1c-1.6-8-2.3-21.9-2.1-30.9c0-0.8,0.1-1.6,0.1-2.5c0.7-22.8,3.3-47.7,26.6-56c49.8-12.8,89.6-40.6,91.3-41.7c6.1-4.3,7.6-12.7,3.3-18.8c-4.3-6.1-12.7-7.6-18.8-3.3c-0.4,0.3-37.7,26.3-83,37.8c-0.4,0.1-0.7,0.2-1,0.3c-43.4,14.9-44.7,61.2-45.3,80.9c0,0.9,0,1.7-0.1,2.5c0,0.1,0,0.2,0,0.3c-0.1,5.2-0.2,31.9,5.1,45.3c1,2.6,2.8,4.8,5.2,6.3c3,2,74.9,47.8,195.2,47.8s192.2-45.9,195.2-47.8c2.3-1.5,4.2-3.7,5.2-6.3C447,415.5,446.9,388.8,446.8,383.6z"/></g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g></svg>{{slave.name}}</td>
                        <td>{{slave.phone}}</td>
                    </tr>
                </template>
            </template>



        </table>
        <v-modal v-if="showModal" v-bind:users="users"></v-modal>
    </div>
</template>

<script>

import Modal from './Modal.vue';
import Button from './Button.vue';
export default {


  components: {
    'v-modal': Modal,
    'v-button': Button
    },

  name: 'Main',
  props: {
    msg: String,
  },

    data: function () {
        return {
            users: [
                {
                    name: 'Василий',
                    phone: '+79993786244',
                    id: '0'
                },
                {
                    name: 'Ирина',
                    phone: '89913234567',
                    id: '1'
                },
                {
                    name: 'Борис',
                    phone: '+79952334456',
                    id: '2'
                },

            ],
            newUser: {
                name: '',
                phone: '',
            },

            showModal: false,

            isSortedByName: false
        }
    },

    mounted() {
      debugger;
        if (localStorage.users) {
            this.users = JSON.parse(localStorage.users);
        } else {
            localStorage.users = JSON.stringify(this.users)
        }

        this.$on('addUser', function(newUser) {
            this.users.push(newUser);

            this.users.forEach(function (user, index) {
                user.id = index
            });

            localStorage.users = JSON.stringify(this.users);
        });

        this.$on('addUserWithBoss', function(newUser) {
            debugger;
            this.users.forEach(function (user, index) {
                if(user.name === newUser.boss) {
                    debugger;
                    if(user.slaves) {
                        user.slaves.push(newUser);
                     } else {
                        user.slaves = [];
                        user.slaves.push(newUser);
                    }
                }
            });

            localStorage.users = JSON.stringify(this.users);
        });

        this.$on('closeModal', function() {
            this.showModal = false;
        })
    },

    methods: {
        sortByPhone: function() {
            debugger;
            if(!this.isSorted) {
                this.users.sort(function(a, b){
                    var nameA = a.phone.toLowerCase(), nameB = b.phone.toLowerCase();
                    if (nameA < nameB)
                        return -1;
                    if (nameA > nameB)
                        return 1;
                    return 0
                });
                this.isSorted = true;
            } else {
                this.users.sort(function(a, b){
                    var nameA = a.phone.toLowerCase(), nameB = b.phone.toLowerCase()
                    if (nameA > nameB)
                        return -1;
                    if (nameA < nameB)
                        return 1;
                    return 0
                });
                this.isSorted = false;
            }


        },

        sortByName: function() {
            debugger;
            if(!this.isSorted) {
                this.users.sort(function(a, b){
                    var nameA = a.name.toLowerCase(), nameB = b.name.toLowerCase();
                    if (nameA < nameB)
                        return -1;
                    if (nameA > nameB)
                        return 1;
                    return 0
                });
                this.isSorted = true;
            } else {
                this.users.sort(function(a, b){
                    var nameA = a.name.toLowerCase(), nameB = b.name.toLowerCase();

                    if (nameA > nameB)
                        return -1;
                    if (nameA < nameB)
                        return 1;
                    return 0
                });
                this.isSorted = false;
            }


        },

        removeUser: function (user) {

            this.users.splice(this.users.indexOf(user), 1);
            localStorage.users = JSON.stringify(this.users);
            // this.users = this.users.filter(user.id => user.id !== 2)
        }

    }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.wrapper {
    padding-left: 100px;
    width: 500px;
    display: flex;
    flex-direction: column;
}

    button {
    width: 130px;
}

h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}


ul {
    padding: 0;
}

.user {
    height: 30px;
    line-height: 30px;
    padding: 10px;
    border-top: 1px solid #eee;
    overflow: hidden;
    transition: all .25s ease;
}

.user:last-child {
    border-bottom: 1px solid #eee;
}

.v-enter, .v-leave-active {
    height: 0;
    padding-top: 0;
    padding-bottom: 0;
    border-top-width: 0;
    border-bottom-width: 0;
}

.errors {
    color: #f00;
}

table {
    margin-top: 30px;
    min-width: 400px;
    border: 1px solid #ccc;
    border-collapse: collapse;
    background-color: #fff;
}

td,th {
    line-height: 30px;
    max-width: 300px;
    border: 1px solid #ccc;
    padding: 5px 10px 5px 10px;
    text-align: left;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    position: relative;
}

th {
    cursor: pointer;
    user-select: none;
}

tr {
    position: relative;
}

.remove {
    position: absolute;
    opacity: 0.4;
    appearance: none;
    background: 0 0;
    border: 0;
    -webkit-box-shadow: none;
    box-shadow: none;
    outline: 0;
    cursor: pointer;
    height: 22px;
    width: 22px;
    top: 8px;
    right: 10px;
}

.remove:hover {
    opacity: 1;
    animation: shake 0.82s cubic-bezier(.36,.07,.19,.97) both;
}

.remove svg {
    width: 22px;
    height: 22px;
    position: absolute;
    top: calc(50% - 11px);
    left: calc(50% - 11px);
}
.remove svg fill {
    transition: .3s ease;
}

.remove:hover svg .fill {
    fill: #e85657;
    -webkit-animation: shake .3s;
    animation: shake .3s;
}

@keyframes shake {
    10%, 90% {
        transform: translate3d(-1px, 0, 0);
    }

    20%, 80% {
        transform: translate3d(1x, 0, 0);
    }

    30%, 50%, 70% {
        transform: translate3d(-2px, 0, 0);
    }

    40%, 60% {
        transform: translate3d(2px, 0, 0);
    }
}

.slave td:first-child {
    padding-left: 40px;
}
.slave td:first-child svg {
    width: 20px;
    height: 20px;
    position: absolute;
    left: 10px;
    top: 10px;
}
</style>
