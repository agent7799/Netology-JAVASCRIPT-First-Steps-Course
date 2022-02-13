<template>
 <!-- Modal Человек Паук-->
         <div class="modal fade"
        id="exampleModal" 
        tabindex="-1" 
        aria-labelledby="exampleModalLabel" 
        aria-hidden="true"
        >
          <div class="modal-dialog">
            <div class="modal-content">
                    
              <div class="modal-header">

                <h5 class="modal-title" 
                id="exampleModalLabel">
                {{character.name}}
                <br><h6 class="modal-title" 
                    >{{character.nameor}}</h6>
                </h5>
                    
                <button type="button" 
                class="btn-close" 
                data-bs-dismiss="modal" 
                aria-label="Close"
                ></button>
              </div>
              <div class="modal-body">
                    
          <!--      <pre>{{character}}</pre> -->
              <!--   <img src="http://i.annihil.us/u/prod/marvel/i/mg/3/50/526548a343e4b.jpg" -->
                   <img 
                   :src="character.thumbnail"
                    class="img-fluid rounded-start" 
                    :alt="character.name"
                    
                    >
                <div>
                    <h5>Описание:</h5>
                    <p>{{character.description}}</p>
                    <h5>Комиксы</h5>
                    <ul>
                        <li v-for ="(el, idx) in character.comics"
                            :key="idx">
                            
                            <a href="el.resourceURI">{{el.name}}</a>
                            <!--     {{el.resourceURI}}   -->
                        <li/>
                        

                    </ul>
                </div>
              </div>
              <div class="modal-footer">
                <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Закрыть</button>
                <!-- <button type="button" class="btn btn-primary">Save changes</button> -->
              </div>
            </div>
          </div>
        </div>

</template>

<script>
    export default {
        name: "AppModal",
        props: ['character'],
    }
</script>

<style scoped>

</style>
