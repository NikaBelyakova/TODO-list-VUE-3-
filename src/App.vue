<template>
  <Header @add="addTask" />
  <CardList @remove-item="removeTask" @item-done="moveToDoneTask" :items="items" :itemsDone="itemsDone" />
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
      ],
      itemsDone: [
        { title: "Задача третья", complete: true, id: Date.now() + 2 },
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
        this.itemsDone = this.itemsDone.filter( item => item.id !== id);
    },
    moveToDoneTask (item) {
        item.complete = !item.complete;
        
        if (item.complete) {
          this.itemsDone.push(item);
          this.items = this.items.filter(item => item.complete === false);
        } else {
          this.items.push(item);
          this.itemsDone = this.itemsDone.filter(item => item.complete === true);
        }
    }
  },
};
</script>

<style scoped>
.task-list {
  list-style: none;
}
</style>