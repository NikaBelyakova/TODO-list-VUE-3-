<template>
  <Header @add="addTask" />

  <CardList @remove-item="removeTask" @item-done="moveToDoneTask" :items="items" :itemsDone="itemsDone" />

  <!-- <div class="container">
        <h2>
            <span>To Do</span>
            <span class="mask-num">{{ items.length }}</span>
        </h2>
        <ul class="mask-list conplete-list">
            <li 
            v-for="(mask, index) in items" 
            :key="mask.id"
            >
                <div>
                    <input 
                    type="checkbox" 
                    @change="doCheck(index, 'need')">

                    <span>{{ mask.title }}</span>
                </div>
                <button 
                class="btn-remove"
                @click="removeMask(index, 'need')"
                >Remove</button>
            </li>
        </ul>

        <h2>
            <span>Done</span>
            <span class="mask-num">{{ completeList.length }}</span>
        </h2>
        <ul class="mask-list conplete-list">
            <li 
            v-for="(mask, index) in completeList" 
            :key="mask.id"
            >
                <div>
                    <input type="checkbox" checked v-on:change="doCheck(index, 'complete')">
                    <span>{{ mask.title }}</span>
                </div>
                <button class="btn-remove"
                v-on:click="removeMask(index, 'complete')"
                >Remove</button>
            </li>
        </ul>
    </div> -->
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
    },
    // doCheck(index, type) {
    //   if (type === "need") {
    //     const completeMask = this.items.splice(index, 1);
    //     this.completeList.push(...completeMask);
    //   } else {
    //     const notCompleteMask = this.completeList.splice(index, 1);
    //     this.items.push(...notCompleteMask);
    //   }
    // },
  },
};
</script>

<style scoped>
.task-list {
  list-style: none;
}
</style>