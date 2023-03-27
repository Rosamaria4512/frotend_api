<template>
    <div>
        <!-- PASO 3. Crear la Interfaz para mostrar los datos -->
        <h1> Listado de Empleados</h1>
        <!-- // crear la Tabla para organizar los Datos -->
        <table class="table table-primary table-bordered border-primary">
            <!-- crear encabezados para los Titulos -->
            <thead>
                <tr class="table-warning">
                    <td>ID</td>
                    <td>NOMBRE</td>
                    <td>SALARIO</td>
                    <td>ACCION</td>
                </tr>
            </thead>
            <!-- // crear el cuerpo de la tabla para ubicar los datos -->
            <tbody>
                <!-- // Recorrer los datos de la Variable Usuarios mediante V-for -->
                <tr v-for="empleado in empleados" v-bind:key="empleado">
                    <!-- // interpolar los datos del arreglo en cada celda -->
                    <td>{{ empleado.id }}</td>
                    <td>{{ empleado.name }}</td>
                    <td>{{ empleado.salary }}</td>
                    <td>
                        <input type="button" value="Editar" class="btn btn-primary" >
                        <input type="button" value="Elimiinar" class="btn btn-danger">
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>
<script>
export default {
    name: 'GetComponent',
    data(){
        return{
            // // PASO 1. Crear variable para guardar los datos de la API
            empleados: []
        }
    },
    // PASO 2. crear el metodo para estraer los datos de la API
    async mounted(){
        // hacer la peticion GET a la ruta de la API 
        await this.axios.get('http://localhost:3000/api/employee')
        // devuelve la promesa con un resultado (response)
        .then(response => {
            // guardar en la variable usuarios la respuesta obtenida
            this.empleados = response.data;
            // si se quiere ver el resultado en consola
            console.log(response.data)
        }) //Mostrar por consola el error
        .catch((e) => {
        console.log(e)      
    });
    }
}
</script>
<style scoped>

</style>