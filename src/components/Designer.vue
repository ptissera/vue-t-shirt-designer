<template lang="pug">
  .container
    menu
      nav(v-for="item in shirtParts" :class="{'nav2': item.useClass}" v-if="currentTemplate.supportedColors >= item.showRequired")
        ul
          li
            label(v-text="item.name")
          li(v-for="c in colorList")
            a(href="#" class="color-box" v-on:click="selectColor(item.index, c.color)" :style="{'background-color': c.color}")
    menu
      nav(class="nav2")
        ul
          li
            label Template Hombres
          li(v-for="t in templates.man" class="menu-templates")
            a(href="#" v-on:click="selectTemplate(t)" v-text="t.name")        
    .canvas
      component(v-bind:is="currentTemplate.key" v-bind="currentColors")

</template>
<script>

import TemplateH01 from './templates/TemplateH01';
import TemplateH02 from './templates/TemplateH02';

export default {
  name: 'Designer',
  components: {
    'template-h-01': TemplateH01,
    'template-h-02': TemplateH02,
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      currentTemplate: {},
      templates: {
        man: [
          {key: 'template-h-01', name: 'template 01', supportedColors: 3},
          {key: 'template-h-02', name: 'template 02', supportedColors: 1}
        ]
      },
      colorList: [
        {name: 'color 1', color: '#dacd4a'},
        {name: 'color 2', color: '#293e7a'},
        {name: 'color 3', color: '#1e263f'},
        {name: 'color 4', color: '#ffffff'},
        {name: 'color 5', color: '#6d0b1c'},
        {name: 'color 6', color: '#6b96a6'},
        {name: 'color 7', color: '#4d8fcc'},
        {name: 'color 8', color: '#b32753'},
        {name: 'color 9', color: '#909195'},
        {name: 'color1 0', color: '#58585a'},
        {name: 'color 11', color: '#786092'},
        {name: 'color 12', color: '#62472d'},
        {name: 'color 13', color: '#d56326'},
        {name: 'color 14', color: '#000000'},
        {name: 'color 15', color: '#c72424'},
        {name: 'color 16', color: '#b02575'},
        {name: 'color 17', color: '#54988c'},
        {name: 'color 18', color: '#468146'},
        {name: 'color 19', color: '#263e32'},
        {name: 'color 20', color: '#874997'}
      ],
      shirtParts: [
        {name: 'Fondo', index: 'fondo', useClass: false, showRequired: 0},
        {name: 'Letras', index: 'letras', useClass: true, showRequired: 0},
        {name: 'Trama 1', index: 'trama1', useClass: false, showRequired: 1},
        {name: 'Trama 2', index: 'trama2', useClass: false, showRequired: 2},
        {name: 'Trama 3', index: 'trama3', useClass: false, showRequired: 3},
        {name: 'Trama 4', index: 'trama4', useClass: false, showRequired: 4},
        {name: 'Trama 5', index: 'trama5', useClass: false, showRequired: 5}
      ],
      color: {
        trama1: '#000',
        trama2: '#000',
        trama3: '#000',
        trama4: '#000',
        trama5: '#000',
        fondo: '#000',
        letras: '#fff'
      }
    }
  },
  created() {
    this.currentTemplate = this.templates.man[0];
  },
  methods: {
    selectColor(index, color) {
      this.color[index] = color;
    },
    selectTemplate(template) {
      this.currentTemplate = template;
    }
  },
  computed: {
    currentColors() {
      return {color: this.color};
    }
  }
}
</script>


<style scoped>
  .container {
    padding: 1px 0;
  }
  menu {
    width: 100vw;
    background-color: #DADADA;
    border-bottom: 1px solid #222;
    padding: 0;
    margin: 0;
  }

  .canvas {
    margin: 20px 0 0 100px;
    width: 300px;
    height: 300px;
  }

  .nav2 {
    padding: 5px 0 5px 30px;
    background: #444;
  }
  nav {
    padding: 5px 0 5px 30px;
    background: #333;
  }
  nav ul {
    display: flex;
    list-style: none;
    padding: 0;
    margin: 0;
  }

  label {
    color: lightgray;
    display: block;
    font-size: 14px;
    width: 105px;
    padding-right: 20px;
  }

  nav li a {
    color: white;
    display: block;
    text-decoration: none;

  }
  nav li a:hover {
    background: tomato;
    color: white;
  }

  .color-box {
    border-radius: 25px;
    width: 15px;
    height: 15px;
    border: 1px solid #ddd;
    margin: 0 3px 0 3px;
  }

  .color-box:hover {
    border-color: yellow;
  }

  .menu-templates {
    padding: 5px;
  }

  .menu-templates a {
    padding: 2px 18px;
    border-radius: 20px;
    background-color: black;
  }
</style>