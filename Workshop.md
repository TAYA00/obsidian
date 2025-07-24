---
sticker: lucide//album
---
Pass for Rechner: 412365

Softare: :
VS Code
Vue library 
next js
smartgit
git

phind AI
powershell cheatsheet
# Notes on workshop
in powershell change the policy -  in settings -> system -> developer
(in you can change date explorere also smth )

## Backend 
`npm install` 
Import in JSON:
postgre SQL pg
uuidv4  pakage - easier to work
express - framework
.m - daten in datei zu lesen. COnfig Daten in lesbar Format abzulegen


express middleware framework:

router Dateien - benutzen Kontroller. Kontroller is 
get func is a middleware (logn f example) damit wir zusamentecken kann. 

controller - middleware func (enthalt from router)middle ware

WTF is design pattern

model - datenbank zugraff
Controller - zugriff zugraff zu HTTP (constrains in controler)
rest API 

in Datenmodel so viel wie moglich constrains zu packen

in datenbank kann mann permissions festlegen

wir haben kein Kontroller in Datanaut datenbank

vererbung - was ist das


##  Frontend
Make Frontend File
new Vue proj with Vite

`npm create vite@latest`
we give a proj name "Proj Kalkulater"
vite - system frontend build tool 
- entwicklung server
- erweiterung for Vue 
ESM-import - module system of JS

in framework choose - TS
unter welche order mochten wir dies erstellen (specify)
`npm install`
`npm run dev`

prime vue installieren
(we use components and inputs from there)
- Tailwind CSS 


in Vue verwenden wir Capitilize for TS snake_case/kebab-case
Midestenz 2 words verwendem

Es hat Ts, style, app von Vue wo dies HelloWorld componente drin
- estellen eigene Komponenete in components folder

We make composition API (teamplate in Vue website)
```VUE
import 
const count and variables
func 
```

``` JS 
<template>
	// for UI
</template>

<script>
	
</script>
```
- controlles
- models
- rouotes

### Prime Vue
`npm create vue@latest`

`proj name`
`choose lang`
`mv`

.vscode inside of Frontend folder that we just created
`git add`
`git create -m`

`npm  run dev `
npm run dev run the dev obj from package.json (what is the diff between run serve and run dev ask one more time chat GPT)

> restart TS server 

-------------- begin of prog --------------------
### 1. Install i18

`npm install i18next-vue`
`npm install http-backend`



i18nextvue - plugin 
we use $t{ "key name"}

we put import and nitialisation code frm i18next website  in main.ts file
Hello World.vue we make call of i18next obj throgh t function

in main.ts we call the i18 initialisation script (in website)
we rite there directly 
```js
i18next  
  .use(HttpApi)  
  .init({  
    fallbackLng: 'de',  
    debug: false,  
    interpolation: {  
      escapeValue: false  
    },  
    backend: {  
      loadPath: 'translation.json'  
    }  
  });

export default i18next
```

and all translatons we put at the separate JSON (like translation.json)

### 2. Install prime Vue (vite)

`npm install prive vue` 
`npm i primevx/theme`
``
go to main.ts and place on the initialisation i18code also import primevue:
`import PrimeVue from '...'`
`import Aura from '...'`
`import Button from '...'`

`const app = createApp(App)`


`and app.use(PrimeVue)` 

in App.vue and delete template that we has 
``` JS 
<template>
	<button></button>
</template>

<script>
	import Button from "primevue.button"
</script>
```

%% how to import components from prime vue and integrate them in project%%

### 3. Tailwind CSS
%%taiolwind css cheat sheat%%
%% download extension tailwind css %%
entweder ohne style oder in style mode verwenden oder Volt nutzen (von 0 styles aufbauen)

styled mode - ?
unstyled mode - ? 

Tailwind 4 - nutzen wir

**We need 3 sets of Tailwind CSS**
- tailwind css `npm i tailwindcss`
- tailwind vite 
- tailwind prime vue




in assets/main.css  file we import tilewind 
`@import ...`  %%in website there is a full code%%
```CSS 
@import: "tailwindcss";
@import: 
```


in the` main.ts` we put inside of initialisation the configuration. We have to put in the right order because it cascade
vue 


tailwind work as a bootstraop with through classes 

```js
<template>
	<button label="label" class="styles for button"></button>
</template>
```


in `vue.config`  we also inport tailwind and set plugins


you can pack aal styles in other css file, thereore its more  well-organized

in main.css
```CSS 
@layer components{
	.sub-menu{
		@apply (then you write styles)
	}
}
```


