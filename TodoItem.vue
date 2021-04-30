<template>
  <InputText v-model="description" />

  <div class="btn-botoes">
    <Button @click="saveTodo" class="btn-voltar">Salvar</Button>
    <Button @click="cancel">Voltar</Button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      description: "",
    };
  },
  methods: {
    cancel() {
      this.$emit("cancel");
    },
    saveTodo() {
      this.$emit("saveTodo", { description: this.description });
    },
  },
};
</script>

<style scoped>
.btn-botoes {
  margin-top: 1rem;
}
.btn-voltar {
  margin-right: 1rem;
}
</style>
