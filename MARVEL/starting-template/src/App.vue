<template>
    <div id="app">

        <app-header :changeSearch="changeSearch"/>

        <div class="container">
            <h1 class="pt-3 pb-3">Персонажи Marvel 04.02.2022 by Dmitry Mikheev</h1>

<h5 v-if = "!character.length && !loading">Такой персонаж не найден!</h5>

            <!--  <pre>App search: {{search}}</pre> -->
            <!--    <pre>character: {{character}}</pre> -->

         <!--    <pre>characterIndex: {{characterIndex}}</pre>  -->

            <app-modal :character="character[characterIndex]"/>


        
            <spinner v-if="loading"/>

            <div class="row">

<div v-for ="(el, idx) in character"
    :key = "el.id"
    class="card mb-3" style="max-width: 440px;">
  <div class="row g-0">
    <div class="col-md-4">
      <img :src="el.thumbnail" 
      class="img-fluid rounded-start" 
      :alt="el.name">
    </div>
    <div class="col-md-8">
      <div class="card-body">
        <h5 class="card-title">{{el.name}}</h5>
        <h6 class="card-title">{{ el.nameor}}</h6>
        <!-- Button trigger modal -->
<button type="button" 
        class="btn btn-primary" 
        data-bs-toggle="modal" 
        data-bs-target="#exampleModal"
        @click="characterIndex = idx"
        >
        Подробнее
</button>
        <!-- <p class="card-text">This is a wider card with supporting text below as a natural lead-in to additional content. This content is a little bit longer.</p>   -->
        <!-- <p class="card-text"><small class="text-muted">Last updated 3 mins ago</small></p>  -->
        <p></p>
        <p></p>
      </div>
    </div>
  </div>
</div>

            </div>

        </div>

    </div>
</template>

<script>
    import Spinner from "./components/Spinner";
    import AppModal from "./components/AppModal";
    import AppHeader from "./components/AppHeader";

    export default {
        name: 'App',
        components: {
            AppHeader,
            AppModal,
            Spinner,
        },

        data() {
            return {
                loading: false,
                characters: [],
                characterIndex: 0,
                search: '',
            }
        },

        methods: {
           fetchCharacters: function () {
               return fetch('https://netology-api-marvel.herokuapp.com/characters')
               .then(res => res.json())     
                .then(json => this.characters = json);
           },    
            changeSearch: function (value) {
                this.search = value;
            },

        },

        computed: {
              character: function(){
                  const {characters, search} = this;
                  return characters.filter((character) => {
                    return character.name.toLowerCase().indexOf(search.toLowerCase()) !== -1;
                  }
                  )
              }
        },

        async mounted(){
            this.loading = true;
            await this.fetchCharacters();
            this.loading = false;
        }


    }
</script>

<style>

</style>
