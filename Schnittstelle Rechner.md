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