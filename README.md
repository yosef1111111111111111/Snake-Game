# Snake-Game

Denne kode er et Python-program, der implementerer et simpelt Snake-spil ved hjælp af Pygame-biblioteket. Spillet består af en slange, som spilleren styrer, og målet er at spise den røde mad, samtidig med at man undgår kollisioner med slangen's egen krop og spillets grænser. Her er en gennemgang af koden:

Import af biblioteker:

Programmet starter med at importere de nødvendige biblioteker: pygame, sys, og random. pygame bruges til at oprette spillet, håndtere grafik og brugerinput.
Initialisering af Pygame:

Funktionen pygame.init() kaldes for at initialisere Pygame-biblioteket.
Konstanter:

Adskillige konstanter er defineret for at konfigurere spillets parametre:
WIDTH og HEIGHT repræsenterer dimensionerne af spilvinduet (400x400 pixels).
GRID_SIZE er størrelsen af hver gittercelle, hvor slangen og maden placeres.
GRID_WIDTH og GRID_HEIGHT beregnes baseret på vinduesdimensionerne og gitterstørrelsen.
Farver defineres ved hjælp af RGB-værdier: WHITE (baggrund), GREEN (slangen) og RED (mad).
SNAKE_SPEED sætter hastigheden for slangens bevægelse.
Initialisering af skærmen:

Spilvinduet oprettes ved hjælp af pygame.display.set_mode() med den angivne bredde og højde, og titlen sættes til "Snake Game."
Initialisering af slangen og maden:

Slangen starter i midten af gitteret, og dens begyndelsesretning er indstillet til stillestående.
Maden placeres på et tilfældigt sted inden for gitteret.
Spilsløjfe:

Hovedspilsløkken kører, indtil flaget game_over er indstillet til True.
Inden for løkken kontrolleres brugerinput for at styre slangens retning ved hjælp af piletasterne.
Slangens bevægelse simuleres ved at opdatere dens position.
Kollision detekteres for at kontrollere, om slangen har spist maden eller om den er stødt mod væggene eller sig selv.
Spilskærmen ryddes, og slangen og maden tegnes på skærmen.
Skærmen opdateres ved hjælp af pygame.display.flip().
Spillets hastighed kontrolleres med clock.tick(SNAKE_SPEED).
Spilslut:

Hvis spillet er slut, vises en "Game Over" besked i midten af skærmen.
Vent og afslut:

Programmet venter i 2 sekunder efter spillet er slut.
Efter ventetiden lukkes Pygame, og programmet afsluttes.
Sammenfattende opretter denne kode et simpelt Snake-spil ved hjælp af Pygame, hvor spilleren styrer en slange for at spise mad og forsøger at undgå kollisioner med væggene eller slangens egen krop. Spilsløjfen håndterer brugerinput, opdaterer spiltilstanden og tegner spillet på skærmen.




Denne Python-kode implementerer et klassisk Snake-spil ved hjælp af Pygame, som er et populært bibliotek til at oprette spil i Python. Spillet giver dig mulighed for at styre en slange, der bevæger sig rundt på et gitter og forsøger at indsamle mad, samtidig med at den undgår at kollidere med væggene og sin egen krop.

Initialisering og Konstanter:
Koden begynder med at initialisere Pygame-biblioteket og definere en række konstanter. Disse konstanter inkluderer spilvinduets dimensioner (400x400 pixels), størrelsen af hver celle i gitteret, farvekoderne for baggrund, slange og mad, samt slangens bevægelseshastighed.

Initialisering af Spilvinduet:
Spilvinduet oprettes ved hjælp af pygame.display.set_mode()-funktionen med de tidligere definerede dimensioner, og vinduets titel angives som "Snake Game."

Initialisering af Slang og Mad:
Spillet starter med en enkelt celle i midten af gitteret som slangens startposition, og slangens bevægelsesretning er indstillet til at være stillestående. Maden placeres tilfældigt et sted inden for gitteret.

Hovedspilsløjfe:
Spillet kører i en hovedsløjfe, der gentages, indtil game_over-flaget er sandt. Inden for denne sløjfe behandles brugerinput, så spilleren kan styre slangens retning ved hjælp af piletasterne.

Slangens bevægelse simuleres ved at opdatere dens position. Hvis slangen spiser maden, genereres ny mad på en tilfældig placering, og slangens længde øges. Hvis slangen kolliderer med væggene eller sin egen krop, afsluttes spillet ved at indstille game_over til sandt.

Grafik og Opdatering:
Spilvinduet ryddes ved at udfylde det med den hvide baggrundsfarve. Derefter tegnes slangens segmenter og maden på skærmen. Spilvinduet opdateres ved hjælp af pygame.display.flip() for at vise de seneste ændringer.

Spilslut:
Hvis spillet slutter, vises en "Game Over" besked midt på skærmen ved hjælp af Pygame's tekstfunktioner.

Afslutning:
Efter en kort ventetid på 2 sekunder lukkes Pygame, og programmet afsluttes.

Dette Snake-spil er et sjovt eksempel på, hvordan man kan oprette et simpelt spil ved hjælp af Pygame i Python. Spilleren kan nyde at styre slangens bevægelse, samle mad og forsøge at opnå den højeste score uden at kollidere med forhindringerne.


Hovedspilsløjfen:
Hovedspilsløjfen er hjertet i spillet. Den køres kontinuerligt og styrer spillets logik. Inden for denne sløjfe sker følgende:

Brugerinputhåndtering: Koden overvåger brugerens input ved hjælp af Pygame's pygame.event.get(). Hvis spilleren trykker på en piletast, ændres slangens retning i overensstemmelse hermed. Dette giver spilleren kontrol over, hvilken retning slangen bevæger sig i.

Slangens bevægelse: Slangens position opdateres ved at tilføje et nyt hovedsegment til dens aktuelle position baseret på den aktuelle retning. Dette simulerer slangens bevægelse.

Kollisionstjek: Der udføres forskellige kollisionstjek for at afgøre, om spillet skal afsluttes. Koden kontrollerer, om slangen har spist maden ved at sammenligne slangens hovedposition med madens position. Hvis dette er tilfældet, genereres ny mad, og slangens længde øges. Koden tjekker også for kollision med spillets grænser og om slangen kolliderer med sin egen krop. Hvis nogen af disse betingelser er opfyldt, indstilles game_over-flaget til sandt, og spillet afsluttes.

Opdatering af spilgrafik: Efter at have opdateret spiltilstanden ryddes skærmen og tegnes på ny. Slangens segmenter og maden tegnes på skærmen ved hjælp af pygame.draw.rect(). Dette giver spilleren visuel feedback om spiltilstanden.

Spilhastighedskontrol: clock.tick(SNAKE_SPEED) bruges til at regulere spillets hastighed. Dette sikrer, at spillet ikke kører for hurtigt eller for langsomt, uanset hvor kraftfuld computeren er.

Spilafslutning:
Når spillet er slut, vises en "Game Over"-besked midt på skærmen ved hjælp af Pygame's tekstfunktioner. Spilleren får derefter en kort pause på 2 sekunder til at se beskeden, før Pygame lukkes, og programmet afsluttes.

Dette Snake-spil er et godt eksempel på et simpelt spilprojekt, der bruger Pygame til at håndtere grafik og spillogik. Det er en sjov måde at lære om spiludvikling og programmering i Python på. Spillet kan også udvides med ekstra funktioner som high score-tracker, lydeffekter og mere avanceret spillogik for at gøre det endnu mere underholdende.
