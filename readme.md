# Parcel, Module Bundler

> 🔨 How to configurate Parcel. From '[grafikart.fr](https://dev.to/nanosoftonline/react-hot-loader-with-web-dev-server-aop)'.
>

![parcel-logo](img-readme/parcel-logo.png)


*Parcel.js is a bundler just like rollup, webpack, browserify but its zero-config/no-config and supports bundling the whole web app not just javascript files. Although few bundlers are only Javascript centered. Bundlers like Webpack, Parcel.js are web app bundlers which includes Javascript, it's variants and the whole ecosystem, Images, Stylesheets, Template engines.*

## Concepts

- Assets: Out of the box support for JS, CSS, HTML, file assets. Parcel Detect all the dependecies declare them and build a tree with dependencies

- [Transformers](https://github.com/parcel-bundler/parcel/tree/v2/packages/transformers): Babel, PostCss... to transform the code.

- [Packagers](https://github.com/parcel-bundler/parcel/tree/v2/packages/packagers): manage behaviours a the end of the chain.

## How to use?

`npm init`

`npm i -D parcel-bundler`

To launch local server:

`parcel serve index.html`

It will create *.dist* and *.cache* directories.

Launch: `http://localhost:1234 `

To build optimized files (css and js minified):

`parcel build index.html`

## CSS preprocessor: Sass

If we add a scss file, Parcel will automatically download node-sass.

Warning: we need to use quotes for url:

````scss
body {
  background: $backgroundColor url("./parcel-js-bkgr.jpg");
}
````

## CSS postprocessor

Create *.postcssrcrc* at the root with:

````json
{
  "modules": false,
  "plugins": {
    "autoprefixer": {
      "grid": true
    },
    "css-mqpacker": {
      "sort": true
    }
  }
}
````

Delete *.cache* before relaunch dev server

Parcel will add *autoprefixer* and *css-mqpacker* and autoprefix and group media queries automatically.

````css
/*autoprefix*/
@-webkit-keyframes demo {
  from {
    transform: scale(0.9);
  }
  50% {
    transform: scale(1);
  }
  to {
    transform: scale(0.9);
  }
}

@keyframes demo {
  from {
    transform: scale(0.9);
  }
  50% {
    transform: scale(1);
  }
  to {
    transform: scale(0.9);
  }
}

/*group media queries that are in 2 different scss files*/
@media screen and (min-width: 756px) {
  .foo {
    background-color: #FF0000;
  }
  .bar {
    background-color: #3cff26;
  }
}
````

## Babel: Converting JS

`npm install --save-dev @babel/core @babel/cli`

`npm install @babel/preset-env --save-dev`

Create *.babelrc* at the root with:

````json
{
  "presets": ["@babel/preset-env"]
}

````
Delete *.cache* before relaunch dev server.

Babel will convert code, for instance `const` to `var`.

## Typescript

If we use Tyscript instead of Javascript, Parcel will convert automatically.

However, It won't be able to do type checking and won't display any error.

## Add plugins

All the plugins begins by 'parcel-plugin'.

For instance let's add, [parcel-plugin-bundle-manifest](https://www.npmjs.com/package/parcel-plugin-bundle-manifest):

`npm install --save-dev parcel-plugin-bundle-manifest`

It will create 'manifest.json'.



## Useful links

- [parcel-bundler/parcel](https://github.com/parcel-bundler/parcel)
- [Using Babel](https://babeljs.io/setup#installation)
- [PostCSS](https://parceljs.org/css.html)
- [What is Parcel.js and how it's faster than webpack?](https://hashnode.com/post/what-is-parceljs-and-how-its-faster-than-webpack-cjrj27c9g01wt84s2elxkdpv5)
- [reactivestack/parcel-react-ssr](https://github.com/reactivestack/parcel-react-ssr)