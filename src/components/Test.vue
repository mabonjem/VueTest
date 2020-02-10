<template>
  <div class="Test">
    <input type="text" v-model="title" />
    <br />
    <h1>{{title}}</h1>
    <p v-if="showname">{{user.first_Name}}</p>
    <p v-else> NO </p>
    <p v-text="user.last_Name"></p>
    
    <button v-on:click="greet('greedin Alert')">Say Greeting</button>
    <br/>
    <input type="text" v-on:Keyup="pressKey">
  </div>
</template>



<script>
export default {
  name: "Test",
  data() {
    return {
      title: "Hello world",
      user: {
        first_Name: "Mohammad",
        last_Name: "AboNjem"
      },
      showname: true,
      items: [
        { title: "item1" },
        { title: "item2" },
        { title: "item3" },
        { title: "item4" },
        { title: "item5" }
      ]
    };
  },
  methods: {
    greet: function(greet) {
      alert(greet);
    },
    pressKey:  function()
    {
      alert('greet'); // console.log("pressed");    
    }
  }
};
</script>
 