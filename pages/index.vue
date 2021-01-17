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
          
          <br>
          
          <p>
            {{ datas[0] }}
          </p>

          <b-form-input v-model="color_picker" type="color"></b-form-input>

          <div id="test"></div>
        </b-row>
      </b-container>
    </section>
  </div>
</template>

<script>
  import { mapMutations } from 'vuex';

  const FormData = require('form-data');

  export default {
    data() {
      return {
        file_krs: null,
        datas: [],
        color_picker: '#000'
      }
    },

    methods: {
      getData(event) {
        event.preventDefault();

        this.$nextTick(() => {
          this.$nuxt.$loading.start()
        });

        const file_krs_name = this.file_krs.name;

        const data_krs_form = new FormData();
        data_krs_form.append('file', this.file_krs, file_krs_name);
        
        this.$axios({
          method: 'post',
          url: 'https://krs-reader.herokuapp.com/post_krs',
          data: data_krs_form
        }).then((response) => {
          this.$nextTick(() => {
            setTimeout(() => this.$nuxt.$loading.finish(), 500);
          });

          console.log('Fetch KRS data success')
          this.datas.push(response.data)
          document.getElementById('test').style.background = this.color_picker;
        }).catch((err) => {
          this.$nextTick(() => {
            setTimeout(() => this.$nuxt.$loading.finish(), 500);
          });

          console.error(err)
        })
      }
    }
  }
</script>

<style>
  #test {
    width: 100px;
    height: 100px;
    border: 1px solid black;
  }
</style>
