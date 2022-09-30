<template>
    <div v-if="text == 'red'">
      <h1 @mouseover="switchColor = 'red'" 
          @mouseleave="switchColor = 'green'"  
          v-bind:class="switchColor">
            {{secretMsg}}
      </h1>
      <ul>
        <div v-for="attack in filteredAttacks" v-bind:key="attack.id">
          <input type="checkbox" v-model="attack.done"><li>{{attack.text}}</li><button @click="removeAttack(attack)">X</button>
        </div>
      </ul>
      <form @submit.prevent="addAttack">
        <input v-model="newAttack">
        <button>Add Attack</button>    
      </form>
      <button @click="hideCompleted = !hideCompleted">
      {{ hideCompleted ? 'Show all' : 'Hide completed' }}
      </button>
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
      <button @click="onDemandLog">AttacksLog</button>
    </div>
</template>
  
<script>
  let id = 0
  export default {
  name: 'TestRed',
  props: {
    secretMsg: String
  },
  computed: {
    filteredAttacks() {
      return this.hideCompleted
        ? this.attacks.filter((t) => !t.done)
        : this.attacks
    }
  },
  data() {
    return {
      hideCompleted: false,
      newAttack: '',
      attacks: [
        { id: id++, text: "TRanch'Herbe", done: false },
        { id: id++, text: "Meteore", done: false },
        { id: id++, text: "Coupe", done: false }
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
    getDone(attackDone) {
      attackDone.done = true
      this.attacks[attackDone.id] = attackDone
    },
    addAttack() {
      let tmp =  { id: id++, text: this.newAttack, done: false }
      this.attacks.push(tmp)
      this.newAttack = ''
      // console.log(this.attacks)
    },
    removeAttack(attackToDel) {
      this.attacks = this.attacks.filter((attack)=> attack !== attackToDel )
    },
    onDemandLog() {
      console.log(this.attacks)
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
    