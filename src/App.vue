<template>
  <Header @add="addTask" />
  <CardList @remove-item="removeTask" @item-done="toggleCompletion" :items="getUncompleteItems()" :itemsDone="getCompleteItems()" />
</template>

<script>
import Header from "@/components/Header.vue";
import CardList from "@/components/CardList.vue";

export default {
  components: {
    Header,
    CardList,
  },
  data() {
    return {
      items: [
        { title: "Задача первая", complete: false, id: Date.now() },
        { title: "Задача вторая", complete: false, id: Date.now() + 1 },
      ]
    };
  },
  methods: {
    addTask(valueInput) {
      this.items.push({
        title: valueInput,
        id: Date.now(),
        complete: false
      });
    },
    removeTask(id) {
    this.items = this.items.filter( item => item.id !== id);
    },
    getUncompleteItems() {
    return this.items.filter(item => !item.complete)
    },
    getCompleteItems() {
    return this.items.filter(item => item.complete)
    },
    toggleCompletion (item) {
    item.complete = !item.complete;
    }
  },
};
</script>

<style >
  * {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    margin: 0;
    padding: 0;
  }

 .container {
    max-width: 800px;
    margin: 0 auto;
    padding: 0 15px;
  }
</style>