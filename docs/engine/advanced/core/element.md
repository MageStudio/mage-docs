# Element

Every physical object you add to your level is an instance of the Element class. This class extends the Entity class, which is described in its own page [here](/engine/advanced/core/entity.md).

By "physical object", we mean Models and each of the Base Elements. Each base element is described in its page.

- [Cube](/engine/advanced/core/base/cube.md)
- [Box](/engine/advanced/core/base/box.md)
- [Sphere](/engine/advanced/core/base/sphere.md)
- [Cylinder](/engine/advanced/core/base/cylinder.md)
- [Plane](/engine/advanced/core/base/plane.md)
- [Line](/engine/advanced/core/base/line.md)
- [CurvedLine](/engine/advanced/core/base/curvedline.md)
- [Grid](/engine/advanced/core/base/grid.md)
- [Sprite](/engine/advanced/core/base/sprite.md)
- [AnimatedSprite](/engine/advanced/core/base/animatedsprite.md)

?> For Models documentation, please refer to this page [here](/engine/advanced/assets/models.md).

---

## Methods

### `constructor(geometry: ThreeGeometry, material: ThreeMaterial, options: Object)`

Something here

### `hasMesh(): boolean`

Checks if this element has an attached mesh. Returns `true` if the mesh is present, `false` otherwise.

### `getMesh(): ThreeMesh`

This method will return the ThreeMesh attached to this element if present.

### `getMeshByName(name: string): ThreeMesh`

This method will search for the ThreeMesh with the required name inside this element. If found, it will be returned. If not found, `undefined` will be returned.

### `setMesh({ mesh?: ThreeMesh, geometry?: ThreeGeometry, material?: ThreeMaterial })`

This method sets the ThreeMesh attached to this element. You have three options:

- `mesh`: an already existing ThreeMesh, will be attached to the element.
- `geometry` and `material`: these need to be instances of a ThreeGeometry and a ThreeMaterial. A ThreeMesh will be created and attached to the element.

> This method is used internally inside the constructor.

### `setName(name: string, options?: object)`

This method sets the name of this element.

- `options` is optional, and only supports one value:
  - `replace` (default: `false`): if this value is set to `true`, the current ThreeMesh will be disposed and replaced.

### `add(element: Element)`

This will add the received `element` to this element.

### `remove(element: Element)`

This will remove a previously added `element` from this element.

### `setColor(color: string|number)`

- `color` can be a string representation of a color (e.g. 'black', '#fefefe'), or its hex value (e.g. 0x000000 for black).

### `setTextureMap(textureId: string, options: Object)`

### `setMaterialFromName(materialName: MaterialType, options; Object)`

### `setOpacity(value: number)`

- `value` (default: `1`): This value sets the opacity of this element. Value can only assume values between `0` and `1`.

### `setWireframe(flag: boolean)`

- `flag`: when it's set to true, this element will be rendered as wireframe.

### `setWireframeLineWidth(width: number)`

- `width` will set the width of the wireframe lines. In order for this to work, you need to call `element.setWireframe(true)` first.

### `toJSON()`

This will return a JSON representation of this element.

---

## Animations

### `playAnimation(id: string, options: Object)`

If this element has animations and the require `id` is a valid animation identifier, that animation will be played.

- `options: { duration: 0.2 }`: This option is being used when transitioning from one animation to another.

### `getAvailableAnimations(): array<ThreeAnimation>`

If this element has animations, this methods will return a list of them.

---

## Physics

### `enablePhysics(options: object)`

If physics are enabled, this will add this element to the Physics Engine.

?> For a better description of the `options` object, have a look at the Physics page [here](/engine/advanced/physics.md).

### `applyForce(force: Object)`

### `setColliders(vectors: array, options: array)`

### `checkCollisions()`

### `isCollidingOnDirection(direction: Object)`
