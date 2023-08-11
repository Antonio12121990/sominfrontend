<template>
    <div class="productos">
        <div class="components">
       <FormularioProductos/>
       <TablaProductos/>
        </div>
    </div>
</template>

<script>

import FormularioProductos from "@/components/FormularioProductos.vue";
import TablaProductos from "@/components/TablaProductos.vue";

export default {
name: 'ProductoView',


components: {
   FormularioProductos,
   TablaProductos
  
}
}
</script>

<style >
body {
    font-family: Arial, sans-serif;
    background-color: #671919;
    margin: 0;
    padding: 0;
}

.components{
    display: grid;
    grid-template-columns: 1fr 2fr;
   grid-auto-rows: 1fr;

}
.container {
   /* max-width: 400px;*/
    margin:1rem;
    padding: 1rem;
    background-color: #676060;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
    border-radius: 5px;
}

h1 {
    text-align: center;
    margin-bottom: 20px;
}

.form-group {
    margin-bottom: 15px;
}

form{

    padding: 2%;
    
}
label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
}

input {
    width: 100%;
    padding: 8px;
    border: 1px solid #17a082;
    border-radius: 3px;
}

button {
    display: block;
    width: 100%;
    padding: 10px;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background-color: #0056b3;
}

table {
    width: 100%;
    border-collapse: collapse;
    margin-bottom: 20px;
    
}

th, td {
    padding: 10px;
    text-align: left;
 /*   border-bottom: 1px solid #ddd;*/
 border-style: solid;
    
}
tr{

    border-style: solid;
}

th {
    background-color: #007bff;
    color: #fff;
    border-style: solid;
}

tr:hover {
    background-color: #c90c0c;
}
</style>