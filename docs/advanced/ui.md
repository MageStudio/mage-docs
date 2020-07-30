# UI

Mage uses [inferno](https://infernojs.org/) as UI library. Why? Because it's fast, uses React-like API, and the entire library is about `7.9kb (minified + gzipped)`, while the couple React + ReactDom is around `38.5kb (minified + gzipped)`. For more informations, have a look on Bundlephobia for [inferno](https://bundlephobia.com/result?p=inferno@7.4.2), [react](https://bundlephobia.com/result?p=react@16.13.1) and [react-dom](https://bundlephobia.com/result?p=react-dom@16.13.1).

## Creating your first UI element

The purpose of this page is not to explain how to craft a beautiful UI, but to help you getting started on how to integrate Inferno with Mage.

You can create a sample UI by creating a new module like so:

```js
import { Component } from 'inferno';

export default class UI extends Component {

    constructor(props) {
        super(props);
    }

    render() {
        return (
            <div>
                <h1>{this.props.title}</h1>
            </div>
        )
    }
}
```

Or, if you prefer being functional:

```js
const UI = ({ title }) => (
    <div>
        <h1>{title}</h1>
    </div>
);

export default UI;
```

From now, you're pretty much good to go, the only thing left is to enable your UI.

## Enabling UI

Each level has a method called `enableUI`.

```js

import UI from './UI';

...
// inside your level
onCreate() {
    this.enableUI(UI, {
        title: 'my game'
    });
}
```

The signature of the method is as follows:
```js
enableUI(rootComponent, options);
```

- `rootComponent` is the root component you want to render.
- `options` represents a list of options for the component.

> When rendering your root component, you can define the DOM element that will contain your UI tree. Mage will try to read the `root` key of the `options` object, expecting a string selector. By default, Mage will use the first element with id = `#ui`. You can find more informations about the level methods [here](/advanced/level.md).

This is what you need to know to get started. For more detailed informations, you can follow the guide on how to connect your component to the Redux store [here](/advanced/state_management.md).