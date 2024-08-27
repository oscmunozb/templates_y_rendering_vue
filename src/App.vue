<!-- Script JS -->
<script>
export default {
  name: 'App',
  data() {
    return {
      // Valores iniciales que se pueden modificar
      colorFondo: 'darkgreen', // Color de fondo del contenedor
      colorTexto: 'white', // Color del texto dentro del contenedor
      mostrarTexto: true, // Controla la visibilidad del texto
      borde: '35', // Valor para redondear los bordes del contenedor (porcentaje)
      contenidoTexto: "Awesome Vue.js", // Contenido del texto que se mostrará en el contenedor
      tipografia: "cursive", // Tipografía seleccionada para el texto
      tipografiasArray: ["Times New Roman", "cursive", "Segoe UI", "monospace"], // Lista de opciones de tipografías disponibles
      opaco: true, // Controla si el contenedor se muestra con opacidad reducida
      tamanoLetra: "mediano", // Tamaño de letra seleccionado para el texto (pequeño, mediano, grande)
    }
  }
}
</script>

<!-- Template HTML -->
<template>
  <main class="m-5 d-flex justify-content-center align-items-center flex-wrap">

    <!-- Formulario para modificar propiedades -->
    <form class="formulario text-white p-4 rounded">
      <!-- Campo para cambiar el color de fondo -->
      <div class="mb-3">
        <label for="colorFondo" class="form-label">Color de fondo</label>
        <input class="form-control" type="text" id="colorFondo" placeholder="#000 o black" v-model="colorFondo">
      </div>
      <!-- Campo para cambiar el color del texto -->
      <div class="mb-3">
        <label for="colorTexto" class="form-label">Color de texto</label>
        <input class="form-control" type="text" id="colorTexto" placeholder="#fff o white" v-model="colorTexto">
      </div>
      <!-- Checkbox para controlar la visibilidad del texto -->
      <div class="mb-3">
        <label class="form-check-label me-2" for="mostrarTexto">Mostrar texto</label>
        <input class="form-check-input" type="checkbox" name="mostrarTexto" id="mostrarTexto" v-model="mostrarTexto">
      </div>
      <!-- Control deslizante para ajustar el borde del contenedor -->
      <div class="mb-3">
        <label class="form-label me-2" for="borde">Borde: {{ borde }}%</label>
        <input class="w-100" type="range" name="borde" id="borde" min="0" max="50" v-model="borde">
      </div>
      <!-- Campo para editar el contenido del texto que se mostrará en el contenedor -->
      <div class="mb-3">
        <label class="form-label" for="contenidoTexto">Contenido texto</label>
        <textarea class="form-control" name="contenidoTexto" id="contenidoTexto" placeholder="Ingresa un texto"
          v-model="contenidoTexto"></textarea>
      </div>
      <!-- Selector de tipografía para el texto -->
      <div class="mb-3">
        <label class="form-label" for="tipografia">Tipografía</label>
        <select class="form-select" name="tipografia" id="tipografia" v-model="tipografia">
          <option :value="tipografia" v-for="tipografia in tipografiasArray">
            {{ tipografia }}
          </option>
        </select>
      </div>
      <!-- Checkbox para aplicar opacidad al contenedor -->
      <div class="mb-3">
        <label class="form-check-label me-2" for="opaco">Opaco</label>
        <input class="form-check-input" type="checkbox" name="opaco" id="opaco" v-model="opaco">
      </div>
      <!-- Opciones para seleccionar el tamaño de letra del texto -->
      <div>
        <label class="form-label w-100">Tamaño de letra</label>
        <input class="form-check-input me-1" type="radio" name="pequeno" id="pequeno" value="pequeno"
          v-model="tamanoLetra">
        <label class="form-check-label me-2" for="pequeno">Pequeño</label>
        <input class="form-check-input me-1" type="radio" name="mediano" id="mediano" value="mediano"
          v-model="tamanoLetra">
        <label class="form-check-label me-2" for="mediano">Mediano</label>
        <input class="form-check-input me-1" type="radio" name="grande" id="grande" value="grande"
          v-model="tamanoLetra">
        <label class="form-check-label" for="grande">Grande</label>
      </div>
    </form>

    <!-- Contenedor que muestra el resultado de las opciones seleccionadas en el formulario -->
    <div class="contenedor border border-2 m-5 d-flex align-items-center justify-content-center"
      :class="{ 'opacidad': opaco }" :style="{ backgroundColor: colorFondo, borderRadius: borde + '%' }">
      <h1 class="text-break m-4" :class="{
        textoPequeno: tamanoLetra === 'pequeno',
        textoMediano: tamanoLetra === 'mediano',
        textoGrande: tamanoLetra === 'grande'
      }" :style="{ color: colorTexto, fontFamily: tipografia }" v-show="mostrarTexto">{{ contenidoTexto }}</h1>
    </div>
  </main>
</template>


<!-- Estilos CSS -->
<style scoped>
/* Estilos del formulario */
.formulario {
  background-color: #2F4F4F;
}

/* Estilos del contenedor que muestra las opciones seleccionadas */
.contenedor {
  width: 350px;
  height: 350px;
}

/* Clase para aplicar opacidad al contenedor */
.opacidad {
  opacity: 0.5;
}

/* Clases para los tamaños de texto */
.textoPequeno {
  font-size: 16px;
}

.textoMediano {
  font-size: 24px;
}

.textoGrande {
  font-size: 32px;
}
</style>