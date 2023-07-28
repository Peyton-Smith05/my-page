# Eternal Flame

Eternal Flame was a team project for my Computer Graphics class at SUTD. The goal of the project was to simulate particle motion, to model a flame, and render the particles with a build board implementation. This was built in C++ with OpenGL.

<!-- TODO : Format these two images -->
![Candle](../assets/candle.gif)

![Lighter](../assets/lighter.gif)

## Particle Motion

The general motion of the flame was controlled using newtons equations for acceleration and velocity. We then wanted to receive input from the user which allowed them to change wind direction and magnitude and the amount of oxygen. The Wind effect was achieved by by translating the particle system along an axis. The acis was user defined and the effect resulted in a shear of the particle system. The oxygen effect was meant to decrease or increase the size of the flame. This was achieved by scaling the velocity and time-to-live variables according the amount of oxygen concentration the user inputs.

## Billboard Rendering

Rendering particles can be expensive as the number of particles in the system grows. If a flame simulation, that requires many particles, were each rendered as 3D objects the rendering of each particle would quickly get very expensive. To solve this problem we implemented the Billboard method of rendering. Rather than representing a particle as a 3D object, it is represented as a 2D textured plane. This 2d plan is then oriented so that it always faces the camera. The particles now oriented towards the camera position will be ordered from front to back to decide what needs to be rendered. The speed up of this rendering process is significant.

We saw the benefits in our project through this implementation. We were able to render 500 particles to achieve a realistic motion and rendering of a candle flame and lighter flame.

## Shaders and Textures

We used 2 different shaders when rendering everything in our scene. One was used for the particles and the other for the 3D model of the candle or lighter. These shaders were implemented with Phone lighting. The were then compiled and rendered on the GPU through OpenGL's shared implementation.

## Results