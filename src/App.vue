<template>
  <div id="app">
    <!-- ナビゲーションバー 20200307追加 -->
    <div>
      <b-navbar toggleable="lg" type="dark" variant="info">
        <b-navbar-brand href="#">NavBar</b-navbar-brand>

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav>
            <b-nav-item href="#">Link</b-nav-item>
            <b-nav-item href="#" disabled>Disabled</b-nav-item>
          </b-navbar-nav>

          <!-- Right aligned nav items -->
          <b-navbar-nav class="ml-auto">
            <b-nav-form>
              <b-form-input size="sm" class="mr-sm-2" placeholder="Search"></b-form-input>
              <b-button size="sm" class="my-2 my-sm-0" type="submit">Search</b-button>
            </b-nav-form>

            <!-- プルダウンサンプル -->
            <!-- <b-nav-item-dropdown text="Lang" right>
              <b-dropdown-item href="#">EN</b-dropdown-item>
              <b-dropdown-item href="#">ES</b-dropdown-item>
              <b-dropdown-item href="#">RU</b-dropdown-item>
              <b-dropdown-item href="#">FA</b-dropdown-item>
            </b-nav-item-dropdown> -->

            <!-- プルダウンサンプル２ -->
            <!-- <b-nav-item-dropdown right>
              <template v-slot:button-content>
                <em>User</em>
              </template>
              <b-dropdown-item href="#">Profile</b-dropdown-item>
              <b-dropdown-item href="#">Sign Out</b-dropdown-item>
            </b-nav-item-dropdown> -->

          </b-navbar-nav>
        </b-collapse>
      </b-navbar>
    </div>
    <!-- ナブバーここまで -->
    <!-- 初期コンポーネント -->
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->

    <!-- 検索フォーム -->
    <div class="container mx-auto col-5">
        <br>
        <h2>書籍を検索</h2>
        <br>
        <div class="row">
            <div class="col-md">
                <form class="form-inline">
                    <div class="form-group">
                      <label></label>
                      <!-- <input type="text" class="form-control" placeholder="7つの習慣"> -->
                      <input class="mx-auto form-control" placeholder="Search">
                      <button class="btn btn-outline-primary" type="submit">Search</button>
                    </div>
                </form>
            </div>
        </div>
    </div>

    <div class="root">
      <Search class="search" @loadStart="onLoadStart" @loadComplete="onLoadComplete"/>
      <Result :items="items" :loadProgress="loadProgress"/>
    </div>

  </div>
</template>

<script>
import Search from "@/components/Search";
import Result from "@/components/Result";

export default {
  data() {
    return {
      items: [],
      loadProgress: false,
    };
  },
  methods: {
    onLoadStart() {
      this.loadProgress = true;
    },
    onLoadComplete({ results }) {
      this.items = results;
      this.loadProgress = false;
    },
  },
  components: {
    Search,
    Result,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
}
</style>
