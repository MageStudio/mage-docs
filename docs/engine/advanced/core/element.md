# Element

Every physical object you add to your level is an instance of the Element class. This class extends the Entity class, which is described in its own page [here](/engine/advanced/core/entity.md).

This includes Models and each of the Core Elements.

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

### `playAnimation(id: string, options: Object)`

### `getAvailableAnimations()`

### `enablePhysics(options: object)`

### `applForce(force: Object)`

### `add(element: Element)`

### `remove(element: Element)`

### `setColliders(vectors: array, options: array)`

### `checkCollisions()`

### `isCollidingOnDirection(direction: Object)`

### `setColor(color)`

### `setTextureMap(textureId: string, options: Object)`

### `setMaterialFromName(materialName: MaterialType, options; Object)`

### `setOpacity(value: number)`

### `setWireframe(flag: boolean)`

### `setWireframeLineWidth(width: number)`

### `toJSON()`


