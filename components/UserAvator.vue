<template>
  <v-menu bottom min-width="200px" rounded offset-y>
    <template v-slot:activator="{ on }">
      <v-btn icon x-large v-on="on">
        <v-avatar color="brown" size="48">
          <span class="white--text text-h5">{{ user.initials }}</span>
        </v-avatar>
      </v-btn>
    </template>
    <v-card>
      <v-list-item-content class="justify-center">
        <div class="mx-auto text-center">
          <v-avatar color="brown">
            <span class="white--text text-h5">{{ user.initials }}</span>
          </v-avatar>
          <h3>{{ user.fullName }}</h3>
          <p class="text-caption mt-1">
            {{ user.email }}
          </p>
          <v-divider class="my-3"></v-divider>
          <v-btn depressed rounded text>
            Edit Account
          </v-btn>
          <v-divider class="my-3"></v-divider>
          <v-btn depressed rounded text>
            LogOut
          </v-btn>
        </div>
      </v-list-item-content>
    </v-card>
  </v-menu>
</template>

<script lang="ts">
import { Vue, Component } from "nuxt-property-decorator";

@Component
export default class UserAvator extends Vue {
  user = {
    initials: "YN",
    fullName: "Yuto Nakamura",
    email: "yutonakamura@gmail.com"
  };
}
</script>
