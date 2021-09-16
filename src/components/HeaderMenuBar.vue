<template>
  <div style="text-align: left" class="menu-toolbar">
    <ul>
        <li class="menu-item">
            <a class="menu-link" href="/">
                <img src="/Default-logos_white.png"/> <b>Default-blog</b>
            </a>
        </li>
        <li class="menu-item"> <a class="menu-link">Профиль</a></li>
        <li class="menu-item"> <a class="menu-link">Блог</a></li>
    </ul>
  </div>
</template>

<script>

export default {
  name: 'HelloWorld',
  data() {
    return {
      input: '# hello',
      postId: null,
      preview: false
    }
  },
  computed: {
  },
  methods: {
  }
}
</script>

<style>
.menu-toolbar {
    height: 50px;
    background-color: #1A2646;  
    vertical-align: middle;  
}

.menu-link {
    vertical-align: middle;
    color: white;
}

ul {
    height: 50px;
    margin: 0px;
}

.menu-item {
    display: inline;
    padding: 0px 10px;
    height: 50px;
    line-height: 45px;
    vertical-align: middle;
}

a{
    text-decoration: none;
    cursor: pointer;
    color:black;
}

img {
    vertical-align: middle;
    padding: 0 10px;
    height: 32px;
    width: 32px;
}
</style>
