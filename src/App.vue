<template>
  <div>
    <h1>To-Do List</h1>
    <form action=""></form>
    <input type="text" v-model="name" />
    <button class="btn btn-primary" @click="onSubmit">click</button>
  </div>
</template>
<script>
import { ref } from "vue";
export default {
  setup() {
    const name = ref("kossie");
    const onSubmit = () => {
      console.log(name.value);
    };
    // const updateName = e => {
    //   name.value = e.target.value;
    // };
    return {
      name,
      onSubmit,
      //updateName,
    };
  },
};
</script>

<style>
.name {
  color: red;
}
</style>
