<template>
    <div class="container">
      <h1>Formulario de Productos</h1>
      <form id="productos-form" @submit.prevent="guardar">
        <div class="form-group">
          <label for="id">Id:</label>
          <input type="number" id="id" name="id" required  v-model="id" />
        </div>
        <div class="form-group">
          <label for="nombre">Nombre:</label>
          <input type="text" id="nombre" name="nombre" required v-model="nombre" />
        </div>
        <div class="form-group">
          <label for="valor">Valor:</label>
          <input type="number" id="valor" name="valor" required v-model="valor" />
        </div>
        <div class="form-group">
          <label for="existencias">Existencias:</label>
          <input type="number" id="existencias" name="existencias"  required v-model="existencias" />
        </div>
  
        <button type="submit" id="guardar" name="guardar">Guardar</button><br />
        <button type="button" id="eliminar" name="eliminar" @click="eliminar"> Eliminar</button ><br />
        <button type="button" id="actualizar" name="actualizar"  @click="actualizar"> Actualizar</button><br />
        <button type="button" id="consultar" name="consultar" @click="consultar"> Consultar</button><br />
      </form>
    </div>
  </template>

  <script>
    import axios from "axios";
    
    export default {
      
      data() {
    
        return {
          id: "",
          nombre: "",
          valor: "",
          existencias: "",
        };
    },
    methods: {
    guardar() {
      
      axios
        .post("http://localhost:8080/api/productos", {
          id: this.id,
          nombre: this.nombre,
          valor: this.valor,
          existencias: this.existencias,
        })
        .then((response) => {
          console.log("Producto registrado con éxito:", response.data);
          alert("exito");
        this.id = '';
        this.nombre = '';
        this.valor = '';
        this.existencias = '';
         
        })
        .catch((error) => {
          console.error("Error al registrar productos:", error);
        });
    },
    
    consultar() {
      
      axios
        .get('http://localhost:8080/api/productos/'+this.id)
        .then((response) => {
          this.nombre = response.data.nombre;
          this.valor = response.data.valor;
          this.existencias = response.data.existencias;
        })
        .catch((error) => {
          console.error("Error al consultar producto:", error);
        });
    },


    actualizar() {
      
      axios
        .put("http://localhost:8080/api/productos/actualizar/"+this.id, {
          id: this.id,
          nombre: this.nombre,
          valor: this.valor,
          existencias: this.existencias,
        })
        .then((response) => {
          console.log("Producto actualizado con éxito:", response.data);
        })
        .catch((error) => {
          console.error("Error al actualizar Producto:", error);
        });
    },
    eliminar() {
     
      axios
        .delete("http://localhost:8080/api/productos/"+this.id)
        .then(() => {
          console.log("Producto eliminado con éxito");
          this.id = "";
          this.nombre = "";
          this.valor = "";
          this.existencias ="";
        })
        .catch((error) => {
          console.error("Error al eliminar producto:", error);
        });
    },
  },
};
</script>