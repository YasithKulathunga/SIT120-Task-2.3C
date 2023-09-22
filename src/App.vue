
<template>
  <div>
    <!--Text Interpolation -->
    <h1>{{ title }}</h1>
  </div>
  <div>
    <!--Using HTML derectives to change the color of the text -->
    <p v-html="htmlElement"></p>
  </div>
  <div>
    <!--Attribute bindings -->
    <button v-bind:disabled="isDisabled">Texting attribute binding</button>
  </div>

  <br>
  <hr>

  <div>
    <!--Javascript expression inside syntax -->
    {{ ok ? 'Okay' : 'Nah' }}
    {{ number + 1 }}
    <div>
      {{ fname.toUpperCase() }}
    </div>
  </div>

  <br>
  <hr>

  <div>
    <!--Methods -->
    <span style="font-weight: 600;font-size: 30px;">Methods</span>
    <h2>Multiply : {{ multiply(10) }}</h2>
    <h2>Add : {{ add(150) }}</h2>
  </div>

  <br>
  <hr>

  <div>
    <!--Reactive fundamentals using refs and setup() -->
    <h1>{{ title3 }}</h1>
  </div>

  <br>
  <hr>

  <div>
    <h1>{{ fullname }}</h1>
  </div>

  <br>
  <hr>

  <div>
        <!--Binding clasess with v-bind-->
        Class Binding
    <h1 class="red" v-bind:class="status" >Warning!!</h1>
    <h1 class="green" v-bind:class= "emergency">Exit -></h1>

    <!--Binding styles -->
   --------- Style Binding ---------
   <p v-bind:style="{
    'font-size' : titlesize + 'px',
   }">Using <span v-bind:style="{color : textbackground,}">inline style bind</span> in vue3 </p>
  </div>

  <br>
  <hr>

  <div>
    <!--List rendering : v-for -->
    <h2 v-for="(game, index) in games" :key="game">{{ index }}. {{ game }}</h2>

  <hr>   

    <!--List rendering : v-for with an object -->
    <ul class="left">
    <li v-for="(value, key, index) in myMovie">
		  {{ index }}. {{ key }}: {{ value }}
		</li>
  </ul>
  </div>

  <hr>

  <div>
    <!--List rendering : v-for with an Range -->
    <span v-for="n in 10">{{ n }}</span>
  </div>

  <hr>

  <div>
    <!--List rendering : v-for on template -->
    <template v-for="movie in movies" : key="movie">
      <h1 class="green">{{ movie }}</h1>
    <hr/>
    </template>
  </div>

  <br>


  <div>
    <!--List rendering : v-for with v-if -->
    <template v-for="game in games">
      <li v-if="laptops in laptops">
        {{ laptops.name }}
        <span v-if="laptops.price > 1500">(Expensive)</span>
      </li>
    </template>
  </div>

  <br>

  <div>
    <!--List rendering : v-for with a component -->
    <fruit-item
      v-for="fruit in fruits"
      :key="fruit"
      :fruit-name="fruit"
    ></fruit-item>
  </div>

  <br>

  <div>
    <!--Event Handling : Inline Handlers -->
    <h1>{{ newname }}</h1>
    <button v-on:click="newname ='Spiderman'">Reveal</button>

    <h2>Count</h2>
    <h2>{{ count }}</h2>
    <button v-on:click="count = count + 1">Add</button>
    <button v-on:click="count = count - 1">Minus</button>
  </div>

  <br>
  <hr>

  <div>
    <!--Event Handling : method Handlers -->
    <button @click="hello">Greet</button>
  </div>

  <br>
  <hr>

  <div>
    <!--Form input Building : v-model -->
    input type : text
    <p>Message is: {{ message }}</p>
	  <input v-model="message" placeholder="edit me" />
    <br>

    input type : checkbox <br>
    <input type="checkbox" id="checkbox" v-model="checked" />
    <label for="checkbox">{{ checked }}</label> <br>

    input type : radio <br>
    Gender: {{ Gender }}<br>
    <input type="radio" id="male" value="Male" v-model="Gender" />
    <label for="male">Male</label>

    <input type="radio" id="female" value="Female" v-model="Gender" />
    <label for="female">Female</label> <br>

    input type : select <br>
    <span> Category: {{ category }}</span> <br>

    <select v-model="category">
      <option value="Action">Action</option>
      <option value="Romance">Romance</option>
      <option value="Comedy">Comedy</option>
    </select><br>

    input type : Textarea <br>
    <span>Type your message:</span><br>
    <p style="white-space: pre-line;">{{ messages }}</p>
    <textarea v-model="messages" placeholder="your message"></textarea>

  </div>
  <hr>
  <div>
    input type : text.lazy
    <p>Message is: {{ lazy }}</p>
	  <input v-model.lazy="lazy" placeholder="edit me" />
    <br>

    input type : text.number {{ age }}
    <input v-model.number="age" />
    <br>

    input type : text.trim
    Final : {{ msg }}
    <input v-model.trim="msg" />
  </div>

  <br>
  <hr>

  <div>
  <!--Watchers-->
  <h2>Volume Tracker(0 -20)</h2>
  <h4>Current Volume - {{ volume }}</h4>
  <div>
    <button @click="volume += 2 ">Increase</button>
    <button @click="volume -= 2 ">Decrease</button>
  </div>
  </div>

  <br>
  <hr>
  <!--Components : Props and emit -->
  <div>
    <div>
      <input type="text" v-model="firstname"/> 
      <input type="text" v-model="lastname"/>
    </div>
      <props :firstname="firstname" :lastname="lastname" @callingevent="callingevent" />
    </div>

  <br>
  <hr>
  <!--Components : Routers -->
  <div>
    <routers/>
  </div>






  


