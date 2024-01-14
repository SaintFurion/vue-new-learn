<template>
  <table>
    <UpdateCase 
      v-for="item in checkList"
      :id="item.id"
      :name="item.name"
      :status="item.status"
      :key="item.id"
    />
  </table>
  <AddCase @add="add"/>
</template>

<script>
  import UpdateCase from "./components/UpdateCase.vue";
  import AddCase from "./components/AddCase.vue";

  export default {

    components: {
      UpdateCase, AddCase
    },
    data() {
      return {
        checkList: []
      }
    },
    methods: {
      add(name) {
        let id = this.checkList.length + 1
        let status = false
        this.checkList.push({id, name, status})
      },
      change(id, name, status) {
        this.checkList = this.checkList.map((item) => {
          if (item.id === id) {
            item.name = name;
            item.status = status;
          }
          return item;
        });
      },
      remove(id) {
        this.checkList = this.checkList.filter((item) => {
          return item.id !== id;
        })
      }
    }
  }
</script>