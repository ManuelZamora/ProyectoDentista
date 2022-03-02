<template>
    <div>
        <!-- Formulario para añadir pacientes -->
        <section class="form">
            <form action="" class="text-center">
                <input v-model="nombrec" @keyup.enter="crearPaciente" type="text" name="nombrec" placeholder="Nombre completo"> 
                <input v-model="nombreu" @keyup.enter="crearPaciente" type="text" name="nombreu" placeholder="Nombre usuario">
                <input v-model="correo"  @keyup.enter="crearPaciente" type="email" name="correo" placeholder="Correo">
                <input v-model="contra"  @keyup.enter="crearPaciente" type="password" name="contra" placeholder="Contraseña">
                <input @click="crearPaciente" type="button" value="Añadir" class="btn btn-success"> 
            </form>
        </section>
    </div>
    <div>
      <table>
        <tbody>
          <tr v-for="todo in todos" :key="todo.id">
              <td> {{ todo.nombre }} </td>
              <td> {{ todo.usuario }} </td>
              <td> {{ todo.correo }} </td>
          </tr>
        </tbody>
      </table>
    </div>
</template>

<script>
import axios from 'axios'
export default {
  data(){
    return {
        todos:null
    }
  },
  mounted(){
      this.getTodos();
  },
  methods: {
    getTodos(){
        axios.get('http://127.0.0.1:8000/api/paciente/traert').then(response => {
          this.todos = response.data
        }).catch(e => console.log(e))
    }
  }
}
</script>

<style scoped>

</style>