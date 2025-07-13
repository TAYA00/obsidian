---
color: ""
sticker: emoji//1f497
banner: chinigraphy-729Y5P6fmfg-unsplash.jpg
banner_y: "0"
aliases:
---

![[chinigraphy-729Y5P6fmfg-unsplash.jpg|30x20]]
### Script
```html
<script src="https://unpkg.com/vue@3.4.9/dist/vue.global.js"></script>
```
# Lesson 17+18
- connect Vue to HTML
- create Vue app
- connect Vue app to id of HTML element (so you can interact with all child elements)
- specific property of Vue `data() {}` that store components info. Data is a fumktion itself
- how to call Vue object property in HTML tag `{{}}`
- you can output the obj property in `{{}}` that  contain not only text but arrows, numbers, Booleans
- *Interpolation*
# Lesson 19
- how to pass the link (or any value) from Vue app to the HTML tag using Vue directive `v-bind:`
```html
<a v-bind:href="vueLink"></a>
```
where vueLink is a obj property
```js
vueLink: 'https://www....'
```
# Lesson 20
- new specific property `methods{}` where you can place functions that you can call. Its an object that full of functions
- we can call a funk from our Vue app just like the value `{{}}` The funk that we wanna call should be in `methods{}` object
	``` html
	<p>{{ outputGoal() }}</p>
```
%%Task: randomly output each of obj prop%%
# Lesson 21
%% randomize output each of the properties but not as a functions from the `method{}` but as a obj properties from `data()` %%

- create property in `data()`
- call properties from `data()` in `method{}` functions using `this.` and make all manipulations with properties there
```js
data() {
        return {
            courseGoalA: 'Learn Vue!',
            courseGoalB: 'Master Vue!',
        };
}
```


```js
    methods: {
       outputGoal() {
            const randomNumber = Math.random();
            if (randomNumber < 0.5) {
                return this.courseGoalA;
            } else {
               return this.courseGoalB;
            }
        
    }
```
# Lesson 22
- call raw HTML content from Vue app in HTML using `v-html=`
```html
<p v-html="courseGoalC"></p>
```
where courseGoalC has a HTML tag inside
```js
courseGoalC: '<h2>This is a tag inside of Vue</h2>'
```
# Lesson 24
- event binding
- add event listener `v-on:` in HTML to call Vue funk or obj props when specific action was done (click, hover...) 
```html
<button v-on:click="counter++">Add</button>
```
where counter is an obj property in a Vue app with a start value

The result will be shown in the HTML tag after buttons with event listener, where we call our obj prop. Vue automatically count and renew the result
```html
<p>Result: {{ counter }}</p>
```

General: updating events through event listeners in HTML directly
# Lesson 25
put the logic for event listeners into the Vue app code using `methods{}` and call them in HTML through `v-on`

```js 
 methods:{
    addCounter(){
     this.counter2 = this.counter2 + 1; // or this.counter2++
    },
    removeCounter(){
     this.counter2 = this.counter2 - 1; // or this.counter2--
    }
  }
```

```html
<button v-on:click="addCounter">Add</button> 
<button v-on:click="removeCounter">Reduce</button>
```
we don't need to put () when we call function through `v-on` 

# Lesson 26
event arguments


- make the program more complex, so that we don't write the specific number in `methods{}`  functions, but we accept parameter that we assign in HTML in `v-on`
	So that is easier to change the value
```html
<button v-on:click="add(5)">Add</button>
```
so that 5 is a value of a num
```js
methods{
	add(num){
	   this.counter3 = this.counter3 + num;
	},
	
	remove(num){
	   this.counter3 = this.counter3 - num;
	}
}
```

# Lesson 27
- working with input. Show the inputted name dynamically in paragraph
- event handling and 2-way-binding (we "listen" to the event listener )
	- `v-on:input` (or `@input`) listens for the `input` event
	- Every time user types in the input field, `setName` method is called
	- browser automatically passes the event object to the method
```html
<input type="text" v-on:input="setName">
```

```js
methods: {
  setName(event) {
    this.name = event.target.value;
  }
}
```
where `event.target.value` gets the current value of the input

%% JavaScript `value` property = "what's actually in the box right now"%%

- add default event obj that stay in the input field together with dynamic input event
```html
 <input type="text" v-on:input="setLastName($event, 'Schwarz')">
 <p>Your Lastname: {{ name }}</p>
```
where Schwarz is the default value that we assign

```js
 name: ''
 
 setLastName(event, lastname) {
      this.name2 = event.target.value + ' ' + lastname; 
    }
```
where event is a dynamic input ans lastname is a default val that we assign in HTML

- `$event` is Vue's way of passing the **actual browser event object** to your method. **With extra parameters:** You must explicitly use `$event` to get the event object
# Lesson 28
- event modifiers
- for example event like reloading the page after sending the form - to avoid `v-on:submit.prevent` `.prevent` is to remove browser default 

# Lesson 30

### Programm a reset button
- add reset button for input 
- add reset method and clear this input :
	- we use the `data()` property `name=''` and output it in input stroke as `v-bind:value="name"`. 
	- in resetInput() methods function and set `this.name = ''` - this value should be reflected in input
	- in setName()  methods function we store entered name `this.name = event.target.value` so that be reflected in input
	- connect button with event Listener `v-on:click="resetInput"`

