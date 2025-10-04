3D Head-Tracked Parallax Scene
This project demonstrates a real-time, interactive 3D parallax effect using a webcam for head tracking. By monitoring the user's head position and distance, the application adjusts the view of a layered 3D scene, creating an immersive "window" effect.

✨ Features
Real-Time Parallax: Layers shift relative to each other based on the user's horizontal (X) and vertical (Y) head movements, simulating depth.

Immersive Zoom (Z-Axis): Moving your face closer to or farther from the camera dynamically zooms the entire 3D scene in and out, enhancing the sense of immersion.

Low-Light Optimized: Uses the robust SSD Mobilenet V1 model for improved face detection performance, especially in sub-optimal lighting conditions.

Static Background: Includes a non-moving background plane that remains fixed, emphasizing the parallax movement of the foreground layers.

Customizable Layers: Easily swap out PNG images to create your own multi-layered 3D scenes.

Smooth Tracking: Utilizes smoothing factors to ensure natural, fluid movement despite minor camera jitters.

🛠️ Setup and Installation
This application requires running on a local web server (e.g., using Python's http.server or Node's serve) because browsers enforce security restrictions (CORS) on file access, especially for webcam streams and face detection models.

1. File Structure (Critical Step!)
The face-api.js library requires external model files to run. You must create a models directory and place the necessary files inside it.

Your directory structure must look like this:

/your-project-folder
|-- index.html (or your HTML file name)
|-- BG.png
|-- layer1.png
|-- layer2.png
|-- ...
|-- /models <--- REQUIRED FOLDER
    |-- ssd_mobilenetv1_model-weights_manifest.json
    |-- ssd_mobilenetv1_model.weights
    |-- face_landmark_68_model-weights_manifest.json
    |-- ... (other required face-api.js model files)

Where to get the models: The model files for ssd_mobilenetv1 and faceLandmark68Net must be downloaded from the official face-api.js repository or model asset site.

2. Dependencies
The code relies on the following external libraries, which are loaded via CDN:

Three.js (r128): The 3D graphics library.

face-api.js (0.22.2): The library used for real-time face and landmark detection.

⚙️ Configuration
You can easily adjust the tracking sensitivity and scene depth by modifying the constants at the top of the <script> block:

Constant

Description

Adjustment

XY_SMOOTHING_FACTOR

Controls the smoothness of the horizontal and vertical parallax.

Higher value (e.g., 0.3) = Snappier, less smooth movement.

Z_SMOOTHING_FACTOR

Controls the responsiveness of the zoom effect (Z-axis).

Higher value (e.g., 0.4) = Faster, more dramatic zoom.

XY_PARALLAX_SENSITIVITY

Multiplier for how far layers move relative to head position.

Higher value = More extreme parallax effect.

CUBE_SIZE

Defines the overall size of the 3D scene container (affects layer positioning).



Z_MIN, Z_MAX

The minimum and maximum camera Z position allowed. This defines the range of the zoom effect.

Wider range = Deeper, more noticeable zoom.

REFERENCE_FACE_WIDTH

The reference pixel size of a face at the "initial" Z-depth. Calibrate this if your webcam view is unusually close or far.



🖼️ Image Layer Setup
Layers are loaded from the LAYER_IMAGE_PATHS array:

const LAYER_IMAGE_PATHS = [
    'BG.png',       // 1. Used as the static, non-moving background plane.
    'layer1.png',   // 2. Furthest parallax layer
    'layer2.png',   // 3. Middle parallax layer
    'layer3.png',   // 4. Closer parallax layer
    'layer4.png',   // 5. Even closer
    'layer5.png'    // 6. Closest parallax layer
];

Ensure all paths listed in this array point to valid PNG image files located in the same directory as the HTML file. The layers are ordered from back to front, with the first item (BG.png) reserved for the static backdrop.
