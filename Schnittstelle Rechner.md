---
sticker: lucide//calculator
---
1. Install i18n
```
npm install
```
when not working (because of newest version in VS Code)
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
npm run serve
```


if you wanna say programm that this is the public version
```
npm config set registry https://registry.npmjs.org/
```


the first things you find in notion and in notes of your phone


`Npm run build`  - this will me compiled in dist folder
> [!IMPORTANT]
    > Make a old version backup of previous program on your computer from Filezilla in website server

Go to `index.html` in dist project folder and copy path from original index.html so it will be like in Fazilla 
%% everything before /js… and /css…%% 

Drag and drop all files from local git folder in Filezilla server and push „Überschreiben“

Last notes
afer you will write the whole algirithm

`npm install i18next-http-backend`

## i18next.js  
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

## main.js  
import './i18next'

## AmortisationCalculator.vue

in template so schrieben: >{{ t('request_offer') }}

data() {  
    return {  
      ready: i18next.isInitialized,  
      sliders: [  
        {  
          val: 55,  
          max: 150,  
          min: 5,  
          step: 5,  
          symbol: 'h'  
        },  
        {  
          val: 1,  
          max: 100,  
          min: 1,  
          step: 1  
        },  
        {  
          val: 30,  
          max: 100,  
          min: 20,  
          step: 1,  
          symbol: '€'  
        },  
        {  
          val: 1,  
          max: 5,  
          min: 1,  
          step: 0.5  
        },  
        {  
          val: 15000,  
          max: 250000,  
          min: 5000,  
          step: 500,  
          symbol: '€'  
        }  
      ],  
      show_modal: false,  
      modal_label: '',  
      modal_text: []  
    };  
  },  
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
  },v

In AmortisationCalculator.vue
first  
 {{ translation.<mark style="background: #BBFABBA6;">one_time_project_costs</mark> }}
last 
{{ t("<mark style="background: #BBFABBA6;">one_time_project_costs</mark>") }}

{{ t("one_time_project_costs") }}