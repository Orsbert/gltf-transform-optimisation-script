# gltf-transform-optimisation-script
Script for optimising models I have downloaded. I just copy and paste this into https://gltf.report

Learn more here https://gltf-transform.donmccurdy.com/

```js
import { MeshoptEncoder, MeshoptSimplifier } from 'meshoptimizer';
import { prune, dedup, resample, textureResize, reorder, instance, simplify, weld, join } from '@gltf-transform/functions';

await document.transform(

	// Remove duplicate vertex or texture data, if any.
	dedup(),

	// Joins compatible Primitives and reduces draw calls
	join({ keepNamed: false }),

	// producing meshes with fewer triangles and vertices.
	weld({ tolerance: 0.0001 }),
	simplify({ simplifier: MeshoptSimplifier, ratio: 0.5, error: 0.1 }),

	// Optimizes Mesh Primitives to be optimal for transmission size (recommended for Web)
	reorder({encoder: MeshoptEncoder}),

	// Losslessly resample animation frames.
	resample(),

	// Remove unused nodes, textures, or other data.
	prune(),

	// Resize all textures to ≤1K.
	textureResize({size: [512, 512]}),

);

```
