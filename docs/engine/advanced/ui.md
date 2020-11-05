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

The component you just created, `UI`, represents the root component of your application. From here, you are free to do as you please: you have full access to the engine and the redux store.

## Enabling UI

Your UI is automatically enabled when launching your application. What you need to is to define your root component inside the `config` Object received by Router at startup, like this:

```js
import UI from './ui';
import Level from './level';

const config = {
    ui: {
        root: UI
    },
    ...
}

window.addEventListener('load', () => {
    Router.on('/', Level);
    Router.start(config, {});
})
```

This is what you need to know to get started. For more detailed informations, you can follow the guide on how to connect your component to the Redux store [here](/engine/advanced/state_management.md).

## Loading screens

When loading a level, you are responsible to render a loading screen. You can use your existing UI structure for this purpose.

As explained in the [state management page](/engine/advanced/state_management.md), Mage will dispatch actions for your UI as well. In particular, it will update the `ui` entry of the store, allowing you to detect when the loading screen should be visible and when it's safe to remove it.

The following example assumes you have a basic understanding of how Redux works and how you can connect your components to the store. This means your root component can look like something like this:

```javascript
import { connect } from 'mage-engine';

const RootComponent = ({ loadingScreenVisible }) => (
    loadingScreenVisible ? 
        <span>loading...</span> : 
        <MainMenu/>
);

const mapStateToProps = (state) => {
    const { ui } = state;

    return {
        loadingScreenVisible: ui.loadingScreenVisible
    };
}

export default connect(mapStateToProps)(RootComponent);
```

