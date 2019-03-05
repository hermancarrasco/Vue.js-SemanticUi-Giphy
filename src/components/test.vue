<template>
  <div>
    <form @submit.prevent="buscar">
    <div class="ui icon input center aligned">
      <input type="text" placeholder="Buscar..." v-model="busqueda">
      <i class="inverted circular search link icon"></i>
    </div>
    </form>
    <br><br>

  <div class="ui grid">

    <div class="four wide column" v-for="(gif, index) in gifs" :key="index">
    <div class="ui card">
      <div class="image">
        <img :src="gif.images.preview_gif.url">
      </div>
      <div class="content">
        <a class="header">{{gif.title}}</a>
        <div class="meta">
          <span class="date">{{gif.import_datetime}}</span>
        </div>
        <div class="description" v-if="gif.source_tld">
          Fuente: {{gif.source_tld}}
        </div>
        <div class="description" v-if="!gif.source_tld">
          Fuente: No Definida
        </div>
      </div>
    </div>
    </div>
  </div>
  </div>

</template>

<script>

  import axios from 'axios'

export default {
  name: 'test',
  props: {
    msg: String
  },
  data(){
    return {
      gifs: '',
      busqueda: ''
    }
  },
  mounted(){
    axios.get('https://api.giphy.com/v1/gifs/search?api_key=9beVqhXkFy8MK8HMXxa9ov261kZvUQfn&lang=es&q=gato')
            .then(res => {
              console.log(res)
              this.gifs = res.data.data
            })
  },
  methods:{
    buscar(){
      axios.get('https://api.giphy.com/v1/gifs/search?api_key=9beVqhXkFy8MK8HMXxa9ov261kZvUQfn&lang=es&q='+this.busqueda)
              .then(res => {
                console.log(res)
                this.gifs = res.data.data
              })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

</style>
