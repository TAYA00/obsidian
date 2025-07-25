---
sticker: lucide//calculator
---
1. Install i18n
```
npm install
```
when not working (because of newest version in VS Code) **optional**
```
Remove-Item -Recurse -Force .\node_modules  
Remove-Item -Force .\package-lock.json
```
2. then install LanguageDetector
```
npm install i18next i18next-http-backend i18next-browser-languagedetector vue-i18next
```
3. Run the Proj
```
npm run serve/dev
```


if you wanna say programm that this is the public version **option**
```
npm config set registry https://registry.npmjs.org/
```


`npm run build`  - this will me compiled in dist folder
> [!IMPORTANT]
    > Make a old version backup of previous program on your computer from Filezilla in website server

Go to `index.html` in dist project folder and copy path from original index.html so it will be like in Fazilla 
%% everything before /js… and /css…%% 

Drag and drop all files from local git folder in Filezilla server and push „Überschreiben“

# Amortisation Rechner (ohne checkboxen)

## i18next.js
create folder lacales with translation.json in the public folder of project

```js
import i18next from 'i18next'
import LanguageDetector from 'i18next-browser-languagedetector'
import HttpApi from 'i18next-http-backend'
i18next
  .use(HttpApi)
  .use(LanguageDetector)
  .init({
    fallbackLng: 'de',
    debug: false,
    interpolation: {
      escapeValue: false
    },
    backend: {
      loadPath: '/includes/rechner/amortisation/locales/translation.json'
    }
  });
export default i18next
```
## main.js  
import i18next
```js
import { createApp } from 'vue'
import App from './App.vue'
import { library } from '@fortawesome/fontawesome-svg-core';
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';
import { faCircleInfo, faCircleQuestion, faSquareXmark, faXmark } from '@fortawesome/free-solid-svg-icons';
import 'vuetify/styles'
import { createVuetify } from 'vuetify'
import * as components from 'vuetify/components'
import * as directives from 'vuetify/directives'
import './i18next'
const vuetify = createVuetify({
  components,
  directives,
})
library.add(faCircleInfo, faCircleQuestion, faSquareXmark, faXmark)
const app = createApp(App);
app.use(vuetify)
app.component('font-awesome-icon', FontAwesomeIcon);
app.mount('#app')
```

## AmortisationCalculator.vue
extra geschickt

### main changes
in template we have to write instead of text this link
`{{ t("one_time_project_costs") }}` - one_time_project_costs this is the name of our object

pay attention to change sliders not only in the scrpt, but in template
```vue
<div v-for="(slider, index) in sliders" :key="index" class="mb-4">
            <p class="mb-0">
              {{ t(`slider_${index}.name`) }}
              <a @click="showModal(index)" href="javascript:void(0)" class="icon">
                <font-awesome-icon :icon="['fass', 'circle-question']" />
              </a>
            </p>
```

in script import i18
`import i18next from '@/i18next';`
and before `sliders:` don't forget
` ready: i18next.isInitialized,`
after sliders paste this
```js
created() {
    const updateReady = () => {
      this.ready = true;
      this.$forceUpdate();
    };
    if (!i18next.isInitialized) {
      i18next.on('initialized', updateReady);
      i18next.on('loaded', updateReady);
    }
    i18next.on('languageChanged', updateReady);
  },
  beforeUnmount() {
    i18next.off('initialized');
    i18next.off('loaded');
    i18next.off('languageChanged');
  },
```
in `methods:` also past this
```js
 t(key, options) {
      return i18next.t(key, options);
    },
```

check also in showModels funktions, abt
```js
   showModal(index) {
      const key = `slider_${index}`;
      this.modal_label = this.t(`${key}.label`);
      this.modal_text = this.t(`${key}.modal`, { returnObjects: true }) || [];
      this.show_modal = true;
    },
```