# Flappy Bird Game
Everyone feels disappointed when they lose in Flappy Bird, so I decided to create a version where the bird automatically navigates through the obstacles! Best of all, I accomplished this in just 40 lines of Python code.
Tools Used:
I used PyCharm, a popular Python code editor, to write this project.
Setting Up the Environment
First, open the terminal and run the command:
pip install pygame
This installs the pygame library, which is essential for this game.
Code Explanation. Here’s a step-by-step breakdown of how I built the game:
Importing Libraries
I started by importing the required libraries:
import pygame
from random import randint
Initializing Pygame
I initialized pygame using:
pygame.init()
Creating Variables:
I created the following variables to set up the game:
display: The game window, created with
pygame.display.set_mode((320, 568))
text: The font for the score display, created with
pygame.font.Font(None, 50)
bg: The background image, loaded with
pygame.image.load('BG Image.png')
bird: The bird image, loaded with
pygame.image.load('Bird.png')
pole_width and pole_gap: Constants for the pole's dimensions, set as
70  # pole width  
100  # gap between poles
pole_x and top_pole_height: Variables for the pole's position and size, initialized as
320  
randint(100, 400)
pole_color: The color of the poles, defined as
(247, 53, 37)  # RGB values
bird_x and bird_y: The bird's position, set as
20  # x-coordinate  
top_pole_height + 20  # y-coordinate
score: The player's score, initialized at0
clock: A pygame clock object to control the frame rate:
pygame.time.Clock()
Game Loop
I created a loop to keep the game running:

python
Copy code
while True:
    # Event handling
    pygame.event.get()

    # Display the background and bird
    display.blit(bg, (0, 0))
    display.blit(bird, (bird_x, bird_y))

    # Move the pole
    pole_x -= 5
    if pole_x <= -pole_width:
        pole_x = 320
        top_pole_height = randint(50, 450)
        bird_y = top_pole_height + 20
        score += 20

    # Draw the poles
    pygame.draw.rect(display, pole_color, (pole_x, 0, pole_width, top_pole_height))
    pygame.draw.rect(display, pole_color, (pole_x, top_pole_height + pole_gap, pole_width, 568))

    # Collision detection
    if pole_x <= bird_x + 50 and bird_x <= pole_x + pole_width:
        if bird_y <= top_pole_height or bird_y >= top_pole_height + pole_gap:
            score -= 5
            print('Collision!', score)

    # Display the score
    score_text = text.render(f'Score: {score}', True, (255, 255, 255))
    display.blit(score_text, (0, 0))

    # Update the display and control the frame rate
    pygame.display.update()
    clock.tick(60)
Final Notes
With this simple script, you now have a version of Flappy Bird where the bird automatically navigates through obstacles. No more losing—and no more sadness! 🎉

