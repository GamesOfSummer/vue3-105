<script setup lang="ts">
import { ref, reactive, watch } from "vue";

let getTaco = ref(true);
const question = ref("");

const state = reactive({
  newComment: "",
  comments: ["Taco comment 1!", "Taco comment 2!", "Taco comment 3!"],
});

function addTacoClick() {
  console.log("clicked");
  state.comments.push(state.newComment);
  state.newComment = "";
}
</script>

<template>
  <div>
    <h2>Taco comments</h2>
  </div>

  <input v-model="state.newComment" />
  <button @click="addTacoClick">Add comment</button>
  <li v-for="item in state.comments" v-text="item" :key="item"></li>
</template>
