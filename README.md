# Voxel Studio Generator

## Description

Voxel Studio Generator is a self-contained, web-based 3D voxel art generator and editor built as a single HTML file (`Main.html`). It transforms 2D images or videos into interactive 3D voxel landscapes using WebGL and Three.js. The application features real-time audio reactivity, customizable lighting, and post-processing effects, emphasizing "Optimized Visibility" with a fixed lighting engine to create stylized, glowing voxel art. This tool is ideal for creative visualization, generative art, or interactive media projects.

## Features

- **3D Voxel Generation**: Converts 2D images or videos into 3D voxel landscapes with up to 40,000 voxels (200x200 grid) using efficient instanced meshes.
- **Real-Time Audio Reactivity**: Integrates with microphone input via Web Audio API to modulate voxel heights based on sound levels.
- **Customizable Visuals**: Adjustable parameters including exposure, glow/bloom, grid density, height, voxel size, color styles, and background.
- **Shape Options**: Toggle between Box, Sphere, and Cone voxel geometries.
- **Interactive Controls**: OrbitControls for camera manipulation with auto-rotation and damping.
- **Post-Processing Effects**: UnrealBloomPass for glow effects with customizable strength, threshold, and radius.
- **Media Support**: Upload images or videos, or use microphone for dynamic input.
- **Export Functionality**: Save high-resolution PNG screenshots of the 3D scene.
- **Optimized Rendering**: Uses custom shaders for height mapping, lighting, and color processing, with ACES Filmic Tone Mapping for accurate brightness.

## Installation and Usage

### Prerequisites
- A modern web browser with WebGL support (e.g., Chrome or Firefox).
- Microphone access for audio reactivity features (optional).

### Running the Application
1. Download or clone the project repository.
2. Open the `Main.html` file directly in your web browser. No server or build process is required, as it is fully self-contained.
3. The application will load with a default UV grid texture. You can start customizing immediately.

### Basic Usage
1. **Load Media**: Click the "Upload" button to select an image or video file, or click "Mic On" to enable microphone input (grant microphone permission when prompted).
2. **Adjust Parameters**: Use the sidebar controls to modify voxel shape, visual settings, color modes, and background.
3. **Interact**: Drag to orbit the camera around the scene. Auto-rotation provides passive viewing.
4. **Export**: Click "SAVE IMAGE" to download a PNG screenshot of the current view.

For best performance, use high-contrast images or videos. Audio reactivity amplifies voxel heights based on sound levels.

## Controls

The application features a glassmorphism-inspired sidebar (320px wide) with the following controls:

- **Media Input**:
  - Upload: File input for images/videos.
  - Mic On: Toggle microphone access for audio reactivity.

- **Shape Selection**: Radio buttons to choose between Box (default), Sphere, and Cone geometries.

- **Visual Parameters** (Sliders):
  - Exposure/Light: 0.1-3.0 (controls brightness).
  - Glow/Bloom: 0-2.0 (intensity of glow effect).
  - Grid Density: 32-200 (number of voxels).
  - Height 3D: 0-10 (vertical scaling of voxels).
  - Voxel Size: 0.1-1.5 (individual voxel scale).

- **Color Styles**: Dropdown with options:
  - Original Colors
  - Rainbow Heightmap
  - Cyberpunk Cyan/Pink
  - Golden Hour
  - Matrix Green

- **Background**: Color picker for scene background.

- **Export**: "SAVE IMAGE" button to capture and download a PNG.

All changes update the 3D scene in real-time.

## Dependencies

The project is self-contained and relies on external libraries loaded via CDN:

- **Tailwind CSS**: For UI styling.
- **Three.js r128**: Core 3D rendering engine.
- **Three.js Addons**:
  - OrbitControls
  - EffectComposer
  - RenderPass
  - ShaderPass
  - CopyShader
  - LuminosityHighPassShader
  - UnrealBloomPass

Browser APIs used:
- WebGL
- Web Audio API
- MediaDevices (for microphone)
- File API (for uploads)

No local dependencies or installation is required; the application runs offline once loaded.

## How It Works

1. **Initialization**: The scene loads a default texture, sets up the Three.js renderer with ACES Filmic Tone Mapping, camera with OrbitControls, and post-processing pipeline.
2. **Voxel Generation**: Input media is sampled at grid positions. Pixel brightness determines height, modulated by audio data and wave animations. Voxels are rendered as instanced meshes.
3. **Rendering Pipeline**:
   - Vertex Shader: Handles UV mapping, height displacement, and normals.
   - Fragment Shader: Applies color modes and directional lighting (ambient + diffuse).
   - Post-Processing: Adds bloom effects via EffectComposer.
4. **Interactivity**: Sliders and inputs update uniforms in real-time. File uploads replace textures dynamically.
5. **Export**: The scene is rendered with effects and saved as PNG.

This implementation demonstrates advanced WebGL techniques for efficient, real-time 3D generation.

## Contributing

Contributions are welcome! Please fork the repository and submit pull requests for enhancements or bug fixes. Ensure changes maintain the self-contained nature of the project.

## License

This project is open-source. Refer to the repository for licensing details.

## Screenshots

<img width="1319" height="1262" alt="image" src="https://github.com/user-attachments/assets/78ea103f-2e26-4562-b115-27db7007aa3f" />
<img width="1220" height="1267" alt="image" src="https://github.com/user-attachments/assets/112a34bb-ad10-496b-b033-32b198e253b8" />
<img width="1320" height="1280" alt="image" src="https://github.com/user-attachments/assets/f0afc20b-6d35-461f-a074-5baabf2a459f" />
<img width="1290" height="1260" alt="image" src="https://github.com/user-attachments/assets/3d9d9b2c-c805-44cb-8ae7-a09c16841e57" />


For visual examples, run the application and experiment with different inputs and settings.
