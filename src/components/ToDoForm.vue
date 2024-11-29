<template>
    <form @submit.prevent="onSubmit">
        <h2 id="list-summary">{{listSummary}}</h2>
<ul aria-labelledby="list-summary" class="stack-large">
  <li v-for="item in ToDoItems" :key="item.id">
    <to-do-item
      :label="item.label"
      :done="item.done"
      :id="item.id"></to-do-item>
  </li>
</ul>
      <input
        type="text"
        id="new-todo-input"
        name="new-todo"
        autocomplete="off"
        v-model.lazy.trim="label"
        class="input__lg" />
      <button type="submit" class="btn btn__primary btn__lg">Add</button>
    </form>
  </template>
  
  

<script>
  export default {
  methods: {
    onSubmit() {
  if(this.label === "") {
    return;
  }
  this.$emit('todo-added', this.label);
  this.label = "";
}

  },
  data() {
    return {
      label: "",
    };
  },
};
</script>
