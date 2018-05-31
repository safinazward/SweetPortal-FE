# Sweet Portal

> Web app based on Polymer 3.x , Webpack, PostCSS.

## Tech/framework used

* [Webpack](https://webpack.js.org/) 4 with [MiniCssExtractPlugin](https://github.com/webpack-contrib/mini-css-extract-plugin) to bundle js files and extract css.
* [webpack-dev-server](https://github.com/webpack/webpack-dev-server) with hot reloading active.
* [PostCSS](http://postcss.org/) with many plugins.
* Copy statics file on `dist` folder (like `vendor/webcomponents-loader.js` and others)
* **ES6 modules bundle and ES5 transpiled bundle** both handled using the new `nomodule` and `type=module` feature of modern browsers. [Learn more on how to ship ES6 modules today in production](https://www.youtube.com/watch?v=GWmO88hBbKY).
* [Bootstrap](https://getbootstrap.com/docs/4.0/getting-started/introduction/) 4 Sleek, intuitive, and powerful front-end framework for faster and easier web development. 

#### Loaders

* [babel-loader](https://github.com/babel/babel-loader) with the [babel-preset-env](https://github.com/babel/babel-preset-env) enabled for the [**last 2 versions**](https://babeljs.io/docs/plugins/preset-env/) and babel-plugin-transform-object-rest-spread installed.
* [text-loader](https://github.com/dfenstermaker/text-loader) - Load HTML templates as string.
* [postcss-loader](https://github.com/postcss/postcss-loader) - Load PostCSS into the `<style>` scoped tag of Polymer elements as string.
* [sass-loader](https://github.com/webpack-contrib/sass-loader) - Compiles Sass to CSS.




## Supported Browsers

All modern browsers. 🕶

But as the features said, we are also transpiling the bundle for "oldie" browsers.

## Usage

#### Prerequisites
1. Install [Nodejs](https://nodejs.org/en/) to use npm package manager.

2. Clone this repository:

```bash
git clone linktorepo [your-app-name]
```

3. Install the dependencies in the local node_modules folder. 

```bash
npm install
```

#### Developing

Start the `webpack-dev-server` on localhost `http://localhost:3000` with hot-reload and watch on `.pcss` files.

For "oldie" browsers, transpiling also Javascript `class`. Works on `Firefox`:

```bash
npm run dev
```

For modern browsers with `class` support. Works on `Chrome`, `Safari`, and `Edge`:

```bash
npm run dev:module
```

#### Test

XO for code style, Stylelint for PostCSS linting, and WCT for components tests:

```bash
npm run test
```

Run [Lighthouse](https://github.com/GoogleChrome/lighthouse) for testing the PWA capabilities:

```bash
npm run test:lighthouse
```

#### Build

(Almost) production-ready (`webpack --optimize-minimze` and copy statics) to `dist` folder. Also generating Service Workers. The command will also create the `module` version of the `bundle` ready to be loaded as `type=module`.

```bash
npm run build
```


## Styling components with PostCSS

During development `.pcss` files will be watched, compiled and injected to the relative `<style>` tag within the component template. The CSS is scoped to the component so don't worry about CSS specificity, you can also use `:host`, `:host-context` and `:root` selectors. Read more about [styling web components](https://www.polymer-project.org/2.0/docs/devguide/style-shadow-dom) and [custom CSS properties](https://www.polymer-project.org/2.0/docs/devguide/custom-css-properties).

We also include Autoprefixer plugin, if you don't know how it works (...and you should), it allows you to write CSS without worrying about vendor prefixes. Just write your css properties prefix-free and let autoprefixer do the work for you when compiling.

**How about commons styles?**
You can simply `import` any other `.pcss` file within your main component `.js` file and print it inside the `template()`.


## [**@webcomponents/webcomponentsjs**](https://github.com/webcomponents/webcomponentsjs)

We are getting the `webpcomponents-loader.js` polyfill from GitHub using NPM and copying it into a `vendor` folder with a `Node` script.


## custom-element-es5-adpater.js

Loading the `custom-element-es5-adapter.js` is necessary because the `custom elements` [known(1)](https://stackoverflow.com/questions/43520535/class-constructor-polymerelement-cannot-be-invoked-without-new/45097891#45097891) [issue(2)](https://github.com/webcomponents/custom-elements#es5-vs-es2015) (the lovely `Uncaught TypeError: Class constructor PolymerElement cannot be invoked without 'new'`) about ES6 `classes`, but just on **old browsers**.


## License

 © MIT
