import pygame
import random

# Initialiser Pygame
pygame.init()

# Indstillinger for spillet
win_width, win_height = 800, 600
game_window = pygame.display.set_mode((win_width, win_height))
pygame.display.set_caption("Salami Snake Game")

# Definér farver
white = (255, 255, 255)
red = (255, 0, 0)

# Slangeens startposition og længde
snake_x, snake_y = win_width // 2, win_height // 2
snake_length = 1
snake_speed = 15

# Salamiens position
salami_x, salami_y = random.randint(0, win_width-20), random.randint(0, win_height-20)

# Spilsløjpe
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # Bevægelse af slangen
    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT]:
        snake_x -= 10
    if keys[pygame.K_RIGHT]:
        snake_x += 10
    if keys[pygame.K_UP]:
        snake_y -= 10
    if keys[pygame.K_DOWN]:
        snake_y += 10

    # Tegn slange og salami
    game_window.fill(white)
    pygame.draw.rect(game_window, red, [salami_x, salami_y, 20, 20])
    pygame.draw.rect(game_window, white, [snake_x, snake_y, 20, 20])

    pygame.display.update()

