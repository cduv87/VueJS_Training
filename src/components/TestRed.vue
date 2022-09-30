<template>
    <div v-if="text == 'red'">
      <h1 @mouseover="switchColor = 'red'" 
          @mouseleave="switchColor = 'green'"  
          v-bind:class="switchColor">
            {{secretMsg}}
      </h1>
      <ul>
        <div v-for="attack in attacks" v-bind:key="attack.id">
          <li>{{attack.text}}</li><button @click="removeAttack(attack)">X</button>
        </div>
      </ul>
      <form @submit.prevent="addAttack">
        <input v-model="newAttack">
        <button>Add Attack</button>    
      </form>
      <p>{{newAttack}}</p>
    </div>
    <div>
      <h1 v-bind:class="titleClass">{{text}}</h1>
    </div>
    <div>
      <button v-on:click="increment">{{ count }}</button>
    </div>
    <br>
    <div>
      <!-- <input :value="text" @input="onInput"> -->
      <input v-model="text">
    </div>
    <div>

    </div>
</template>
  
<script>
  let id = 0
  export default {
  name: 'TestRed',
  props: {
    secretMsg: String
  },
  data() {
    return {
      newAttack: '',
      attacks: [
        { id: id++, text: "TRanch'Herbe" },
        { id: id++, text: "Meteore" },
        { id: id++, text: "Coupe" }
      ],
      text: 'blue',
      titleClass: 'red',
      switchColor: 'green',
      count: 0
    }
  },
  methods: {
    increment() {
      // update component state
      this.count++
    },
    onInput(e) {
    // a v-on handler receives the native DOM event
    // as the argument.
    this.text = e.target.value
    },
    addAttack() {
      let tmp =  { id: id++, text: this.newAttack }
      this.attacks.push(tmp)
      // console.log(this.attacks)
    },
    removeAttack(attackToDel) {
      this.attacks = this.attacks.filter((attack)=> attack !== attackToDel )
    }
  }
}

  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.green {
  color: rgb(95, 255, 95);
}
.red {
  color: rgb(255, 94, 94);
}
h3 {
    margin: 40px 0 0;
}
ul {
    list-style-type: none;
    padding: 0;
}
li {
    display: inline-block;
    margin: 0 10px;
}
a {
    color: #42b983;
}
</style>
    