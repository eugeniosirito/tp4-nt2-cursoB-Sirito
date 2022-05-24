<template>
  <section class="src-componentes-formulario">
    <div class="jumbotron">
      <h1>Formulario</h1>
      <hr />
      <hr />
      <br />

      <vue-form :state="formState" @submit.prevent="enviar()">
        <validate tag="div">
          <label for="nombre">Nombre</label>
          <input
            type="text"
            id="nombre"
            name="nombre"
            class="form-control"
            v-model.trim="formData.nombre"
            autocomplete="off"
            required
            :minlength="nombreMinLength"
            maxlength="15"
          />

          <field-messages name="nombre" show="$dirty">
            <div slot="required" class="alert alert-danger mt-1">
              Campo Obligatorio
            </div>
            <div slot="minlength" class="alert alert-danger mt-1">
              Este campo requiere minimo {{ nombreMinLength }} caracteres.
            </div>
          </field-messages>
        </validate>

        

        <validate tag="div">
          <label for="edad">Edad</label>
          <input
            type="number"
            id="edad"
            name="edad"
            class="form-control"
            autocomplete="off"
            v-model.number="formData.edad"
            required
            :min="edadMin"
            :max="edadMax"
          />

          <field-messages name="edad" show="$dirty">
            <div slot="required" class="alert alert-danger mt-1">
              Campo Obligatorio
            </div>
            <div slot="min" class="alert alert-danger mt-1">
              La edad mínima permitida {{ edadMin }} años.
            </div>
            <div slot="max" class="alert alert-danger mt-1">
              La edad máxima permitida {{ edadMax }} años.
            </div>
          </field-messages>
        </validate>

        <validate tag="div">
         
          <label for="email">Mail</label>
          <input 
            type="email"
            id="email"
            name="email" 
            class="form-control"
            autocomplete="off"
            v-model.trim="formData.email" 
            required 
          />

          
          <field-messages name="email" show="$dirty">
            
            <div slot="required" class="alert alert-danger mt-1">Campo Obligatorio</div>
            <div slot="email" class="alert alert-danger mt-1">Email Invalido</div>
          </field-messages>
        </validate>

        <button class="btn btn-success my-3" :disabled="formState.$invalid">
          Enviar
        </button>
      </vue-form>

      <hr />
      <p><u>formData</u></p>
      <pre>{{ formData }}</pre>

      <hr />
      
    </div>
  </section>
</template>

<script>
export default {
  name: "src-componentes-formulario",
  props: [],
  mounted() {},
  data() {
    return {
      formState: {},
      formData: this.getInicialData(),
      nombreMinLength: 5,
      edadMin: 18,
      edadMax: 120,
    };
  },
  methods: {
    getInicialData() {
      return {
        nombre: "",
        edad: "",
        email: "",
      };
    },
    enviar() {
      console.log({ ...this.formData });

      this.formData = this.getInicialData();
      this.formState._reset();
    },
  },
  computed: {},
};
</script>

<style scoped lang="css">

h1{
  color:coral;
}
</style>
