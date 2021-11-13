<template>
  <div id="app">
    <nav id="nav">
      <router-link to="/">Список</router-link> |
      <router-link to="/create">Создать</router-link>
    </nav>
    <el-row :gutter="20" type="flex" justify="center">
      <el-col :xs="24" :sm="22" :md="20" :lg="16" :xl="12">
        <router-view class="content" />
      </el-col>
    </el-row>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
.content {
  padding: 20px 0 0;
}
</style>
