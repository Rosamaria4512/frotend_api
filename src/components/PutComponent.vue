<template>
    <div class="container">
        <form action="" class="form-horizontal"></form>
        <div class="form-group left">
            <label for="" class="control-label col-sm-2">Nombre</label>
            <div class="col-sm-10">
                <input type="text" name="nombre" class="form-control" id="nombre" v-model="form.name">

                <div class="form-group left">
                <label for="" class="control-label col-sm-2">Salario</label>
                <div class="col-sm-10">
                <input type="text" name="salario" class="form-control" id="salario" v-model="form.salary">
            </div>
            </div>
            </div>
            <div class="form-group">
            <button class="btn btn-primary" v-on:click="editar()">Editar</button>
        </div>
        
        </div>

    </div>
</template>
<script>
import axios from 'axios';
export default {
    name:'PutComponent',
    data() {
        return {

            form:{
                empleadoId:"",
                name:"",
                salary:""
            }
        }
    },
    methods: {
    editar(){
        axios.patch('http://localhost:3000/api/employee',this.form)
        .then(data =>{
            console.log(data)
        })

    }
    },
    mounted:function(){
        this.form.empleadoId = this.$route.params.id;
        axios.get('http://localhost:3000/api/employee', this.form.empleadoId).
        then(datos =>{
            this.form.nombre = datos.data[0].nombre
            this.form.salario= datos.data[0].salario
            this.form.token = localStorage.getItem('token')
            console.log(this.form)
        })
    }
}

</script>
<style scoped>
.left{
    text-align:left;
}
</style>