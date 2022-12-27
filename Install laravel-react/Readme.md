# Install Laravel 9 and react 

how to install laravel 9 and react alongside each other

if you use any version of laravel less than 9 , this tutorial won't work out for you 

## Installation
this is base on [this](https://techvblogs.com/blog/how-to-install-react-in-laravel-9-with-vite) tutorial

first in a parent directory

```bash
composer create-project --prefer-dist laravel/laravel:^9.45 laravel9-react-vite
```
move to the project directory then 

now install NPM Dependencies
```bash
npm install
```
then install the latest version of react 

```bash
npm install react@latest react-dom@latest
```
install virejs/plugin-react-refresh

```bash
npm i @vitejs/plugin-react --force
npm i @vitejs/plugin-react-refresh --force
```
remain 'resources/js/app.js' to 'resources/js/app.jsx'

add 'App.jsx' to 'resources/js' then 

```js
// resources/js/App.jsx
import React from 'react';
import { createRoot } from 'react-dom/client'

export default function App(){
    return(
        <h1>How To Install React in Laravel 9 with Vite</h1>
    );
}

if(document.getElementById('root')){
    createRoot(document.getElementById('root')).render(<App />)
}
```
remove the styles from head tag in 'resources/views/welcome.blade.php' and add this
to the end of header

```html
<head>
    ...
    @viteReactRefresh
    @vite(['resources/css/app.css', 'resources/js/app.jsx'])   
</head>
```
replace body tag with the following code 

```html 
<body>
	<div id="root"></div>
</body>
```
