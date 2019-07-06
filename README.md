# README

## BootstrapVue
  [https://bootstrap-vue.js.org/](https://bootstrap-vue.js.org/)

## How to start Bootstrap-Vue

1. Ready to use bootstrap-vue
  ```
  $ rails new bootstrapvue_rails --webpack=vue
  $ cd bootstrapvue_rails
  $ yarn add bootstrap-vue
  $ rails g controller Home index
  ```

2. edit config/routes.rb
  ```
  Rails.application.routes.draw do
    root to: 'home#index'
    # For details on the DSL available within this file, see http://guides.rubyonrails.org/routing.html
  end
  ```

3. make and edit javascript file
  - make
  ```
  $ touch app/javascript/packs/home.js
  ```

  - edit
  ```
  import Vue from 'vue/dist/vue.esm'
  import BootstrapVue from 'bootstrap-vue'
  import App from '../app.vue'
  　　
  import 'bootstrap/dist/css/bootstrap.css'
  import 'bootstrap-vue/dist/bootstrap-vue.css'
  　　
  Vue.use(BootstrapVue)
  　　
  document.addEventListener('DOMContentLoaded', () => {
    　　const app = new Vue({
  　　    el: '#hello',
  　　    data: {
  　　      message: "Can you say hello?"
  　　    },
  　　    components: { App }
  　　  })
  })
  ```

4. edit app/javascript/app.vue
  ```
  <template>
    <div id="app">
      <p>{{ message }}</p>
      <div class="text-center my-3">
        <b-button v-b-tooltip.hover title="Tooltip content">Hover Me</b-button>
      </div>
    </div>
  </template>

  <script>
  export default {
    data: function () {
      return {
        message: "Hello Vue!"
      }
    }
  }
  </script>

  <style scoped>
  p {
    font-size: 2em;
    text-align: center;
  }
  </style>
  ```

5. edit app/views/home/index.html.erb
  ```
  <h1>Home#index</h1>
  <p>Find me in app/views/home/index.html.erb</p>

  <div id='hello'>
    {{message}}
    <app></app>
  </div>

  <%= javascript_pack_tag 'home' %>
  ```

## start server
```
$ ./bin/webpack-dev-server
$ rails s
```
