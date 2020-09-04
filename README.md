# My Awesome Video Gallery (Vuejs/Nuxtjs)

> This video gallery demo is built with Vuejs/Nuxtjs, it is a clone project, see _**reference**_ below, the original project is built with html, css, vanilla javascript, and I built it in Vue way. There is a lot of css codes involved. I personally think it is a good looking design, I like the card very much, the border radius is perfect, the color (both background and foreground) is perfectly matched

## Technology involved in this project
- HTML5 video tag
- CSS Flexbox, Grid
- SSR (asyncData())
- Page PreLoader

## Notes
```bash
 # when you set border-radius of an image, add overflow:hidden to make the radius perfect !!!
 img {
   border-radius: 6px;
   overflow: hidden;
 } 
```

## Build Setup

```bash
# install dependencies
$ npm install

# serve with hot reload at localhost:3000
$ npm run dev

# build for production and launch server
$ npm run build
$ npm run start

# generate static project
$ npm run generate
```

## Deploy to Netlify
```bash
# basic build settings
Build command: npm run generate
Publish directory: dist
```

## Reference
[How To Make Video Gallery In HTML And CSS Website Step By Step Tutorial - Easy Tutorials](https://www.youtube.com/watch?v=wnseY8goQoc)