> [!NOTE]
    > https://sakai.primevue.org/documentation
    > check there the styles  for prime vue 



### 4. Import components
 in `configurator.vue` - we import script for component of our calculator (in App.vue we paste the template for this component that we need)

new component products vue

### 5. Zugriff zu Datenbank
`npm i axios`
in App.vue 
`import axios from 'axios' `
`data.const = axios.get("...")`


ich muss von backend erauben dass daten from frontend geladen sind
`npm i cors ` there is other install command for TS
in index.ts `import cors from 'cors'` und `app.use(cors())`

Entweder Bend und Fend in gleichen port oder 2 verschiedene serv entsntanzen

in ProductVue 
```js 
<template>
<label>{{data}}</label>
</template>
<script setup lang="ts">
import axios from 'axios'
import {onMounted, ref} from 'vue'

const.data = ref("");

onMounted (async () => {
	try{
		const.response = await,axios.get ('http:licalhost.3000/products');
		data,value = response.state;
	}catch{
		console.error ('...', error);
	}
});
</script>

```
###  Daten aus  dem Datenbank abzufragen
download postman VS Code extension
in backend/routes zuerst Product
```TS 
router.get (/products/, fetchallPpducts) // we have to call specific product
```


**we workimg with props**
in App.vue - we take id from TS file ans place it in сіі
```
ProductView product-id ('...')
```
in ProductView.vue 
```JS 
<template>
<label>{{data}}</label>
</template>
<script setup lang="ts">
import axios from 'axios'
import {onMounted, ref} from 'vue'

const.data = ref("");
const props = defineProps (['product.id']);

onMounted (async () => {
console.log(props)
	try{
		const.response = await,axios.get ('http:licalhost.3000/api/product$props['productId]');
		data,value = response.state;
	}catch{ 
		console.error ('...', error);
	}
});
```

### editions und modules dazu laden
in ProductView.vue 
```JS 
<template>
<label>{{data}}</label>
</template>
<script setup lang="ts">
import axios from 'axios'
import {onMounted, ref} from 'vue'

const.data = ref("");
const props = defineProps (['product.id']);

onMounted (async () => {
console.log(props)
	try{
		const.response = await,axios.get ('http:licalhost.3000/api/product$props['productId]');
		data,value = response.state;
	}catch{
		console.error ('...', error);
	}
});
```

css bauen

mit input anfangen mit Matheus 



# 22.06
plan für Diese Woche machen

###  Installed packages
you have to go direcrtly to file with your proj
- in terminal 
	`npm create vue@latest` 
		- set proj name 
		- welche sprache benutzen: TS
	`npm install`
	`npm install primevue`
	`npm install primeicons`
	`npm install primeuix/themes` -?
	`npm install vite.js/plugin-vue`   
	`npm install -D @tailwindcss/latest postcss@latest`
	(make shure that node is installed )
	`npm run dev` -  to check if the vite indstalled and 


in main css`@import 'tailwindcss'` 

in vite.config.ts 
```TS
import { defineConfig } from 'vite'
import tailwindcss from '@tailwindcss/vite'
export default defineConfig({ 
	plugins: [ 
		tailwindcss(), 
	],
})
```

%% router -  route to another page %%

### Project structure:
- public
- src - what we set for frontend 
- assets - globally used files (main.css, base.css, svg) styles
- components - we write components (elemente in proj [toast]). We use it to separate proj and dont write it in one big file
- icons - Vue have own icons, so we dont have to put it manually in our proj. We can set only specific f.E logo
	`npm install primeicons` - to install icons package

all icons we import in main.ts 
``` TS
import 
import 'primeicons/primeicons.css'
```

but for component in main.ts
``` TS 
import inputNumber from '.../...'
App.component ('InputNumber', InputNumber)
createApp(app).mount('App')
```
for primevue general in main.ts
``` TS 
import 
App.use (PrimeVue [])
```


in App.vue we show the needed icon/component through


> [!NOTE]
    > Contentstyle scoped in components -  styles for current component and only latest

App.vue -  take all component and call them 
```VUE
// structure of App.vue
<template> </template>
<script> we link our components </script>
```

> [!NOTE]
    > components in Vue - allow us to split the UI into independent and reusable pieces
![[Pasted image 20250722125737.png]]
### Adjust App.vue

### Componente 
- toast - for notifications
- card + select-button - for edition
- buttons + - module %% soll flex %% 
- carousel+ buttons - for features die Module oder Editionabhöngig sind (includes features will be shown static in the summary) 
- card - overlay-panel - for dinamic price 
- panel - for all extras that are included (we will show first 3 and then all other). Will be imported  as an array 
- submitt button 
### Connect Components