</template>

<script>
import { ref, computed, reactive } from 'vue'
import props from './components/props.vue'
import routers from './components/routers.vue'
export default {
  name : 'Greetings',
  components : {
    props,
    routers
  },
  setup(){
    const name = ref('Vue.js')
    const title3 = ref('Concept Number 3')
    const firstname = ref('')
    const lastname = ref('')

    function callingevent(call) {
      alert(`Calling ${call}`)
    } 

    setTimeout(() => {
      title3.value = 'Reactivity Fundamentals'
      console.log(title3)
    },2000)

    return {
      title3,
      firstname,
      lastname,
      callingevent,
    }
  },

  

  data() {
    return {
      title: 'Text Interpolation',
      htmlElement: '<h1 style="color:red">This is red</h1>',
      isDisabled: true,
      number: 5,
      fname: 'John',
      lname: 'Richardson',
      ok: true,
      basemultipler: 2,
      status: 'danger',
      emergency: 'exit',
      textbackground: 'yellow',
      titlesize: 30,
      newname: 'Peter Parker',
      count: 0,
      message:'',
      messages:'',
      lazy:'',
      checked: true,
      Gender: 'Male',
      category: '',
      msg: '',
      age:0,
      volume: 0,
      fruits: ['Apple', 'Banana', 'Orange', 'Strawberry', 'Grapes'],
      games: ['Minecraft', 'Super Mario Bros', 'Super Mario Bros 2'],
      movies: ['Avatar', 'Avengers: Endgame', 'Avengers: Endgame 2'],
      laptops: [
        {
          name: 'Macbook Pro',
          price: 1300,
        },
        {
          name: 'Macbook Air',
          price: 2000,
        },
        {
          name: 'Macbook Pro 2',
          price: 1500,
        }
      ],
      myMovie: {
        name: 'ready player one',
        director: 'Steven Spielberg',
        year: 2019,
        rating: 8.5,
        genre: 'Action'
      },
    }
  },
  methods: {
    multiply(num) {
      return num * this.basemultipler
    },
    add(num1) {
      return num1 + 1
    },
    hello(event) {
      alert(`Hello ${name.value}!`)
      if(event){
        alert(event.target.tagName)
      }
    },
    
  },
  computed: {
    fullname(){
      return `${this.fname} ${this.lname}`
    }
  },
  watch: {
    volume(newValue, oldValue){
      if(newValue > oldValue && newValue === 16){
        alert('Your volume is too high')
      
      }
   }
 
   }
}
</script>

<style scoped>
header {
  line-height: 1.5;
}

div{
  text-align: center;
  align-items: center;
  justify-content: center;
}

.left{
  text-align: left;
}

.right{
  text-align: right;
}
.danger{
  font-weight: 800;
  text-decoration: underline;
}

.exit{
  text-decoration:italic;
  font-size: 20px;
}

.red{
  color: red;
}

.green{
  color: green;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
