<template>
  <div class="container">
    <h2>
      <span>To Do</span>
      <span class="task-num">{{ items.length }}</span>
    </h2>
    <ul class="task-list">
      <li v-for="task in items" :key="task.id">
        <div>
          <input type="checkbox" @change="$emit('itemDone', task)" />
          <span>{{ task.title }}</span>
        </div>
        <button class="btn-remove" @click="$emit('removeItem', task.id)">
          Remove
        </button>
      </li>
    </ul>

    <h2>
      <span>Done</span>
      <span class="task-num">{{ itemsDone.length }}</span>
    </h2>
    <ul class="task-list complete-list">
      <li v-for="task in itemsDone" :key="task.id">
        <div>
          <input type="checkbox" @change="$emit('itemDone', task)" checked/>
          <span>{{ task.title }}</span>
        </div>
        <button class="btn-remove" @click="$emit('removeItem', task.id)">
          Remove
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    items: Array,
    itemsDone: Array
  },
  data() {
    return {};
  },
  methods: {},
};
</script>

<style scoped>
</style>