<template>
    <div class="container">
        <h1>Tabla de Productos</h1>
        <table>
            <thead>
                <tr>
                    <th>Id</th>
                    <th>Nombre</th>
                    <th>Valor</th>
                    <th>Existencias</th>
                    
                </tr>
            </thead>
            <tbody>
              
                    <tr v-for="producto in productos" :key="producto.id">
                    <td>{{ producto.id }}</td>
                    <td>{{ producto.nombre }}</td>
                    <td>{{ producto.valor }}</td>
                    <td>{{ producto.existencias }}</td>
                </tr>
                   
                <router-view />
            
              
            </tbody>
        </table>
    </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      productos: [],
    };
  },

  methods: {
    obtenerProductos() {
      axios.get('http://localhost:8080/api/productos/listar')
      .then((response) => {
        this.productos = response.data;
      })
      .catch((error) => {
        console.error("Error al obtener listado de productos:", error);
      });
    },
  },
  mounted() {
    this.obtenerProductos();
  },
};
</script>
