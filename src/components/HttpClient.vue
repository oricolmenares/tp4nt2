<template>
  <section class="src-components-http-client">
    <div class="mainDiv">
      <h2> Usuarios Mockapi </h2>
      <hr>
      <hr>
    </div>
    <button class="btn btn-warning my-3 mr-3" @click="getUsersXHRCb()"> Pedir Usuarios(cb)</button>
    <button class="btn btn-warning my-3 mr-3" @click="getUsersAxios()"> Pedir Usuarios axios </button>

    <br>
    <div v-if="users.length">
      <table class="table table-dark">
        <tr>
          <th>Nombre</th>
          <th>Telefono</th>
          <th>Email</th>
        </tr>
        <tr v-for="user in users" :key="user.id">
          <th>{{user.name}}</th>
          <th>{{user.phone}}</th>
          <th>{{user.email}}</th>
        </tr>
      </table>
    </div>
    <h4 v-else class="alert alert-danger text-center"> No se encuentran datos </h4>
    
  </section>

</template>

<script>

  export default  {
    name: 'src-components-http-client',
    props: [],
    mounted () {

    },
    data () {
      return {
        url:'https://635c78e1f0bc26795bff441d.mockapi.io/users',
        users: []
      }
    },
    methods: {
      getUsersXHRCb(){
        const xhr = new XMLHttpRequest()
        xhr.open('get', this.url)

        xhr.addEventListener('load', ()=>{
          if(xhr.status == 200){
            let respuesta = JSON.parse(xhr.response)
            this.users = respuesta;
          }
        })

        xhr.send()
      },
      xhrPromise(){
        return new Promise((resolve, reject) => {
          const xhr = new XMLHttpRequest()
          xhr.open('get', this.url)

          xhr.addEventListener('load', ()=>{
            if(xhr.status == 200){
              let respuesta = JSON.parse(xhr.response)
              resolve(respuesta)
            } else {
              reject(`error http: ${xhr.status}`)
            }
          })
          xhr.send()
        })
        
      },
      getUsersXHRPromise(){
        this.xhrPromise()
          .then(respuesta => { this.users = respuesta })
          .catch(error => console.error(error))
      },
      getUsersAxios(){
        this.axios(this.url)
          .then(respuesta => { this.users = respuesta.data })
          .catch(error => console.error(error))
      }
    },
    computed: {

    }
}
</script>

<style scoped lang="css">
  .mainDiv{
    background-color: gray;
    color:black;
  }

  hr{
    background-color: teal;
  }
  
</style>
