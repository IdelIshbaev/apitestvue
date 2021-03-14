<template>
  <div id="app">
    <h1>Person: {{person.name}}</h1>
    <h1>Age: {{person.age}}</h1>
    <h2>Count: {{people.id}}</h2>
    <button @click="changeCount">Increase</button>
    <h3>{{count}}</h3>
    <div v-for="(item, index) in people" :key="item.name">
      {{item.name}} - {{index}}
    </div>
    <div v-for="(value, name) in object" :key="value">
      {{value}} - {{name}}
    </div>
    <div v-for="n in 10" :key="n">{{n}}</div>
    <div v-if="condition">U see me</div>
    <div>
      <p>{{msg}}</p>
      <input v-model="msg">
    </div>
    <br>
    <MyComponent :data="person"/>
    <p>{{dvaspisok}}</p>
    <div>
    <div v-for="item in dvaspisok" :key="item.id"> {{item}}
      <div v-for="(it, index) in item" :key="it">
        <p v-if="it == '1'">{{it}} - {{index}}</p>
        </div>
    </div> 
    </div>

    <!-- <MyComponent v-bind:data="person"/> -->
  </div>
</template>

<script>
// import MyComponent from './components/MyComponent.vue'
import {dataFromData, dvaspisok} from './data/mydata';
import MyComponent from './components/MyComponent';

export default {
  components:{
    MyComponent
  },
  name: 'App',
  data() {
    return{
      dvaspisok: [Array],
      msg: "msg",
      condition:{
        seen: true
      },
      person:{
        name: "Idel",
        age: 20
      },
      people:[
          {name: "Idel1",
          id: 1},
          {name: "Idel2",
          id: 2},
          {name: "Idel3",
          id: 3}
      ],
      object:{
        gorod: "ufa",
        rayon: "cher"
      },
      count: 0
    };
  },
  methods: {
    changeCount(){
      this.count++;
    }
  },
  created() {
    this.msg = dataFromData;
    this.dvaspisok = dvaspisok;
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
