import pygame
import sys

# Game Variables
SCREEN_WIDTH, SCREEN_HEIGHT = 400, 600
PLAYER_POS = [50, 300]
GRAVITY = 0.5
FLAP_POWER = -10
player_velocity = 0

# Initialize Pygame
pygame.init()
screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))

# Load the bird image
bird = pygame.image.load('bird.png')  # Make sure you have an image named 'bird.png' in your directory

# Game Loop
while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_SPACE:
                player_velocity = FLAP_POWER

    # Apply gravity
    player_velocity += GRAVITY
    PLAYER_POS[1] += player_velocity

    # Draw everything
    screen.fill((255, 255, 255))  # White background
    screen.blit(bird, (PLAYER_POS[0], PLAYER_POS[1]))

    pygame.display.update()
