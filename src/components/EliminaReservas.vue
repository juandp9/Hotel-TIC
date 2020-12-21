<template>
  <div id="eliminaReservas">
    <h2>Eliminar Reserva</h2>
    <label for="">Número de habitación</label>
    <input type="text" v-model="habitacion_id" />
    <label for="">Nombre</label>
    <input type="text" v-model="nombre" />
    <label for="start">Fecha de inicio:</label>
    <input type="date" id="start" v-model="fecha_inicio"
       value="2020-12-24"
       min="2020-12-24" max="2021-12-31">
    <label for="end">Fecha fin:</label>
    <input type="date" id="end" v-model="fecha_fin"
       value="2020-12-24"
       min="2020-12-24" max="2021-12-31">
        <h4>¿Estás Seguro?</h4>
    <button v-on:click="EliminaReservas">Confirmar</button>
  </div>
</template>


<script>
import axios from 'axios';
export default {
    name: "EliminaReservas",
    data:function(){
        return{
          habitacion_id: "",
          nombre: "",
          fecha_inicio: "",
          fecha_fin: "",
            
        };
    },
    methods: {
      EliminaReservas: function() {
        var self = this
        console.log("hola mundo")
        var datosJson =         
        {
            habitacion_id: self.habitacion_id,
            nombre: self.nombre,
            fecha_inicio: self.fecha_inicio,
            fecha_fin: self.fecha_fin
        };
        console.log(datosJson)
        axios
            .delete("https://hotel-tic-back.herokuapp.com/reservas/eliminar", {data: datosJson})
            .then(response => {
            alert(response.data.mensaje);
            })
            .catch(err => {
            console.log(err.response);
            alert("error en el servidor");
            });
    }
  }
};
</script>

<style>

#eliminaReservas {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
}

label {
    display: block;
    font: 1rem 'Fira Sans', sans-serif;
}

input,
label {
    margin: 0.5rem 0;
}


</style>

   
