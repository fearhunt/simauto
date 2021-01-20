<template>
  <div>
    <section id="introduction" class="simauto-border-radius bg-primary-simauto">
      <b-container class="h-100">
        <b-row class="align-items-center h-100">
          <b-col class="d-none d-md-block">
            brand
          </b-col>

          <b-col class="text-center">
            <h1 class="title text-white">
              SimAuto
            </h1>

            <h2 class="subtitle">
              Generator jadwal KRS-mu menjadi urut dalam bentuk foto dan integrasi dengan Google Calendar
            </h2>

            <button class="btn btn-secondary-simauto">
              Upload PDF
            </button>
          </b-col>
        </b-row>
      </b-container>
    </section>

    <section id="how-it-works" class="simauto-border-radius">
      <b-container>
        <b-row>
          <b-col cols="12" class="text-center mb-2">
            <p class="brief-title">
              <span class="text-secondary-simauto">SimAuto</span>
              <span> > </span>
              <span class="text-primary-simauto">How It Works</span>
            </p>

            <h1 class="title">
              How It Works
            </h1>

            <h2 class="subtitle">
              Lorem ipsum dolor jamet.
            </h2>
          </b-col>

          
        </b-row>
      </b-container>
    </section>

    <section>
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
  #introduction {
    height: calc(108vh + 4rem);
    padding-top: 12rem;
  }

  #test {
    width: 100px;
    height: 100px;
    border: 1px solid black;
  }
</style>