in main.ts you register the component
```TS
import Button from 'primevue/button';
```
to use it 
```TS
const app = createApp(App)
	app.component('Button', Button);
app.mount('#app')
```

in App.vue
```JS 
<template>
	<Button class="font-bold">Start</Button> 
	// we set styles specifically for element with tailwind
</template>
```

### Connect styles
> [!NOTE]
    > SAKAI - styles that you can use for free
design token -  key with the value 

```JS 
// in main.ts 
import PrimeVue from ' primevue/config';
import Aura from '@primevue/themes/aura';
import './assets/main.css';

import{ createApp }from 'vue'
import App from './App.vue'

import Button from 'primevue/button'

const app = createApp(App);
app.use(PrineVue,{
	// Default theme configuration
	unstyled: true, //  very important to apply theme 
	theme: {
		preset: Aura,
			options:{
				prefix: 'p'
				darkModeSelector: "system',
				cssLayer: false
	}		}
});
```

> [!NOTE]
    > the `unstyled: true` option in PrimeVue is **necessary** when you're applying **custom themes** to disable pre-styled CSS

default styles -  we connect through vue. 
specific styles -  we specidy inside of  tailwind classes 

test.vue 

copy from App.vue and paste in in test.vue
```JS 
<template>   
	<main>
		<p>Hallo</p›  
		<Button class="font-bold">Start</Button> 
	</main>
</template>  
<script setup lang="ts">  
</script>
```

```JS 
// in App.vue
<temaplate>
<test/> // we link App.vue with test/
</template> 
<script>
import test from './components/buttons/test.vue'
</script>
```

### Set the edition component

import card inside of main.ts 

```TS
import Card from 'primevue/card';
```

and link the component
```TS
app.component('Card', Card);
```

Editions.vue
```JS
<template>
  <Button>
    <Card>
      <template #title>
        <span>Click Me Card</span>
      </template>
      <template #content>
        <p>This card looks like a card, but acts like a button.</p>
      </template>
    </Card>
  </Button>
</template>
```

we have to write flex styles my ourself

### Connect to backend
go to backend and `npm run div`
see routes and search path in .get in index.ts watch the number  of server
in index.ts 
```TS
// index.ts
const app = express;
const port = 3000;
app. use(express. json));
I
app.get('/', function (_req, res) { 
	res.send ('Bienvenue sur la calculatrice');
});
app use('/api', productRoutes); // part of url that we need 
app.use('/api', editionRoutes);
app.use('/api', moduleRoutes);
```
in editionRoutes there is rest of URL
```TS
router get('/edition/', editoionRoutes)
```

> [!NOTE]
    > knex - postgress verbindung

`interfaces.ts` -  write structure of database (for info)
`services.ts` - call variables from Database

### dx
in Editions.vue 
```vue
<script setup lang = "ts">
	import { getEdition } from '../../services/services' // import backend service
	import type { Edition } from '../../services/interfaces'
	import Button from 'primevue/button'
	import { ref, onMounted } from 'vue'
	const editions = ref<Edition[]>([]) // create reactive list, so when data is loaded, the UI updates automatically
	async function loadEditions () { // defining a  Async Function to Load Data
		try{
			editions.value = await getEdition ( ) // calls get edition
			console. log( 'Editionen:', editions.value) // store result in editions.value
		} catch (err) {
			console.error ('Fehler beim Laden der Editionen:', err)
		}
	function handleMounted(){ // lifecycle hook that runs when the component is first displayed
		loadEdition() // to fetch the data from the backend immediately
	}
	onMounted(handleMounted)
</script›

<template>
	<main>
		// displays data in template. Loops through editions and display each edition obj
		<Button v-for="edition in editions" :key="edition.edition_id">
			{{ edition.name }} <br> // call things from backend 
			{{ edition.price }} <br>
			{{ edition.included_module_count }}
		</Button>
	</main>
‹/template>
```

We create `Configurator.vue` file. That is the main file that we will use for Calculator UI and for all links to components. We don't use `App.vue` anymore

    
> Tasks:
file to call all  for summary 
make structure of website 
make modules selectable (clickable) and build price card with logic


emit - cancel, save. Emmited ein aktion

# 24.06
editionen:
- verbindung with Frontend und Backend erstellt
- dynamisch display von Edition 
- Buttons benutzt: clickable, Anzahl von Module, Preis, 


