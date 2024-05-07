<template>
  <form @submit.prevent="onSubmit">
  <h2 class="label-wrapper">
    <label for="todo-input" class="input-lg">Mitä pitäisi tehdä? </label>
  </h2>
    <input
      type="text"
      id="todo-input"
      name="new-todo"
      autocomplete="off" 
       v-model.lazy.trim="label"
       class="input-lg"/>
    <button type="submit" class="btn btn-primary btn-lg" style="margin: 20px;" >Lisää</button>
  </form>
</template>

<script>
  export default {
    methods: {
      onSubmit() {
        if (this.label === "") {
          return;
        }
        this.$emit("todo-added", this.label);
        this.label = "";
      },
    },
    data () {
      return {
        label: "",
      };
    },
  };
</script>

<style>
  button {
    margin: 10px;
    padding: 10px;
  }
</style>