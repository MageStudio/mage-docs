# Setting up your project

## index.html

First things first, you will need to setup a `index.html` page somewhere in your project folder. The page should look like something like this:

```html
<!DOCTYPE html>
<html>
    <head>
        <link rel="stylesheet" href="/dist/bundle.css">
        <script type="text/javascript" src="/dist/bundle.js"></script>
    </head>
    <body>
        <div class='loader'/>
        <div id="ui"/>
        <div id="gameContainer"/>
    </body>
</html>
```

The structure of the page is completely up to you, but two elements are required:

- `<div id='ui'/>` is the ui container. This is where your UI will render. An entire section of this docs is related to how to enable and work with your UI.
- `<div id='gameContainer'/>` is the game container. Your scenes will be rendered inside this element. The id of this element can be changed to whatever suits your needs.

Both elements can be styled freely.

> As you can see, we're referring to `/dist/bundle.css` and `/dist/bundle.js`. This means we're going to assume you will have a bundling tool installed, and that you have a basic understanding of how they work. If you find yourself stuck, please refer to [Bundling examples](/getting-started/2_1_bundling_examples.md).

---

## index.js


You project needs an entry point, which we will call `index.js` . It needs to look like this:

```js
import { Router } from 'mage-engine';
import Scene from './first/Scene';

const assets = {};
const config = {};

window.addEventListener('load', function() {
    Router.on('/', Scene);
    Router.start(config, assets, '#gameContainer');
});
```

Explanation:

Mage is using an internal Router to bind Scenes to url fragments.

You can import Router by doing `import { Router } from 'mage-engine'` . As you can see in this example, we're using the `load` event on the window object to configure Router and start our application.

- `Router.on('/', Scene)` : this line is performing the binding between the base route and your Scene. This means that when the user will navigate to `http://whereveryourapp.is` , the `Scene` will be executed.
- `Router.start(config, assets, '#gameContainer')` : this is what starts the application. This method requires three parameters: config, assets, and the id of the DOM element where your scenes will be rendered.

The last thing is the scene import line: `import Scene from './first/Scene';`.

This line is obviously just importing the Scene from where you defined it. There are no constraints on how you name your scenes or where you define them.

> More informations on Router, how to configure your app or how to define and load your assets can be found here:

[Router](/)

[Configuration](/)

[Assets](/)

---

## What's next

You're now ready to create your first scene.

[Creating the first scene](/getting-started/3_creating-first-scene.md)