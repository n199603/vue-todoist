<template>
  <v-app dark>
    <v-navigation-drawer v-model="drawer" :clipped="clipped" fixed app>
      <v-list>
        <div v-for="(item, i) in items" :key="i">
          <v-list-item v-if="!item.subItems" :to="item.to" router exact>
            <v-list-item-action>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title v-text="item.title" />
            </v-list-item-content>
          </v-list-item>

          <v-list-group v-else :key="item.title" no-action>
            <template v-slot:activator>
              <v-list-item>
                <v-list-item-content>
                  <v-list-item-title>{{ item.title }}</v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </template>
            <v-list-item
              v-for="subItem in item.subItems"
              :to="subItem.to"
              :key="subItem.title"
            >
              <v-list-item-title v-text="subItem.title" />
            </v-list-item>
          </v-list-group>
        </div>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar :clipped-left="clipped" fixed app>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-spacer />
      <v-btn icon>
        <v-icon>mdi-plus</v-icon>
      </v-btn>
      <user-avator />
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<script lang="ts">
import UserAvator from "~/components/UserAvator.vue";

export default {
  components: {
    UserAvator
  },
  data() {
    return {
      clipped: true,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: "mdi-apps",
          title: "Welcome",
          to: "/"
        },
        {
          icon: "mdi-inbox",
          title: "Inbox",
          to: "/inbox"
        },
        {
          icon: "mdi-calendar-today",
          title: "Today",
          to: "/today"
        },
        {
          icon: "mdi-calendar-month",
          title: "Upcoming",
          to: "/upcoming"
        },
        {
          icon: "mdi-calendar-month",
          title: "Projects",
          to: "/projects",
          subItems: [
            { title: "Personal", to: "/projects/personal" },
            { title: "Work", to: "/projects/work" }
          ]
        }
      ]
    };
  }
};
</script>
