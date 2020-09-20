# Mouse

Controlling mouse input allows you to detect interactions with elements of your level, as well as regular mouse-screen interactions.

---

## Enabling Mouse

Enabling Mouse input is straightforward:

```js
import { Input } from 'mage-engine';

// somewhere inside your app
Input.enableMouse();
```

> The Mouse module will be available as `Input.mouse`.

---

## Events

?> All the following events have listeners in your Scene, according to the following pattern: for each event, the listener that will be used is `onEventName`, assuming that the event is `eventName`. Note that the difference between the listener name and the event name is the upperCase event name preceded by the prefix `on`.

If you want to set up listeners in your scripts, you have to:

```js
import { Input } from 'mage-engine';

// inside your script
start() {
    Input.enableMouse();
}
```

---

## Methods

---

## Disabling

