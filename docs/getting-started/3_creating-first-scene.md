# Creating your first scene

In the `index.js` file we imported a Scene that doesn't exist yet. Let's create one.

Create a new file wherever you want, but for the sake of this example, let's stick to the path we defined in `index.js` and create a `Scene.js` file in `PROJECT_ROOT/first/`.

Mage Engine is expecting each Scene to be a class extending the base class provided by the engine, called `BaseScene`.

We can define it like this:

```js
    import { BaseScene } from 'mage-engine';

    class FirstScene extends BaseScene {

        onCreate() {
            // do something cool here
        }
    }

    export default FirstScene;
```

Explanation:

- `onCreate`: this is a lifecycle method of your Scene. It will be called when the scene has been created, assets have been loaded and it's now ready to render elements on your screen.

> For a more in-depth documentation of the BaseScene class, please refer to this page: [BaseScene](/)

If you open your `index.html` now, our FirstScene will be bound to the root path, but it will render nothing. Our `onCreate` method is currently doing nothing, so let's add the 3D equivalent of a Hello World, a cube.

---

## Hello Cube

Adding a cube to the scene is incredibly straightforward. What you need to do is import it from `mage-engine` and create a new instance of it. Our newly created `FirstScene` will look like this:

```js
import { BaseScene, Cube } from 'mage-engine';

class FirstScene extends BaseScene {

    onCreate() {
        const size = 10;
        const color = 0x00ff00;
        const cube = new Cube(size, color);

        cube.setPosition({ x: 0, y: 0, z: 0});
    }
}

export default FirstScene;
```

Run the application now, and you will get 