---
color: ""
sticker: emoji//1f497
---
```html
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
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
- for example event like reloading the page after sending the form - to avoid it 