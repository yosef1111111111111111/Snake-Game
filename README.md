# Snake-Game


## Projektinformation

- **Navn:** [Yosef, Rashaath, Malthe]
- **Klasse:** [2.P]
- **Årgang:** [2.G]
- **Udviklingsmiljø:** [Visual Studio Code]
- **Programmeringssprog:** Python
- **Antal tegn:** [2920]

## Beskrivelse

Dette projekt er en Python-implementering af det klassiske Snake-spil ved hjælp af Pygame-biblioteket. Spillet giver spilleren kontrol over en slange, der skal indsamle mad og undgå kollisioner for at opnå en høj score.

## Funktionsbeskrivelse

### Skærmlayout

Spillet kører i et rektangulært vindue med dimensioner på 400x400 pixels. Slangen og maden vises som firkantede segmenter, og spillet viser en "Game Over" besked ved spilafslutning.

### Indtastningsmuligheder

Spilleren kan styre slangens bevægelse ved hjælp af følgende tastaturtaster:
- Piletast op: Bevæg slangen opad.
- Piletast ned: Bevæg slangen nedad.
- Piletast venstre: Bevæg slangen til venstre.
- Piletast højre: Bevæg slangen til højre.

### Funktionalitet

- Spillet begynder med en enkelt celle i midten af gitteret som slangens startposition.
- Maden placeres tilfældigt et sted inden for gitteret.
- Spilleren styrer slangens retning ved hjælp af tastaturinput.
- Slangen bevæger sig og øger sin længde, når den spiser maden.
- Spillet afsluttes, hvis slangen kolliderer med væggene eller sin egen krop.
- Spillet viser en "Game Over" besked og tillader spilleren at fortsætte eller afslutte spillet.

## Dokumentation

### Overordnet beskrivelse af programmet

Dette program er en Pygame-implementering af Snake-spillet. Det bruger Pygame-biblioteket til at håndtere spilgrafik og brugerinput. Koden omfatter en hovedspilsløkke, der styrer spillogikken og opdaterer skærmbilledet i realtid.

### Detaljeret dokumentation

- **Hovedspilsløkke:** Hovedspilsløkken styrer spillogikken og opdaterer spillet i realtid. Den inkluderer brugerinputhåndtering, bevægelse af slangen, kollisionstjek og opdatering af spilgrafik.

- **Brugerinput:** Spillerens tastaturinput overvåges ved hjælp af Pygame's event-håndtering. Piletasterne bruges til at ændre slangens retning.

- **Slangens bevægelse:** Slangen bevæger sig ved at tilføje et nyt hovedsegment til dens aktuelle position baseret på den aktuelle retning.

- **Kollisionstjek:** Der udføres forskellige kollisionstjek for at afgøre, om spillet skal afsluttes. Koden kontrollerer, om slangen har spist maden ved at sammenligne slangens hovedposition med madens position. Der tjekkes også for kollision med spillets grænser og om slangen kolliderer med sin egen krop.

## Udviklingsproces

I udviklingsprocessen begyndte jeg med at implementere de grundlæggende spilfunktioner, herunder slangens bevægelse, madgenerering og kollisionstjek. Jeg brugte Git til versionsstyring og lavede flere commits for at spore ændringer og gemme forskellige udviklingsstadier. Jeg skrev også pseudokode og flowcharts for at planlægge koden og dens struktur.

## Commit-Historie

- **Første commit:** Oprettelse af projektets grundstruktur og README-fil.
- **Anden commit:** Implementering af grundlæggende spilgrafik og slangens bevægelse.
- **Tredje commit:** Tilføjelse af madgenerering og kollisionstjek.
- **Fjerde commit:** Implementering af "Game Over" -besked og spilafslutning.
- **Femte commit:** Finpudsning af koden og dokumentationen.
- **Sidste commit:** Endelig gennemgang og klargøring til publicering.

Dette README-dokument giver en detaljeret forståelse af projektet og dets udviklingshistorie. For at få mere detaljeret information om koden og dens udviklingsproces, kan du besøge projektets GitHub-repositorium.




    import pygame
    import sys
    import random

    # Initialize Pygame
    pygame.init()

    # Constants
    WIDTH, HEIGHT = 400, 400
    GRID_SIZE = 20
    GRID_WIDTH = WIDTH // GRID_SIZE
    GRID_HEIGHT = HEIGHT // GRID_SIZE
    WHITE = (255, 255, 255)
    GREEN = (0, 255, 0)
    RED = (255, 0, 0)
    SNAKE_SPEED = 10

    # Initialize the screen
    screen = pygame.display.set_mode((WIDTH, HEIGHT))
    pygame.display.set_caption("Snake Game")

    # Initialize the snake
    snake = [(GRID_WIDTH // 2, GRID_HEIGHT // 2)]
    snake_direction = (0, 0)

    # Initialize the food
    food = (random.randint(0, GRID_WIDTH - 1), random.randint(0, GRID_HEIGHT - 1))

    # Game over flag
    game_over = False

    # Game loop
    clock = pygame.time.Clock()

    while not game_over:
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                pygame.quit()
                sys.exit()
            elif event.type == pygame.KEYDOWN:
                if event.key == pygame.K_UP and snake_direction != (0, 1):
                    snake_direction = (0, -1)
                elif event.key == pygame.K_DOWN and snake_direction != (0, -1):
                    snake_direction = (0, 1)
                elif event.key == pygame.K_LEFT and snake_direction != (1, 0):
                    snake_direction = (-1, 0)
                elif event.key == pygame.K_RIGHT and snake_direction != (-1, 0):
                    snake_direction = (1, 0)

        # Move the snake
        new_head = (snake[0][0] + snake_direction[0], snake[0][1] + snake_direction[1])
        snake.insert(0, new_head)

        # Check for collision with food
        if snake[0] == food:
            food = (random.randint(0, GRID_WIDTH - 1), random.randint(0, GRID_HEIGHT - 1))
        else:
            snake.pop()

        # Check for collision with walls
        if (
            snake[0][0] < 0
            or snake[0][0] >= GRID_WIDTH
            or snake[0][1] < 0
            or snake[0][1] >= GRID_HEIGHT
        ):
            game_over = True

        # Check for collision with itself
        if len(snake) > 1 and snake[0] in snake[1:]:
            game_over = True

        # Clear the screen
        screen.fill(WHITE)

        # Draw the snake
        for segment in snake:
            pygame.draw.rect(screen, GREEN, (segment[0] * GRID_SIZE, segment[1] * GRID_SIZE, GRID_SIZE, GRID_SIZE))

        # Draw the food
        pygame.draw.rect(screen, RED, (food[0] * GRID_SIZE, food[1] * GRID_SIZE, GRID_SIZE, GRID_SIZE))

        # Update the display
        pygame.display.flip()

        # Control game speed
        clock.tick(SNAKE_SPEED)

    # Game over message
    font = pygame.font.Font(None, 36)
    game_over_text = font.render("Game Over", True, (0, 0, 0))
    game_over_rect = game_over_text.get_rect(center=(WIDTH // 2, HEIGHT // 2))
    screen.blit(game_over_text, game_over_rect)
    pygame.display.flip()

    # Wait for a moment before closing the game
    pygame.time.wait(2000)

    pygame.quit()
    sys.exit()