###  final code
```html
<input type="text"  v-bind:value="name" v-on:input="setName($event, 'Schwarzmüller')">
<button v-on:click="resetInput">Reset Input</button>
<p>Your Name: {{ name }}</p>
```

```js
data() {
	name: '' // початкове значення
}

methods(){
	setName(event) {
	  this.name = event.target.value; // зберігає введнні дані
	},
	resetInput() {
      this.name = ''; // тобто повертає до початкового значення
    }
}
```
so you listening to input and sending stored value back

### Shortcut
`v-model=` - - (”direktive of two-way binding”) Synchronizes data with input fields

it is a shortcut for `v-on:value` and `v-on:input`
```HTML
<input type="text" v-on:model="name">
```

# Lesson 31
- output a full name 
	- create `outputFullName()` methods function
	- call it in `p` that show result of input `<p>Your Name: {{ outputFullName() }}</p>` so that we output name with assigned last name
	- add check with if , so that when it's nothing in input - it show nothing and when yes - output name + last name
```HTML
<input type="text" v-model="name">
<p>Your Name: {{ outputFullName() }}</p>

```


```JS
outputFullName() {
      if (this.name === '') {
        return '';
      }
      return this.name + ' ' + 'Schwarzenegger';
    },
```

> [!NOTE]
    > BUT with `{{ outputFullName() }}`  this method will be re-executed by Vue, whenever smth changes on a page (for example counter)

Methods should not be used to output dynamically calculated value

#  Lesson 32
to avoid execution of all methods simultaneously - we use <mark style="background: #FF5582A6;">computed properties</mark>.
Vue will execute them **ONLY** one of the dependencies changed.

`computed:{}` - inside we define methods

- we write prop that will be functioning as a `data()` prop, so we name it as it will be in data
	`fullname() {}`
- inside we place the code that was it our method `outputFullname()`
	```JS
	computed: {
		fullname() {
	      if (this.name === '') {
	        return '';
	      }
	      return this.name + ' ' + 'Schwarzmüller';
		}
	}
	```
- we POINT at it and doing it WITHOUT ()
	```HTML
	<p>Your Name: {{ fullname }}</p>
	```

# Lesson 33
<mark style="background: #FF5582A6;">watchers</mark> - func that tell Vue to execute, when **one of dependencies  changed**
you can use watchers instead of computed props.

`watch:{}` - it is an obj. You repeat `data()` or `computed:` props inside of `watch:`. And it will be executed, whenever the data/computed prop changes. Inside of copied prop we specify any logic
```JS
watch:{
	name(value){
		this.fullname + this.value + ' ' + 'Schwarzmüller';
	}
}
```
watch func gets the last val from data prop with the same name - so we don't have to refer to it. And just write `value`


> [!NOTE]
> better not to use it but use computed

![[image.png]]
# Lesson 35
`v-on:click` shorthand -> `@click`
`v-bind:value` shorthand -> `:value`

# Lesson 36
dynamic styling - change in Vue styles in reaction to smth

Task: when clicking on div - it highlights
- in `data()` we control which div is selected
- in `methods:` - fire when div is clicked (write our logic)
- `@click="boxSelected('letter that we assign to div')"` - to call our method on event listener click
- to apply style for dynamic val - we use `:style=''`
- in Vue we can write styles not like a normal CSS, but trough **the object**. Where you could also write the conditions, when does this style will apply

> [!NOTE]
    > This works ONLY with Vue
```HTML
<section id="styling">
<div class="demo" :style="{borderColor: boxASelected ? 'red' : 'grey'}"  @click="boxSelected('A')"></div>
<div class="demo" :style="{borderColor: boxBSelected ? 'purple' : 'grey'}" @click="boxSelected('B')"></div>
<div class="demo" :style="{borderColor: boxCSelected ? 'pink' : 'grey'}" @click="boxSelected('C')"></div></section>
```

```JS
const app = Vue.createApp({
    data() {
        return {
            boxASelected: false,
            boxBSelected: false,
            boxCSelected: false,
        };
    },
    methods: {
        boxSelected(box) {
            if (box === 'A'){
                this.boxASelected = true;
            }else if (box === 'B'){
               this.boxBSelected = true;
            }else if (box === 'C'){
               this.boxCSelected = true;
            }
        },
    }
});
app.mount('#styling');
```

# Lesson 37
bins CSS clases dynamiccaly

- create CSS class
```CSS
.active{
  border-color: red;
  background-color: salmon;
}
```
- we assign dynamically class with `v-bind:class`
- pass an obj `class:"{}"` and add property `demo`
	- name of that prop reflect on CSS class
	- value of `demo` have a Boolean value that indicate  if the class should be added
	```HTML
	<div
	:class="{demo: true, active: boxASelected}"
	@click="boxSelected('A')"
	></div>
	```
	that means "add class active(with assigned styles) when boxASelected is true"

- to be able to unselect boxes we just add in our ` boxSelected(box)` method !
```JS
// instead of 
if (box === 'A'){
	this.boxASelected = true
}
// we write 
if (box === 'A'){
	this.boxASelected = !this.boxASelected
}
```

> [!NOTE]
    > watch vids 38 and 39 (34,34 in coursehunter) one more time

![[image-1.png]]
> [!NOTE]
    > make the a Section 3,4,5,6

# Lesson 41
conditional content & Lists
	- rendering content with conditons
	- output list of data
	- optimisation