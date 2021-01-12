<template>
  <div>
    <section id="introduction">
      <b-container>
        <b-row>
          <b-form @submit="getData">
            <b-form-file
              v-model="file_krs"
              placeholder="Cek KRS"
              drop-placeholder="Taruh KRS"
            ></b-form-file>

            <b-button type="submit">Check</b-button>
          </b-form>
        </b-row>
      </b-container>
    </section>
  </div>
</template>

<script>
  import axios from 'axios';

  const FormData = require('form-data');

  export default {
    data() {
      return {
        file_krs: null
      }
    },

    methods: {
      getData(event) {
        event.preventDefault();

        const file_krs_name = this.file_krs.name;

        const data_krs = new FormData();
        data_krs.append('file', this.file_krs, file_krs_name);

        axios({
          method: 'post',
          url: 'https://krs-reader.herokuapp.com/post_krs',
          data: data_krs
        }).then((response) => {
          console.log(response.data)
        }).catch((err) => {
          console.error(err)
        })
      }
    }
  }
</script>

<style>

</style>
