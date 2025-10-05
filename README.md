# Asteroid Dodge

A real-time, interactive 3D game using webcam-based head tracking to control a UFO navigating through a parallax-layered space scene. Dodge asteroids to survive and collect aliens for bonus points, with immersive audio effects and a dynamic 3D environment.

## ✨ Features

- **Real-Time Head-Tracked Parallax**: Background layers shift based on your head's horizontal (X) and vertical (Y) movements, creating a vivid 3D depth effect.
- **Immersive Zoom (Z-Axis)**: Move your face closer to or farther from the webcam to zoom the scene in and out, enhancing immersion.
- **Gameplay Mechanics**:
  - Control a UFO to avoid asteroids (lose 1 health on hit) and collect aliens (gain 100 points on hit, 5 points if passed).
  - Score increases by 0.1 per frame, with additional points for passing asteroids (10 points).
  - Health starts at 3; game ends when health reaches 0.
- **Audio Effects**:
  - Looping background music (`background_music.mp3`) plays during gameplay.
  - Sound effects for game start (`game_start.mp3`), game over (`game_over.mp3`), asteroid collisions (`asteroid_hit.mp3`), and alien collisions (`alien_hit.mp3`).
- **Visual Feedback**:
  - HUD displays score, health, and time.
  - Screen shake and UFO color flash (red for asteroid hits, green for alien hits) on collisions.
  - Particle explosion effect on asteroid hits.
- **Fallback Controls**: Use arrow keys to control the UFO if face detection fails.
- **Low-Light Optimized**: Utilizes the SSD Mobilenet V1 model for robust face detection in various lighting conditions.
- **Customizable Assets**: Easily swap PNG images for background, layers, UFO, asteroids, and aliens.
- **Smooth Tracking**: Smoothing factors ensure fluid movement despite camera jitters.

## 🛠️ Setup and Installation

This game requires a local web server (e.g., `http-server` for Node.js or `python -m http.server`) due to browser CORS restrictions on webcam access and file loading.

### Python Server
Run in bash
python -m http.server 8080

Access the game at http://localhost:8080 in a browser 

