<template>
  <div class="header">
    <div class="container">
      <div class="logo">TODO List</div>
      <div class="form">
        <input type="text" v-model="valueInput" @keypress.enter="addTask" />
        <button class="btn" @click="addTask">Add new task</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      valueInput: "",
    };
  },
  methods: {
    addTask() {
      if (this.valueInput === "") {
        alert("Заполните поле");
        return
      }
      this.$emit("add", this.valueInput);
      this.valueInput = "";
    },
  },
};
</script>

<style scoped>
    .header {
    background-color: #333;
    padding: 10px 0;
    margin-bottom: 40px;
    }

    .header .container {
    display: flex;
    align-items: center;
    justify-content: space-between;
    }

    .header .container .logo {
    width: 110px;
    line-height: 50px;
    color: #ddd;
    font-size: 24px;
    cursor: pointer;
    }

    .header .container .form {
    width: 60%;
    display: flex;
    justify-content: space-between;
    }

    .header .container .form input {
    width: calc(100% - 145px);
    height: 40px;
    text-indent: 10px;
    border: 1px solid #fff;
    border-radius: 5px;
    border-radius: 0;
    box-sizing: border-box;
    outline: none;
    transition: 0.2s border;
    }

    .header .container .form input:focus {
    border: 1px solid #12c0dd;
    }
        
    .btn {
        background-color: #12c0dd;
        border: 1px solid #12c0dd;
        color: #fff;
        font-weight: 700;
        text-transform: uppercase;
        padding: 10px 15px;
        font-size: 12px;
        height: 40px;
        outline: none;
        transition: 0.2s;
        cursor: pointer;
    }
    
    .btn:hover {
        background-color: #0dd6f8;
        border-color: #0dd6f8;
    }
</style>