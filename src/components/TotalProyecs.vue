<template>
      <div class="row my-3 ">
        <div class="col-6">
          <h3>Total de proyectos: {{numeroProyectos}}</h3>
        </div>
        <div class="col-6 text-end">
           <button @click="limpiarData" class="btn btn-danger">Limpiar proyectos</button>
        </div>
      </div>

    <div class="table-responsive">
    <table class="table table-dark">
      <thead>
        <tr>
          <th>#</th>
          <th>Proyecto</th>
          <th>Tipo</th>
          <th>Urgente</th>
          <th>Completado</th>
          <th>Borrar</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(proyecto, index) in proyectos" :key="index"  >
          <td>{{index}}</td>
          <td>{{proyecto.proyecto}}</td>
          <td>{{proyecto.tipo}}</td>
          <td @click="cambiarEstado(proyecto, 'urgente')" :class="proyecto.urgente ?
           'bg-success' : 'bg-danger'">{{proyecto.urgente ? "Si" : "No"}}</td>
          <td @click="cambiarEstado(proyecto, 'completado')" :class="proyecto.completado ?
           'bg-success' : 'bg-danger'">{{proyecto.completado ? "Completado" : "Incompleto"}}</td>
       
          <td>
            <button @click="limpiar(proyecto,index)" class="btn btn-danger">Eliminar</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default{
    props: ["numeroProyectos", "proyectos", "cambiarEstado","limpiarData","limpiar",
    ],
    
};

</script>