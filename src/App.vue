<script>
export default {
  data() {
    return {
      isSearchActive: false,
      items: [
        {
          active: true,
          title: "Satış Kanalları Senk",
          code: "OMP02",
        },
        {
          active: true,
          title: "Online Satış Kanalları",
          code: "OMP01",
        },
        {
          active: true,
          title: "Satış Kanalları Sensssk",
          code: "OMP04",
        },
        {
          active: false,
          title: "Online Satış Kanallarsssı",
          code: "OMP015",
        },
      ],
    };
  },
  methods: {
    openFavSearchBar() {
      // if (!this.isSearchActive) {
      //   console.log(this.$refs);
      //   this.$refs.favoritesMenuSearchField.focus();
      // }
      this.isSearchActive = !this.isSearchActive;
    },
  },
};
</script>

<template>
  <v-app id="inspire">
    <!-- <v-layout>
      <v-toolbar color="white" light fixed app>
        <v-toolbar-title>Favorites Lists</v-toolbar-title>
        <v-spacer></v-spacer>

        <v-btn icon class="favorites-menu-icon">
          <v-icon>star</v-icon>
        </v-btn>
      </v-toolbar>

     
    </v-layout> -->
    <div class="favorites-menu-container">
      <v-toolbar class="elevation-0 white">
        <v-toolbar-title class="text-xs-center"
          >Favorites -
          <span class="favLengt">{{ items.length }}</span></v-toolbar-title
        >

        <v-spacer></v-spacer>

        <div class="favorites-menu-search-bar" v-if="isSearchActive">
          <v-text-field
            :autofocus="isSearchActive"
            prepend-inner-icon="search"
            @blur="openFavSearchBar"
          ></v-text-field>
        </div>

        <v-btn icon @click="openFavSearchBar">
          <v-icon>search</v-icon>
        </v-btn>
      </v-toolbar>

      <v-divider></v-divider>

      <v-list class="px-2">
        <v-list-tile v-for="item in items" :key="item.title" avatar>
          <v-list-tile-content>
            <v-list-tile-title
              class="list-title"
              v-html="item.title"
            ></v-list-tile-title>
            <div class="list-title-code" v-html="item.code"></div>
          </v-list-tile-content>

          <v-list-tile-action>
            <v-icon :color="item.active ? 'warning' : 'grey'">star</v-icon>
          </v-list-tile-action>
        </v-list-tile>
      </v-list>
    </div>
  </v-app>
</template>

<style lang="scss">
@import "./assets/_variables.scss";
#app {
  font-family: Roboto, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.favorites-menu-icon {
  color: $rbx-warning !important;
}

.favorites-menu-search-bar {
  position: absolute;
  z-index: 3;
  width: 100%;
  background: $rbx-white;
  left: 0;
  top: 0;
  height: 100%;
  display: flex;
  align-items: center;
  padding: 1rem 1.5rem;
  transition: all 1s ease-in-out;
}

.favorites-menu-container {
  position: relative;
  max-width: 375px;
  width: 100%;
  margin: 150px;
  box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
  height: max-content;

  .list-title {
    font-size: 14px !important;
    font-weight: 600;
  }
  .list-title-code {
    font-size: 12px !important;
  }
  .v-list__tile {
    &:hover {
      background: $rbx-white-bg;
      cursor: pointer;
    }
  }
  .favLengt {
    background: $rbx-success;
    padding: 2px 4px;
    border-radius: 4px;
    color: $rbx-white;
  }
}
</style>
