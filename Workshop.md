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
    > ContentSAKAI - styles that you can use for free
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
	theme: {
		preset: Aura,
			options:{
				prefix: 'p'
				darkModeSelector: "system',
				cssLayer: false
	}		}
});
```

default styles -  we connect through vue. 
specific styles -  we specidy through tailwind classes 

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


