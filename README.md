import pygame
import random

# Inicializar pygame
pygame.init()

# Colores
WHITE = (255, 255, 255)
BLACK = (0, 0, 0)
GREEN = (0, 255, 0)
RED = (255, 0, 0)

# Dimensiones de la pantalla
WIDTH = 600
HEIGHT = 400
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption('Juego del Gusano comiendo Peras')

# Parámetros del gusano
SNAKE_SIZE = 10
snake_pos = [100, 50]  # posición inicial
snake_body = [[100, 50], [90, 50], [80, 50]]  # cuerpo del gusano
snake_direction = 'RIGHT'
change_direction = snake_direction

# Parámetros de la pera
pear_pos = [random.randrange(1, (WIDTH // SNAKE_SIZE)) * SNAKE_SIZE,
            random.randrange(1, (HEIGHT // SNAKE_SIZE)) * SNAKE_SIZE]
pear_spawned = True

# Velocidad del juego
clock = pygame.time.Clock()
SPEED = 15

# Puntuación inicial
score = 0

# Función para mostrar el puntaje
font = pygame.font.SysFont('arial', 35)

def show_score():
    score_text = font.render(f'Score: {score}', True, BLACK)
    screen.blit(score_text, [0, 0])

# Ciclo principal del juego
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

        # Detectar el movimiento del gusano
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_UP and snake_direction != 'DOWN':
                change_direction = 'UP'
            if event.key == pygame.K_DOWN and snake_direction != 'UP':
                change_direction = 'DOWN'
            if event.key == pygame.K_LEFT and snake_direction != 'RIGHT':
                change_direction = 'LEFT'
            if event.key == pygame.K_RIGHT and snake_direction != 'LEFT
