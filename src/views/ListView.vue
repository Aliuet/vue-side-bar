<template>
    <div class="form-group">
      <div class="input-wrapper">
        <input v-model="text" class="form-control" /> &nbsp;
        <button class="btn btn-success" @click="addText">Add Text</button>
      </div>
      <transition-group tag="ul" name="list" class="item-list">
        <li v-for="(text, idx) in items" :key="text" @click="removeText(idx)">
            {{ idx + 1 }}. {{ text }}
        </li>
      </transition-group>
    </div>
  </template>
<script>
import { reactive, ref } from 'vue';
export default {
    setup() {
        const text = ref("");
        const items = reactive(["Vue js", "Laravel"]);
        const addText = () =>{
            items.push(text.value);
            text.value = "";
        };
        const removeText = (idx) => {
            items.splice(idx, 1);
        };
        return {
            text,
            items,
            addText,
            removeText
        }

    },
}
</script>
<style scoped>

.list-enter-active,
.list-leave-active {
    transition: all 0.5s ease;
}
.list-enter-from,
.list-leave-to {
    opacity: 0;
    transform: translateX(30px);
}
.btn {
  padding: 8px 16px;
  border: none;
  border-radius: 5px;
  color: white;
  cursor: pointer;
}

.btn-success {
  background-color: #4caf50;
}
.item-list {
  list-style: none;
  padding: 0;
}
.item-list li {
  padding: 8px;
  margin: 4px 0;
  background-color: #f2f2f2;
  border-radius: 5px;
  cursor: pointer
}
.item-list li:hover {
  background-color: #e0e0e0;
}
.form-group {
  max-width: 400px;
  margin: 0 auto;
}
.form-control {
  flex: 1;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 5px;
}
</style>
