# Pygame Screen Recorder

Simple project which implements screen recording functionality for pygame

While developing pygame projects/games, there is commonly an urge to record screen-casts of the same. 
This module provides a simple way to do so.

Simply import the `ScreenRecorder` class from the module, 
pass in the required parameters (display height, width and frame per second) while creating an object.
Call the `capture_frame` method after updating the display. 
Call `end_recording` method while exiting the game loop.

To use the module, clone this repository then install:
```bash
git clone https://github.com/jcranney/pygame_recorder.git
cd pygame_recorder
pip install .
```
or directly (without cloning):
```bash
pip install git+https://github.com/jcranney/pygame_recorder.git
```


Sample Usage:
```python
import pygame
from pygame_recorder import ScreenRecorder

WIDTH, HEIGHT = 600, 400
FPS = 60

win = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption('Screen Recorder Test')

clock = pygame.time.Clock()
run = True

# Create a screen recorder object
recorder = ScreenRecorder(WIDTH, HEIGHT, FPS)

while run:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            run = False
        # Handle other events
        pass
    
    # Handle drawing .. 
    win.fill((255, 255, 255))
    
    pygame.display.update()
    
    # Capture the frame
    recorder.capture_frame(win)
    
    clock.tick(FPS)

# Stop the screen recording
recorder.end_recording()
 
    
```

