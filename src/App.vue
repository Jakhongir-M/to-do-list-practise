<template>
  <div class="container">
    <div class="card">
      <h1>To-do-pactise</h1>
      <div class="form-control">
        <div id="example"></div>
        <input
          v-model.trim="InputValue"
          class="input"
          type="text"
          :style="{
            border:
              InputValue.length >= 10 ? '2px solid red' : '2px solid #42b983',
          }"
        />
        <br />
        <button
          class="btn"
          :class="{
            primary: true,
            danger: InputValue.length >= 10,
          }"
          @click="sendFunc"
        >
          Add
        </button>
      </div>
    </div>
    <div class="card">
      <ul v-if="MyNotes.length > 0" class="list">
        <li class="list-item" v-for="(list, index) in MyNotes" :key="index">
          {{ index + 1 }} {{ list }}
          <button class="btn danger" @click="Delete(index)">DELETE</button>
        </li>
      </ul>
      <h2 v-else class="title-yes">here not info</h2>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      InputValue: "",
      MyNotes: [],
    };
  },
  methods: {
    sendFunc() {
      if (this.InputValue.length > 0) {
        this.MyNotes.push(this.InputValue);
        this.InputValue = "";
      }
    },
    Delete(index) {
      this.MyNotes.splice(index, +1);
    },
  },
};
</script>

<style></style>
