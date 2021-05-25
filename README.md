# flappy_bird_game
Everyone is sad when they get out in the flappy bird game so I have made it so the bird will automatically go through the obstacles with just 40 lines python!!
I have done it by using Pycharm which is an python code editor.
In the first in the terminal I have written **pip install pygame** and then press enter.
Then in the first I have imported pygame.
Then I have written from random import randint
Then I have told pygame pygame.init().
Then I have created a variable called display and entered the value as pygame.display.set_mode((320, 568)).
Then I have created another varibale called text and entered the value as pygame.font.Font(None, 50).
Then I have created another variable called bg and entered the value as pygame.image.load('BG Image.png').
Then I have created another variable called bird and entered the value as pygame.image.load('Bird.png').
Then I have created another variable called pole_width and entered the value as 70.
Then I have created another variable called pole_gap and entered the value as 100.
Then I have created another variable called pole_x and entered the value as 320.
Then I have created another variable called top_pole_height and entered the value as randint(100, 400).
Then I have created another variable called pole_color and entered the value as (247, 53, 37)
Then I have created another variable called bird_x and entered the value as 20
Then I have created another variable called bird_y and entered the value as top_pole_height + 20
Then I have created another variable called score and entered the value as 0
Then I have created another variable called clock and entered the value as pygame.time.Clock().
Then I have created a while loop and entered the value as pygame.event.get()
    display.blit(bg, (0, 0))
    display.blit(bird, (bird_x, bird_y))
    pole_x = pole_x - 5
    if pole_x <= -pole_width:
        pole_x = 320
        top_pole_height = randint(50, 450)
        bird_y = top_pole_height + 20
        score = score + 20
    pygame.draw.rect(display, pole_color, (pole_x, 0, pole_width, top_pole_height))
    pygame.draw.rect(display, pole_color, (pole_x, top_pole_height + pole_gap, pole_width, 568))
    # collision
    if pole_x <= bird_x + 50 and bird_x <= pole_x + pole_width:
        if bird_y <= top_pole_height or bird_y >= top_pole_height +pole_gap:
            score = score - 5
            print('Collision!!', score)
    score_text = text.render(f'Score: {score}', True, (255, 255, 255))
    display.blit(score_text, (0, 0))
    pygame.display.update()
    clock.tick(60).
Now your automatic flappy bird game is ready now you never get sad!!
