# GlTF Transform Optimization Script

Welcome to the glTF Transform Optimization Script! This script is designed to optimize models downloaded in glTF format. Simply copy and paste the script into [glTF Report](https://gltf.report) to optimize your models.

## About:

This script utilizes the capabilities of glTF Transform, a tool for optimizing, converting, and viewing glTF assets. glTF Transform provides a wide range of features for optimizing models, including compression, mesh simplification, texture optimization, and more.

Learn more about glTF Transform [here](https://gltf-transform.donmccurdy.com/).

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

## Usage:

To use this script, follow these steps:

1. **Download Models**: 
   Download the models you wish to optimize in glTF format.

2. **Copy Script**: 
   Copy the optimization script provided here.

3. **Paste into glTF Report**: 
   Navigate to [glTF Report](https://gltf.report) and paste the script into the appropriate field.

4. **Run Optimization**: 
   Run the optimization process to apply various optimizations to your glTF models.

5. **Download Optimized Models**: 
   Once the optimization process is complete, download the optimized models for use in your projects.

## Additional Notes:

- **Optimization Parameters**: You can adjust the optimization parameters in the script according to your requirements. Refer to the glTF Transform documentation for details on available options and their effects.

- **Customization**: Feel free to customize and extend this script to suit your specific optimization needs. You can add additional optimization steps or modify existing ones to achieve desired results.

- **Feedback and Contributions**: If you encounter any issues or have suggestions for improvements, please don't hesitate to open an issue or submit a pull request on the [GitHub repository](https://github.com/Orsbert/gltf-transform-optimisation-script). Your feedback and contributions are highly appreciated.

Happy optimizing your glTF models with glTF Transform! If you have any questions or need assistance, feel free to reach out.


