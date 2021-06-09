<template>
  <v-row>
    <v-col>
      <div>{{ text }}</div>
    </v-col>
  </v-row>
</template>

<script lang="ts">
import { Vue, Component, Prop } from "nuxt-property-decorator";

@Component
export default class TaskList extends Vue {
  @Prop()
  text!: string;
}
</script>

<style>
.list-title {
  font-size: 20px;
  font-weight: 700;
}
</style>
