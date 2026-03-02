🌍 Interactive 3D Globe (React + Three.js)

An advanced interactive 3D Earth visualization built with React and Three.js, inspired by NASA Earth simulations.

This project demonstrates real-time 3D rendering, geo-spatial calculations, raycasting interaction, physics-based rotation, and smooth camera transitions — all optimized for performance.

🚀 Live Demo

👉 Add your GitHub Pages / Vercel link here

✨ Features

🌍 Realistic 3D Globe

High-resolution Earth textures
Bump mapping + specular mapping
Ambient + directional lighting
Starfield background (8000 particles)


🖱 Advanced Interaction System

Mouse drag rotation
Momentum / inertia physics
Smooth deceleration
Auto-rotation fallback
Scroll-based zoom
Touch support (mobile)

🎯 Smart Raycasting

Hover detection (cursor changes)
Click detection on flag sprites
Country-based camera focus


🌎 Country Rendering

GeoJSON borders rendered dynamically
Polygon + MultiPolygon support
Country centroid calculation
Accurate lat/lon to 3D vector conversion


🏳 Dynamic Flag Sprites
Flags loaded via REST API
Sprite scaling based on country area
Depth-optimized rendering
Render order control


🎥 Cinematic Camera Transitions

Smooth LERP-based rotation
Intelligent shortest-path rotation logic
Zoom-in focus mode
Restore previous camera state on modal close


🪟 React UI Integration

Modal rendered via React state
Selected country data binding
Animated progress bars
Clean UI overlay


🧹 Memory Optimization

Texture disposal
Geometry cleanup
Event listener removal
Animation frame cancellation
GPU resource cleanup


🛠 Tech Stack

React (Hooks)
Three.js
WebGL
GeoJSON
REST APIs
ES6+


🧠 Architecture Breakdown

1️⃣ Scene Setup

PerspectiveCamera (FOV 60)
WebGLRenderer with SRGB color space
Pixel ratio optimization
Transparent canvas

2️⃣ 3D Math System

Lat/Lon → 3D Vector Conversion
Uses spherical coordinate transformation:
phi = (90 - lat) * (PI / 180)
theta = (lon + 180) * (PI / 180)
Converts geographic coordinates into Cartesian 3D positions.


3️⃣ Physics-Based Rotation System

State stored in stateRef:

velocity tracking
drag detection
autoRotate fallback
zoom state
transition state

Inertia formula:

velocity *= 0.92
Creates natural deceleration effect.

4️⃣ Smart Camera Rotation Logic

When a country is clicked:
Calculate target rotation from centroid
Normalize rotation to nearest angular lap
LERP camera + globe
Prevent long spin rotations
Smooth threshold snapping


5️⃣ Raycasting Engine

Uses THREE.Raycaster
Converts screen coords → normalized device coords
Intersects with flag sprites
Changes cursor dynamically


6️⃣ Data Sources

GeoJSON:
https://raw.githubusercontent.com/johan/world.geo.json/master/countries.geo.json

Country data:
https://restcountries.com/v3.1/all
