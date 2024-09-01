<script>
export default {
  name: 'TemplatesForm',
  data() {
    return {
      colorFondo: '',
      colorTexto: '',
      mostrarTexto: '',
      borde: '',
      contenidoTexto: '',
      tipoLetraSeleccionada: '',
      tamanoLetraSeleccionada: '',
      tipoLetra: ['georgia', 'roboto'],
      opaco: '',
      tamanoLetra: [
        { value: '2rem', label: 'Pequeño' },
        { value: '5rem', label: 'Mediano' },
        { value: '8rem', label: 'Grande' }
      ]
    }
  }
}
</script>
<template>
  <h1>Desafío - Templates y rendering en Vue</h1>

  <div class="container">
    <!--izq-->
    <form class="form flex-column">
      <div class="form-group">
        <label for="colorFondo">Color Fondo</label>
        <input type="color" id="colorFondo" v-model="colorFondo" class="form-control" />
      </div>
      <div class="form-group">
        <label for="colorTexto">Color Texto</label>
        <input type="color" id="colorTexto" v-model="colorTexto" class="form-control" />
      </div>

      <div class="form-group flex-row">
        <label for="mostarTexto">Mostar Texto</label>
        <input type="checkbox" id="mostarTexto" v-model="mostrarTexto" class="form-control" />
      </div>

      <div class="form-group">
        <label for="borde">Borde</label>
        <input
          type="range"
          name="borde"
          id="borde"
          min="0"
          max="40"
          v-model="borde"
          class="form-control"
        />
      </div>
      <div class="form-group flex-column">
        <label for="contenidoTexto">Contenido Texto</label>
        <textarea id="contenidoTexto" v-model="contenidoTexto" class="form-control"> </textarea>
      </div>
      <div class="form-group">
        <label for="tipografia">Tipografia</label>
        <select name="tipoLetra" id="tipografia" v-model="tipoLetraSeleccionada">
          <option v-for="tipografia in tipoLetra" :key="tipografia" :value="tipografia">
            {{ tipografia }}
          </option>
        </select>
      </div>

      <div class="form-group flex-row">
        <label for="opaco">Opaco</label>
        <input type="checkbox" id="opaco" v-model="opaco" />
      </div>
      <div class="form-group flex-row">
        <label for="tamanoLetra">Tamaño Letra</label>

        <div class="check-item flex-row" v-for="tamano in tamanoLetra" :key="tamano.value">
          <label :for="tamano.value">{{ tamano.label }}</label>
          <input
            type="radio"
            :name="tamano.value"
            :value="tamano.value"
            :id="tamano.value"
            v-model="tamanoLetraSeleccionada"
          />
        </div>
      </div>
    </form>
    <!--der-->
    <div
      id="resultado"
      :style="{
        backgroundColor: colorFondo,
        color: colorTexto,
        borderRadius: `${borde}%`,
        fontFamily: tipoLetraSeleccionada,
        fontSize: tamanoLetraSeleccionada
      }"
      :class="{
        opaco: opaco
      }"
    >
      <p v-show="mostrarTexto">{{ contenidoTexto }}</p>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  align-items: center;
  gap: 2rem;
}

.flex-row {
  display: flex;
  gap: 10px;
}

.flex-column {
  display: flex;
  flex-direction: column;
}

form {
  align-items: start;
  background-color: rgb(15, 9, 69);
  padding-inline: 2.5rem;
  padding-block: 2rem;
}
label {
  color: white;
}
input {
  width: 100%;
}

.form-group {
  padding-bottom: 1.5rem;
}
#resultado {
  height: 450px;
  width: 450px;
  display: grid;
  place-content: center;
}
.opaco {
  opacity: 0.3;
}
</style>
