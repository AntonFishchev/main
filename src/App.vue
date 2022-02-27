<template>
  <FishchevComponent />
  <Vyatsu :results='results'/>
  <!-- <Autorization title='Авторизация'/> -->
  <LoginWindow />
</template>

<script>
import FishchevComponent from 'fishchev-component';
import Vyatsu from 'vyatsu-fishchev';
import axios from 'axios';
// import Autorization from 'autorization-fishchev';
import LoginWindow from './components/LoginWindow.vue';

const url = 'http://localhost:8080/admission/';

export default {
  name: 'MainApp',
  components: {
    FishchevComponent,
    Vyatsu,
    LoginWindow,
  },
  data() {
    return { FishchevComponent, results: [] };
  },
  mounted() {
    axios
      .get(url)
      .then((response) => {
        console.log(response);
        this.results = response.data;
      })
      .catch((error) => console.log(error));
  },
};
</script>

<style>
</style>
