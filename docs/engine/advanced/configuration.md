# Configuration

In order to configure your Mage application, you don't need to create specific config files. The only thing you need to do is to instruct Router how to start your application: for this to happen properly, you need to provide a basic configuration (for lights, physics, screen and camera configuration) as well as your assets definition.

An example configuration would look like this:

```js
import { Router } from 'mage-engine';
import Intro from './intro';
import First from './first';

const assets = {
    'models': {
        'player': 'assets/models/player.gltf'
    },
    'textures': {
        'playerTexture': 'assets/textures/player.png'
    },

    '/': {
        'models': {
            'modelForThisLevel': 'assets/models/box.gltf'
        }
    },
    '/level': {
        'textures': {
            'spriteTexture': 'assets/textures/sprite.png'
        }
    }
};

const config = {
    screen: {
        h : window ? window.innerHeight : 800,
        w : window ? window.innerWidth : 600,
        ratio : window ? (window.innerWidth / window.innerHeight) : (600/800),
        frameRate : 60,
        alpha: true
    },

    lights: {
        shadows: true
    },

    physics: {
        enabled: false,
        path: './mage.physics.js'
    },

    tween: {
        enabled: false
    },

    camera: {
        fov: 75,
        near: 0.1,
        far: 3000000
    },

    fog: {
        enabled: false,
        density: 0,
        color: '#ffffff'
    },
};

window.addEventListener('load', function() {
    Router.on('/', Intro);
    Router.on('/level', First);

    Router.start(config, assets, '#gameContainer');
});
```

Let's break it down.

---

## Configuration

Mage configuration is split in a few different blocks.

### `screen`

```json
screen: {
    h,
    w,
    ratio,
    frameRate,
    alpha
}
```
- `h: number`: is the height of the area you're using to display your application. If fullscreen, you can use `window.innerHeight`.
- `w: number`: is the width of the area you're using to display your application. If fullscreen, you can use `window.innerWidth`.
- `ratio: number`: is the ratio between `width` and `height`.
- `frameRate: number`: this value will be used in one of the callbacks.
- `alpha: boolean`: This boolean toggles transparency.

### `lights`

```json
lights: {
    shadows
}
```
- `shadows: boolean`: This boolean toggles shadows.

### `physics`

```json
physics: {
    enabled,
    path
},
```

- `enabled: boolean`: This boolean toggles physics.
- `path: string`: This property refers to the position of the physics worker.

?> Mage uses a WebWorker for Physics handling, thanks to [OimoJS](http://lo-th.github.io/Oimo.js/index.html#basic). For more information about enabling and working with Physics, refer to its page [here](/engine/advanced/physics.md).

### `tween`

Mage uses a tweening library to handle smooth transitions from one state tom another. You can enable/disable it using this property.

```json
tween: {
    enabled
}
```

- `enabled: boolean`: This boolean toggles the tweening library.

### `camera`

```json
camera: {
    fov,
    near,
    far
}
```

- `fov: number`: This represents the field of view for your camera.
- `near: number`: This value represents the distance of the `near` plane from the camera.
- `far: number`: This value represents the distance of the `far` plane from the camera.

### `fog`

```json
fog: {
    enabled,
    density,
    color
}
```

- `enabled: boolean`: This boolean toggles fog in your levels.
- `density: number`: this value changes the density of the fog.
- `color: string`: This is the hex string of the fog color.

----

## Assets Definition

