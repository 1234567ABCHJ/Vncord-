import pygame
import sys

pygame.init()

# Set up the screen
screen_width = 800
screen_height = 600
screen = pygame.display.set_mode((screen_width, screen_height))
pygame.display.set_caption("Player Movement")

# Set up colors
WHITE = (255, 255, 255)
BLACK = (0, 0, 0)

# Set up player
player_width = 50
player_height = 50
player_x = (screen_width - player_width) // 2
player_y = (screen_height - player_height) // 2

# Set up movement speed
player_speed = 5

# Main game loop
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # Get keys pressed
    keys = pygame.key.get_pressed()

    # Update player position based on keys pressed
    if keys[pygame.K_LEFT]:
        player_x -= player_speed
    if keys[pygame.K_RIGHT]:
        player_x += player_speed
    if keys[pygame.K_UP]:
        player_y -= player_speed
    if keys[pygame.K_DOWN]:
        player_y += player_speed

    # Fill the screen with white
    screen.fill(WHITE)

    # Draw the player
    pygame.draw.rect(screen, BLACK, (player_x, player_y, player_width, player_height))

    # Update the display
    pygame.display.update()

    # Add a small delay
    pygame.time.delay(30)

pygame.quit()
sys.exit()
