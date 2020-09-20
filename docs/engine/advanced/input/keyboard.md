# Keyboard

Handling keyboard is incredibly easy. Under the hood Mage uses the library called [Keypress](https://dmauro.github.io/Keypress/).

---

## Enabling Keyboard

Enabling Keyboard input is straightforward:

```js
import { Input } from 'mage-engine';

// somewhere inside your app
Input.enableKeyboard();
```

> The Keyboard module will be available as `Input.keyboard`.

---

## Events

?> All the following events have listeners in your Scene, according to the following pattern: for each event, the listener that will be used is `onEventName`, assuming that the event is `eventName`. Note that the difference between the listener name and the event name is the upperCase event name preceded by the prefix `on`.

If you want to set up listeners in your scripts, you have to:

```js
import { Input } from 'mage-engine';

// inside your script
start() {
    Input.enableKeyboard();
    Input.addEventListener('keydown', this.onKeydown.bind(this));
    Input.addEventListener('keyup', this.onKeyup.bind(this));
}

onKeydown(event) {
    // do something here
}
```

---

## Methods

---

## Disabling