to-do:
- start developing modules 
	- connect to backend
	- dinamically display modules from backend
	
- in Module.vue 
	- name 
	- nach positionsortieren 
	- clickable

# Anpassungen 24.07

###  Configurator.vue 
```vue
// added Modules component
<Modules :selectedModules="selectedModules" :selectedEdition="selectedEdition" @select="selectedModules = $event" />
```

`v-vind: :selectedModules` -  pass the Modules array that is located inside the props in the file `Modules.vue`
pass `v-vind :selectedEdition` - pass the editions that is located inside the props in the file `Modules.vue`

``` js
import type { Module } from './services/interfaces'
// pass the array of modules through const, that we will use in Modules.vue
const selectedModules = ref<Module[]>([])
```

### Modules.vue
```js
// import also editions to use it for Toast
import type { Edition } from '../services/interfaces'
```

```js
// declare var that passes Modules array
const modules = ref<Module[]>([])
```

```js
// in props we passed const that we declared in Configurator.vue
const props = defineProps<{
  selectedModules: Module[]
  selectedEdition: Edition | null
}>()
```
### function only with alert and multi-select

```js
function selectModule(module: Module): void {
  if (!props.selectedEdition) { // is selectedEdition is false
    toast.add({
      severity: 'warn',
      summary: 'Hinweis',
      detail: 'Bitte wählen Sie zuerst eine Edition aus.',
      life: 3000,
    })
    return // exit this function (like break in java)
  }
  // check if selected module exists in selectedModules using some()
  // m is a short name
  const exists = props.selectedModules.some((m) => m.module_id === module.module_id) 
  if (exists) { // if module already selected
  // we delete module from array
    const filtered = props.selectedModules.filter((m) => m.module_id !== module.module_id) 
    // sends this updated array without module to the parent component via the `select` event
    emit('select', filtered)
  } else { // if module not selected
  // we add new module to selected
    emit('select', [...props.selectedModules, module])

  }
}
```
### function with alert abt edition,abt modules limit and  multi-select 
```js
// add limit of alerts.This is a reactive value that by default has value false
const limitExceededShown = ref(false)
// watch that reset .value = false
watch(() => props.selectedEdition, () => {
  limitExceededShown.value = false // allows you to show the toast again
	// false - we show the toast
	// true - don't show toast again
})
```

```js
function selectModule(module: Module): void {
// ------------------------ part that styied
  if (!props.selectedEdition) {
    toast.add({
      severity: 'warn',
      summary: 'Hinweis',
      detail: 'Bitte wählen Sie zuerst eine Edition aus.',
      life: 4000,
    })
    return
  }
  const exists = props.selectedModules.some((m) => m.module_id === module.module_id)
// ------------------------ new
// just put the if statement in variable that check if the module already selected
  let updatedModules = exists
    ? props.selectedModules.filter((m) => m.module_id !== module.module_id)
    : [...props.selectedModules, module]

  
// pass the module count and inclusivity 
  const limit = props.selectedEdition.included_module_count
  const unlimited = props.selectedEdition.included_all_modules

  
/* if edition doesn't have unlimited modules 
- AND selected modules count MORE THAN included module count 
- AND the toast is not shown yet (if value of limitExceededShown is !true (which means false) */
  if (!unlimited && updatedModules.length > limit && !limitExceededShown.value) {
	// we pop the alert
    toast.add({
      severity: 'info',
      summary: 'Zusätzliche Module',
      detail: `Sie haben mehr als ${limit} Module gewählt. Weitere Module kosten je 2500 €.`,
      life: 4000,
    })
    // set it to true - to not show it again
    limitExceededShown.value = true
  }
  emit('select', updatedModules)
}
```
> [!NOTE]
    > `const баночка = ref("чай")`
    > `console.log(баночка)`  // це баночка з етикеткою
    > 	{ value: string } бо баночка це об'єкт
    > `console.log(баночка.value)`   // це сам чай :)

```js
function getButtonClass(module: Module): string[] {
// same thing check id modue exists in seectedMody=ules
  const isSelected = props.selectedModules.some((m) => m.module_id === module.module_id)
  return [ // this is not conditional
    'w-full min-h-[5rem] rounded-lg font-semibold text-center flex items-center justify-center',

    'transition-colors break-words text-wrap leading-snug',

    'text-xs sm:text-sm md:text-base px-2 py-2',
    isSelected 
      ? 'bg-[#bcd000] text-[#082028]' // if module selected
      : 'bg-[#082028] text-white hover:bg-[#bcd000] hover:text-[#082028]' // if not

  ]

}
```