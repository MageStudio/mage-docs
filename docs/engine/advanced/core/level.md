# Level

Every level you create must be a class extending `Level` from `mage-engine`, like this:

```js
import { Level } from 'mage-engine';

export default class MyLevel extends Level {
    ....
}
```

## Router integration

In order for your level to be used within your application, you need to link it to the Router module using the `Router.on` method. Since every level is associated to a specific path, you need to provide both path and the Level to this method like this:

```js
import MyLevel from './MyLevel';

window.addEventListener('load', function() {
    const path = '/mylevel';

    Router.on(path, MyLevel);

    Router.start(config, assets);
});
```

?> A more in depth explanation of how the Router module works, how it handles levels and which methods exposes can be found [here](/engine/advanced/router.md).

## Methods

### `constructor(options: object)`

The constructor of your level will receive an `options` object, that will be available within your Level as `this.options`. This object will be provided by the Router module, and it's the representation of the URL query parameters.

**Example**
The user lands on `www.domain.com/?value=10&anotherValue=20#myLevel`. What will happen is that the `MyLevel` Level will be loaded, and the options object will be:
```js
{
    path: '/myLevel',
    value: 10,
    anotherValue: 20
}
```


### `loadScene`

### `enableUI`

### `disableUI`

### `disableInput`

### `toJSON`

## Lifecycle Methods

### `onCreate`

### `onStateChange`

### `onUpdate`

### `onInputEnabled`

### `onInputDisabled`

### `onUiEnabled`

### `onUiDisabled`

### `onBeforeDispose`

### `onDispose`

