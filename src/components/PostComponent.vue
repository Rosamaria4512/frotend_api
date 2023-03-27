<template>
    <main>
        <h1>Registrar Nuevo Empleado</h1>
        <!-- PASO 3: Crear la Intefaz -->
        <form class="border p-2" @submit='postEmployees()'>
            <div class="mb-3">
                <label for="nomEmploye" class="form-label">Nombre</label>
                <input type="text" id="nomEmploye" class="form-control" v-model="empleadoNuevo.name">
            </div>
            <div class="mb-3">
                <label for="salarioemploye" class="form-label">Salario</label>
                <input type="text" id="salarioemploye" class="form-control" v-model="empleadoNuevo.salary">
            </div>
            <br>
            <button class="btn btn-primary">Crear</button>
        </form>
    </main>
</template>

<script>
import axios from 'axios';
export default {
    name:'PostComponent',
    data() {
        return { // PASO 1
            // Crear variable para almacenar los datos que se enviaran a la API
            // los campos estaran vacios por que se insertan desde un formulario
            empleadoNuevo: {
                name:'',
                salary: '',
            }
        }
    },
    methods:{ // PASO 2:se crea el metodo con el nombre postEmployees
        postEmployees() {
            axios // con el metodo POST se enviaran los datos a la API
                  // los datos se envian a la API desde la variable empleadoNuevo
                .post('http://localhost:3000/api/employee', this.empleadoNuevo)
                // se podran ver por consola una vez se envien
                .then((response) => console.log(response))
        }
    }
}
</script>
<style scoped>

</style>

