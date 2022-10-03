<template>
  <!-- <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </nav>
  <router-view/> -->
  <div id="app" class="container">
    <div class="row">
      <div class="col-md-12">
        <h1>Personas</h1>
      </div>
    </div>
    <div class="row">
      <div class="col-md-12">
        <formulario-persona @add-persona="agregarPersona"/>
        <tabla-personas 
          :personas="personas" 
          @delete-persona="eliminarPersona"
          @actualizar-persona="actualizarPersona"
        />
      </div>
    </div>
  </div>
</template>

<script>
  import TablaPersonas from '@/components/TablaPersonas.vue'
  import FormularioPersona from '@/components/FormularioPersona.vue'

  export default{
    name: 'app',
    components: {
      TablaPersonas,
      FormularioPersona,
    },
    data(){
      return{
        personas: [
          {
            id:1,
            nombre:'Pablo',
            apellido:'Jake',
            email:'pablo@email.com'
          },
          {
            id:2,
            nombre:'Tyrone',
            apellido:'Jackson',
            email:'tyrone@email.com'
          },
          {
            id:3,
            nombre:'Uniqua',
            apellido:'Simon',
            email:'uniqua@email.com'
          },
        ]
      }
    },
    methods: {
      agregarPersona(persona){
        let id = 0

        if(this.personas.length>0){
          id = this.personas[this.personas.length - 1].id + 1
        }

        this.personas = [...this.personas, {...persona , id}]
        console.log(this.personas)
      },
      eliminarPersona(id){
        this.personas = this.personas.filter(
          persona => persona.id !== id
        )
      },
      actualizarPersona(id, personaActualizada){
        this.personas = this.personas.map(persona =>
        persona.id === id ? personaActualizada : persona)
      },
    }
  }
</script>

<style lang="scss">
// #app {
//   font-family: Avenir, Helvetica, Arial, sans-serif;
//   -webkit-font-smoothing: antialiased;
//   -moz-osx-font-smoothing: grayscale;
//   text-align: center;
//   color: #2c3e50;
// }

// nav {
//   padding: 30px;

//   a {
//     font-weight: bold;
//     color: #2c3e50;

//     &.router-link-exact-active {
//       color: #42b983;
//     }
//   }
// }
button{
  background: #009435;
  border: 1px solid #009435;
}
</style>
