<template>
  <v-row>
    <v-col>
      <div>
        <list-title text="Inbox"></list-title>
      </div>
      <div v-for="(item, i) in items" :key="i">
        <task-list :text="item" />
      </div>
      <neumo-button />
    </v-col>
  </v-row>
</template>

<script lang="ts">
import ListTitle from "~/components/ListTitle.vue";
import TaskList from "~/components/TaskList.vue";

export default {
  components: {
    ListTitle,
    TaskList
  },
  data() {
    return {
      items: ["Buy MacBook", "Study Vue.js"]
    };
  }
};
</script>
