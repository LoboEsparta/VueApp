<template>
  
  <div class="row">

    <div class="col-12 mb-4">
      <Porgressbar :porcentaje="porcentaje"></Porgressbar>
    </div>



    <div class="col-12 col-md-4">
      <form @submit.prevent="registrarProyecto">
   <div class="mb-3">
      <label class="form-label">Proyecto</label>
      <input v-model.trim="proyecto" type="text" class="form-control" required>
   </div>

    <div class="mb-3">
        <label class="form-label">Actividad</label> 
        <select v-model.trim="tipo" class="form-select" required>
             <option disabled selected value="">Selecciona una Actividad</option>
             <option >Aplicaciones web con Vue.js</option> 
             <option >Backend Services con Node.js</option>
             <option >App movil con React Native</option>
      </select> 
      </div>

    <div class="mb-3">
        <label for="exampleInoutPassword1" class="form-check-label">Urgente</label>
        <input v-model="urgente" type="checkbox" class="form-check-input" />
      </div>


      <button type="submit" class="btn btn-primary">Guardar</button>
  </form>
    </div>




    <div class="col-12 col-md-8">
    <Total-proyecs
    :numeroProyectos="numeroProyectos" 
    :proyectos="proyectos" 
    :cambiarEstado="cambiarEstado"/>
  
    </div>
  </div>

</template>

<script>
import TotalProyecs from "./TotalProyecs.vue";
import Porgressbar from "./Porgressbar.vue";

 export default{
  data: () => ({
    proyecto: "",
    tipo: "",
    urgente: false,
    proyectos: [],
    
  }),
  methods: {
    registrarProyecto() {
       const proyecto = {
        proyecto: this.proyecto,
        tipo: this.tipo,
        urgente: this.urgente,
        completado: false,
      };
      this.proyectos.push(proyecto);
      localStorage.setItem("proyectos", JSON.stringify(this.proyectos));

      

      this.proyecto="";
      this.tipo ="";
      this.urgente = false ;
    },
    cambiarEstado(proyecto, campo){
      proyecto[campo] = !proyecto[campo];
      //this.proyectos[id].urgente = !this.proyectos[id].urgente;
    }
  },
  computed: {
    numeroProyectos(){
      return this.proyectos.length;
    },
    porcentaje(){
      let completados = 0;
      this.proyectos.map( proyecto => {
          if (proyecto.completado) completados++;
        });
        return (completados * 100) / this.numeroProyectos || 0;
    },
  },
  components: { TotalProyecs, Porgressbar },
  mounted (){
    this.proyectos = JSON.parse(localStorage.getItem("proyectos")) || [];
  }
 };

</script>