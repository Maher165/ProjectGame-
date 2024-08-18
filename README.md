Game Overview:

Objective: Navigate through a maze to reach the exit while avoiding enemies, collecting keys, and interacting with various objects. Gameplay Elements: Player Character: Controlled by the player, this character must traverse the maze to find the exit. Maze: A grid-based structure with walls, entry and exit points, and various objects. Enemies: Characters that move within the maze and can harm the player upon contact.

Collectibles: Key: A required item to unlock the exit. Hearts: Increase the player's lives. Shields: Grant temporary invincibility to the player. Speed Boosts: Increase the player's movement speed. Traps: Hazards that can harm the player.

HUD (Heads-Up Display): Displays information such as lives, time taken, and collected items.

Game Controls:

During gameplay: Arrow Keys or WASD: Move the player character. ESC Key: Toggle game pause E Key : Pause R Key : Resume X Key: Decrease minimap size. C Key: Increase minimap size.

Game Flow:

Start Screen:

The game starts at the Main Menu Players can navigate to different screens, such as starting a new game or accessing the main menu. Main Menu:

Options to start a new game, select a level, adjust settings, or exit the game.

Level Selection:

Players may choose a specific maze level to play. Gameplay:

The player character starts at the entry point of the maze. Navigate through the maze using arrow keys or WASD. Collect keys, hearts, shields, and speed boosts. Avoid enemies and traps. Reach the exit point after collecting the key. Pause Menu:

Pressing ESC or E pauses the game. Access the pause menu to resume, restart, load a new map, return to the main menu, or exit the game. Game Over:

If the player loses all lives, the game over screen is set. If the player wins then the win screen will be set.

Animate Class :

The Animate class provides functionality for animating textures over time in Java, specifically designed for use with the LibGDX game development framework. This class includes methods to retrieve the current texture based on an internal timer and to update the timer for smooth animation.

Usage To use the Animate class, follow these steps:

Instantiate an Animate object:

// Example instantiation with an animation frame period of 0.1 seconds Animate animator = new Animate(0.1f); Define your animation textures:

// Example: creating an array of TextureRegions TextureRegion[] animationTextures = { /* add your TextureRegions here */ }; OR

// Example: creating an ArrayList of TextureRegions ArrayList animationTexturesList = new ArrayList<>(); // add your TextureRegions to animationTexturesList OR

// Example: creating an array of Textures Texture[] animationTextures = { /* add your Textures here */ }; Retrieve the current texture for rendering:

// Example: getting the current texture based on the internal timer TextureRegion currentTexture = animator.currentTexture(animationTextures); Update the internal timer for smooth animation:

// Example: updating the timer with the delta time per frame float deltaTime = /* get your delta time per frame */; animator.updateTimer(deltaTime); Render the current texture in your game/application.

Methods public TextureRegion currentTexture(TextureRegion[] textures) Returns the current TextureRegion of the animation based on the internal timer.

public TextureRegion currentTexture(ArrayList textures) Returns the current TextureRegion of the animation based on the internal timer (for use with ArrayList).

public Texture currentTexture(Texture[] textures) Returns the current Texture of the animation based on the internal timer.

public void updateTimer(float delta) Increments the internal timer by the specified delta time. This method controls the animation of the object.

Attributes public float animateTime The current animation time, indicating the progress of the animation.

public final float ANIMATION_FRAME_PERIOD The period for each animation frame, specified during object instantiation.

Example

// Example usage of the Animate class public class ExampleUsage { public static void main(String[] args) { // Instantiate an Animate object with an animation frame period of 0.1 seconds Animate animator = new Animate(0.1f);

    // Example: creating an array of TextureRegions
    TextureRegion[] animationTextures = { /* add your TextureRegions here */ };

    // Example: updating the timer with the delta time per frame
    float deltaTime = /* get your delta time per frame */;
    animator.updateTimer(deltaTime);

    // Example: getting the current texture based on the internal timer
    TextureRegion currentTexture = animator.currentTexture(animationTextures);

    // Render the currentTexture in your game/application
    // ...
}
}

Dynamic_Characters Class :

The Dynamic_Characters class is an abstract class representing dynamic characters in the game. It provides common attributes and methods for dynamic characters, such as position, texture region, and speed.

Usage This class serves as a base class for other dynamic characters in the game. To use the Dynamic_Characters class, follow these steps:

Create a subclass:

// Example: Create a subclass for a specific dynamic character public class Player extends Dynamic_Characters { // Additional attributes and methods specific to the player character } Override methods if necessary:

// Example: Override the isMoveInvalid method in the Player class public class Player extends Dynamic_Characters { // ... other attributes and methods

@Override
public boolean isMoveInvalid(float posX, float posY, Maze maze) {
    // Custom implementation for checking invalid moves specific to the player
    // ...
    return false;
}
} Instantiate and use the subclass:

// Example: Instantiate and use the Player class Player player = new Player(); player.setPosX(10); player.setPosY(20); player.setSpeed(5.0f); Attributes private final TextureRegion textureRegion The texture region associated with the dynamic character.

private float posX, posY The X and Y coordinates of the dynamic character.

private float speed The speed of the dynamic character.

Methods public TextureRegion getTextureRegion() Gets the texture region associated with the dynamic character.

public float getPosX(), public void setPosX(float posX) Gets and sets the X-coordinate position of the dynamic character.

public float getPosY(), public void setPosY(float posY) Gets and sets the Y-coordinate position of the dynamic character.

public float getSpeed(), public void setSpeed(float speed) Gets and sets the speed of the dynamic character.

public boolean isMoveInvalid(float posX, float posY, Maze maze) Checks if a move to the specified position is invalid based on the maze configuration. This method is meant to be overridden by subclasses for specific implementations.

Example

// Example usage of the Dynamic_Characters class public class ExampleUsage { public static void main(String[] args) { // Instantiate a subclass of Dynamic_Characters (e.g., Player) Player player = new Player();

    // Set attributes for the player
    player.setPosX(10);
    player.setPosY(20);
    player.setSpeed(5.0f);

    // Access and use methods from the Dynamic_Characters base class
    float posX = player.getPosX();
    float posY = player.getPosY();
    float speed = player.getSpeed();
    TextureRegion textureRegion = player.getTextureRegion();

    // Override methods if necessary in the Player class
    // ...
}
}

Character Class :

The Character class represents the player character in the game and extends the Dynamic_Characters class. It provides methods for character movement, animation, collision detection, and other player-related functionalities.

Usage To use the Character class, follow these steps:

Instantiate a Character object:

// Example instantiation with initial position (0, 0) Character player = new Character(0, 0); Access and update character attributes:

// Example: getting and setting player position float playerX = player.getPosX(); float playerY = player.getPosY(); player.setPosX(10); // Set player X-coordinate to 10

// Example: getting and setting player lives int lives = player.getLives(); player.setLives(3); // Set player lives to 3

// Example: checking if the player is shielded boolean isShielded = player.isShielded(); player.setShielded(true); // Activate player shield Move the player based on user input:

// Example: moving the player based on input and updating animation player.movePlayerOnInput(maze, delta); Check for collisions and perform related actions:

// Example: checking for collisions with an enemy Enemy enemy = /* get your enemy object */; if (player.collidesWithEnemy(enemy)) { // Handle collision with the enemy } Update animation and other time-dependent features:

// Example: updating animation timer based on elapsed time float deltaTime = /* get your delta time */; Character.animateTimer(deltaTime); Attributes private final TextureRegion textureDown, textureRight, textureUp, textureLeft TextureRegions representing the character's appearance in different directions.

private final TextureRegion[] textureDownAnimation, textureRightAnimation, textureUpAnimation, textureLeftAnimation Arrays of TextureRegions for animated character movements in different directions.

private float posX, posY The current X and Y coordinates of the player.

private float previousPosX, previousPosY The previous X and Y coordinates of the player, used for collision detection and invalid moves.

private TextureRegion currentDirection The current direction of the player character.

private Array turnFrames An array of TextureRegions containing frames for character animation.

public static final float ASPECT_RATIO A constant representing the aspect ratio of the character.

private int lives The number of lives remaining for the player.

private boolean isShielded A flag indicating whether the player is currently shielded.

private Sound characterGrunts, characterDeath, characterKey Sound objects for player grunts, death, and key-picking events.

private static float animateTime A static attribute representing the current animation time for the player.

private static final float ANIMATION_FRAME_PERIOD A constant defining the period for each animation frame.

private Direction lastPressedButton An enumeration representing the last pressed directional button.

private float speed The speed of the player character.

Methods public void movePlayerOnInput(Maze maze, float delta) Moves the player based on user input and updates the animation.

public boolean isMoveInvalid(float posX, float posY, Maze maze) Checks if a move to the specified position is invalid based on the maze configuration.

public boolean collidesWithEnemy(Enemy enemy) Checks if the character collides with an enemy based on bounding rectangles.

public void animateTimer(float delta) Updates the animation timer based on elapsed time.

public boolean isAt(GameObject gameObject, float CELLSIZE) Checks if the player is at the location of the specified GameObject.

Example

// Example usage of the Character class public class ExampleUsage { public static void main(String[] args) { // Instantiate a Character object with initial position (0, 0) Character player = new Character(0, 0);

    // Example: getting and setting player position
    float playerX = player.getPosX();
    float playerY = player.getPosY();
    player.setPosX(10); // Set player X-coordinate to 10

    // Example: checking for collisions with an enemy
    Enemy enemy = /* get your enemy object */;
    if (player.collidesWithEnemy(enemy)) {
        // Handle collision with the enemy
    }

    // Example: moving the player based on input and updating animation
    float delta = /* get your delta time */;
    player.movePlayerOnInput(maze, delta);

    // Example: updating animation timer based on elapsed time
    Character.animateTimer(delta);
}
}

Enemy Class :

The Enemy class represents an enemy character in the game. It extends the Dynamic_Characters abstract class and includes methods for enemy movement, collision detection, and animation.

Attributes private TextureRegion directionTexture The texture region representing the current direction of the enemy.

private final TextureRegion[] textureDownAnimation, textureRightAnimation, textureUpAnimation, textureLeftAnimation Animation frames for different movement directions.

private Array turnFrames Array of turn frames for animation.

private float enemyX, enemyY X and Y coordinates of the enemy.

private float speed Speed of the enemy.

private int currentDirection, currentDirectionCollision0, currentDirectionCollision1, currentDirectionCollision2, currentDirectionCollision3 Current movement direction of the enemy, and randomized directions in case of collision.

private float remainingMoveTime Remaining time for each random move of the enemy.

private static float animateTime Animation time for sprite animation.

private static final float ANIMATION_FRAME_PERIOD = 0.1F Animation frame period for sprite animation.

Constructor public Enemy(float enemyX, float enemyY) Constructs an Enemy with the specified initial position.

Methods public TextureRegion getTextureRegion() Gets the texture region representing the current direction of the enemy.

public float getEnemyX(), public float getEnemyY() Gets the X and Y coordinates of the enemy.

public float getSpeed(), public void setSpeed(float speed) Gets and sets the speed of the enemy.

public void setCurrentDirection(int currentDirection) Sets the current movement direction of the enemy.

public void update() Updates the state of the enemy, including movement and random direction generation.

private void loadTurnAnimation() Loads the turn animation frames from the sprite sheet.

private void generateRandomDirection() Generates a random direction for the enemy to move and initializes the remaining move time.

private void moveCharacter(int direction) Moves the enemy character based on the current direction.

public void wallCollisionEnemy(Maze maze) Handles collision with walls by adjusting the enemy's position and direction.

@Override public boolean isMoveInvalid(float enemyX, float enemyY, Maze maze) Checks if the enemy's move is invalid, considering collision with walls.

public static void animateTimer(float delta) Updates the animation timer for sprite animation.

Example Usage

// Example usage of the Enemy class public class ExampleUsage { public static void main(String[] args) { // Instantiate an Enemy with initial position Enemy enemy = new Enemy(10, 20);

    // Set attributes for the enemy
    enemy.setSpeed(2.0f);

    // Access and use methods from the Enemy class
    TextureRegion textureRegion = enemy.getTextureRegion();
    float enemyX = enemy.getEnemyX();
    float enemyY = enemy.getEnemyY();
    float speed = enemy.getSpeed();

    // Update the state of the enemy in the game loop
    enemy.update();

    // Handle wall collision in the game loop
    enemy.wallCollisionEnemy(maze);
}
}

Maze Class :

The Maze class represents a maze loaded from a .properties file. It stores the map as a 2D integer array with additional fields for height, width, entry point coordinates, and key point coordinates. Values in the map array are assigned according to the following key:

0 = free path 1 = wall 2 = entry point 3 = exit point 4 = trap 5 = enemy 6 = key (Note that this is not equivalent to the mapping in the .properties file)

Attributes private int[][] map 2D integer array representing the maze map.

private int width, height Width and height of the maze.

private int entryPointX, entryPointY X and Y coordinates of the entry point in the maze.

private int keyPointX, keyPointY X and Y coordinates of the key point in the maze.

Constructors public Maze(String filePath) Parameters: filePath - The path to the .properties file containing the map. Description: Constructs a Maze object by loading the map from the specified .properties file. Methods public int getEntryPointX(), public int getEntryPointY(), public int getKeyPointX(), public int getKeyPointY() Return Type: int Description: Gets the x and y coordinates of the entry and key points in the maze. public int getWidth(), public int getHeight() Return Type: int Description: Gets the width and height of the maze. public int[][] getMap() Return Type: int[][] Description: Gets the map of the maze as a 2D integer array. private int[][] loadMap(String filePath) Parameters: filePath - The path to the .properties file containing the map. Return Type: int[][] Description: Loads the map from a .properties file and returns it as a 2D integer array. Example Usage

// Example usage of the Maze class public class ExampleUsage { public static void main(String[] args) { // Instantiate a Maze by providing the path to the .properties file Maze maze = new Maze("path/to/maze.properties");

    // Access and use methods from the Maze class
    int entryPointX = maze.getEntryPointX();
    int entryPointY = maze.getEntryPointY();
    int keyPointX = maze.getKeyPointX();
    int keyPointY = maze.getKeyPointY();
    int width = maze.getWidth();
    int height = maze.getHeight();
    int[][] map = maze.getMap();
}
}

Game Objects :

The provided code includes several classes representing different game objects in a maze game. These classes extend a common base class called GameObject and have specific functionalities and attributes related to their respective objects.

Heart Class (Heart.java)

The Heart class represents a collectible heart object in the game. Hearts are typically used as items to replenish a player's health. The class extends the GameObject class and has static texture regions for different animation frames.

Attributes:

public static final TextureRegion[] textures: Array of texture regions for different animation frames.

Key Class (Key.java)

The Key class represents a collectible key object in the game. Keys are often used as items to unlock certain doors or mechanisms in the maze. Similar to the Heart class, it extends the GameObject class and has static texture regions for different animation frames.

Attributes:

public static final TextureRegion[] textures: Array of texture regions for different animation frames.

Shield Class (Shield.java)

The Shield class represents a shield object in the game. Shields can provide protection or special abilities to the player. This class also extends the GameObject class and includes an array list of texture regions for animation frames.

Attributes:

public static final ArrayList textures: ArrayList of texture regions for animation frames.

SpeedBoost Class (SpeedBoost.java)

The SpeedBoost class represents a speed boost object in the game. Speed boosts are items that temporarily increase the player's movement speed. Similar to the other classes, it extends the GameObject class and has an array of textures for animation frames.

Attributes:

public static final Texture[] textures: Array of textures for different animation frames. These classes can be instantiated in your game logic to place and manage these objects within the maze. Ensure that you handle the rendering and updating of these objects appropriately within your game loop.

Trap Class (Trap.java)

The Trap class represents a trap object in the game. Traps are typically used to hinder or damage the player upon contact. This class extends the GameObject class and includes static texture regions for different animation frames.

Attributes:

public static final TextureRegion[] textures: Array of texture regions for different animation frames.

The Menus class serves as a superclass for menu screens in a game. It provides a common structure for menu screens, including a background image and a stage for UI elements. The class extends Screen, which is part of the LibGDX framework for managing screens in a game.

Menus Class :

Attributes:

protected final MazeRunnerGame game: Reference to the main game class, used to access global resources and methods. protected Stage uiStage: Stage for UI elements (buttons, etc.). protected Stage backgroundStage: Stage for the background. protected Sprite backgroundSprite: Sprite for the background image. protected Table table: Table to organize buttons and other UI elements. Constructor:

Initializes the class with a reference to the main game. Creates stages for UI elements and the background. Loads a background image and creates a sprite for it. Creates a table to organize UI elements. Adds the table to the UI stage. Methods:

render(float delta): Renders the menu screen. Draws the background image and renders the UI stage. resize(int width, int height): Called when the screen is resized. Updates the UI stage viewport and resizes the background sprite accordingly. dispose(): Disposes of resources when the screen is disposed. Disposes of both background and UI stages. show(): Called when the screen is shown. Sets the input processor so the stage can receive input events. Unused Methods (from Screen interface):

pause(), resume(), hide(): These methods are not used in this particular screen and are left empty. This class provides a convenient foundation for creating menu screens in a game, and specific menu screens can extend this class to inherit its common functionality. Each menu screen can customize its UI elements by manipulating the table and responding to user input through the uiStage. The background image is drawn based on the loaded sprite, and the class handles screen resizing gracefully.

MainMenuScreen Class :

The MainMenuScreen class is responsible for displaying the main menu of the game. It extends the LibGDX Screen class and sets up the UI components for the menu. Here's an overview of the class:

Attributes:

private static Music mainMenuMusic: Static variable for the main menu background music. Constructor:

Initializes the class by calling the superclass constructor (Menus). Sets up UI elements such as a title label and buttons for Play, Settings, and Exit. Adds listeners to the buttons to respond to user interactions. For example, the "Play" button switches to the LevelSelectionScreen when clicked. Adds UI elements to the table for organization. Initializes and plays the main menu background music. Static Method:

getMainMenuMusic(): Provides access to the main menu background music. The class leverages LibGDX's UI components such as Label for displaying text and TextButton for interactive buttons. The background music is played using the Music class, and listeners are used to handle button clicks and trigger appropriate actions, such as transitioning to other screens or exiting the game.

The MainMenuScreen serves as the entry point for users to navigate to different parts of the game, such as starting gameplay (LevelSelectionScreen), adjusting settings (SettingsScreen), or exiting the game. The background music enhances the overall user experience during navigation through the main menu.

The SettingsScreen class :

It represents the screen where the user can adjust game settings. It extends the LibGDX Screen class and sets up the UI components for the settings menu. Here's an overview of the class:

Attributes:

private final Skin skin: The Skin object for styling UI elements. Constructor:

Initializes the class by calling the superclass constructor (Menus). Sets up UI elements such as a title label ("Settings"), volume slider, speed slider, and a button to go back to the main menu. Adds listeners to the sliders to respond to changes in volume and player speed. Adds UI elements to the table for organization. Private Methods:

getVolumeSlider(): Creates and returns a volume slider with appropriate listeners. getSpeedSlider(): Creates and returns a speed slider with appropriate listeners. The class leverages LibGDX's UI components such as Label for displaying text, Slider for adjustable values, and TextButton for interactive buttons. The sliders allow the user to adjust the volume and player speed, and listeners are used to apply these changes to the game's audio and player speed.

The "Back to Menu" button allows users to navigate back to the main menu (MainMenuScreen). The class also ensures that background music is stopped when transitioning back to the main menu.

Overall, the SettingsScreen provides a user-friendly interface for adjusting game settings, enhancing the overall gaming experience.

The MinimapScreen class: This Class represents a screen that displays a minimap of the maze. It shows the current position of the player within the maze and provides functionality to dynamically adjust the size of the minimap.

Attributes:

private final MazeRunnerGame game: The main game class. private final Maze maze: The maze for which the minimap is displayed. private final OrthographicCamera camera: The OrthographicCamera used in the game. private final Character player: The player character in the maze. private final static Texture BROWN: Texture for brown tiles. private final static Texture GREY: Texture for grey tiles. private final static Texture RED_CIRCLE: Texture for the red circle representing the player. private float miniCellHeight: Height of each cell in the minimap. private float miniCellWidth: Width of each cell in the minimap. private float minimapSize: Size of the minimap, initially set to 0.1. Constructor:

Initializes the class by setting up attributes. Calculates initial sizes for cells based on the minimap size. Public Methods:

increaseSize(): Increases the size of the minimap within a certain range. decreaseSize(): Decreases the size of the minimap within a certain range. changeSize(float amount): Changes the size of the minimap based on the given amount. Private Methods:

drawMaze(): Draws the maze and the player on the minimap. getTile(int type): Returns the texture for a specific type of tile. Override Methods (from Screen interface):

render(float delta): Renders the minimap. show(), resize(int width, int height), pause(), resume(), hide(), dispose(): Not used in this screen. The minimap is drawn by iterating over the maze and rendering each cell based on its type. The player's position is represented by a red circle on the minimap. The size of the minimap can be dynamically adjusted within a specified range. The class leverages LibGDX's SpriteBatch to draw the textures on the screen.

The LevelSelectionScreen class : This class represents the screen for selecting game levels, including pre-defined levels (1-5) and a custom map option. It extends the Menus class and implements the Screen interface.

Attributes:

private static Music mazeMusic: The background music associated with the maze. Methods:

getMazeMusic(): Gets the maze background music. LevelSelectionScreen(MazeRunnerGame game): Constructor for the LevelSelectionScreen. Sets up buttons for levels 1-5 and a custom map. Initializes the maze music. loadMap(String mapPath): Loads the specified map and transitions to the GameScreen. Creates a Maze object using the specified map path. Sets the screen to a new GameScreen with the loaded maze. Stops the main menu music and plays the maze music. Disposes of the current screen. Button Listeners:

For each level button (1-5), a listener is added to load the corresponding map. For the custom map button, a file chooser dialog is displayed to choose a custom map. The chosen map is loaded if it has a ".properties" extension; otherwise, an error dialog is displayed. The back to the menu button transitions back to the main menu screen. Note:

The class uses LibGDX's NativeFileChooser for choosing custom maps, and it includes error handling for invalid map selections. The maze music is managed through the mazeMusic attribute, allowing control over its playback throughout the level selection screen. This class facilitates level selection and custom map loading, providing a smooth transition between different game screens.

The MazeRunnerGame class : It represents the core of the Maze Runner game. It manages screens and global resources like SpriteBatch and Skin.

Attributes:

gameScreen: Represents the current game screen. fileChooser: Manages file choosing functionality, typically used in a desktop environment. spriteBatch: Used for rendering graphics. skin: Represents the UI skin used in the game. topicFont, buttonFont: Fonts used for titles and buttons in the game. Constants for game settings, such as the number of volume and speed settings, maximum player speed, initial player speed, number of lives, and maximum number of collectibles.

Methods:

setPlayerSpeed(float playerSpeed): Sets the player's speed. getFileChooser(): Gets the NativeFileChooser used in the game. getTopicFont(), getButtonFont(): Gets fonts used in the game. create(): Called when the game is created, initializes SpriteBatch, Skin, and loads fonts and character animation. goToMenu(): Switches to the main menu screen, disposes of the current game screen if it exists. loadCharacterAnimation(): Loads the character animation from the "character.png" file. dispose(): Cleans up resources when the game is disposed.

Note:

Fonts are loaded using FreeTypeFontGenerator, and different fonts are used for titles and buttons. The goToMenu() method disposes of the current game screen if it exists, ensuring proper cleanup when transitioning between screens. The game uses a SpriteBatch for rendering and a Skin for UI elements. This class provides a central structure for managing the game's core components, making it easier to handle screens, resources, and settings.

The EndOfGameScreen class represents the screen displayed at the end of the game, either when the player wins or loses. It provides options for returning to the main menu.

Attributes:

stage: The stage for UI components. backgroundSprite: The background sprite for the screen. spriteBatch: The sprite batch for rendering. winMusic: The music played when the player wins. gameOverMusic: The music played when the player loses. game: The game instance.

Methods:

getWinMusic(), getGameOverMusic(): Gets the music played when the player wins or loses. constructor: Constructs an EndOfGameScreen with the specified game instance and result. show(), resize(), pause(), resume(), hide(): Empty implementations for the Screen interface methods. dispose(): Empty implementation for disposing resources if needed. render(float delta): Renders the screen, clearing the color buffer, drawing the background sprite, and rendering the stage. Also, checks for the ENTER key to go to the main menu.

Note:

The constructor initializes the UI components, background music, and sets up the table with a message label and a button to return to the main menu. The render() method renders the screen, and it includes a check for the ENTER key to go to the main menu. It utilizes a background image based on whether the player won or lost. The dispose() method is left as an empty implementation. If there are resources that need disposal, it can be extended. The class uses libGDX's Stage and UI elements like Label and TextButton for UI rendering.

The GameScreen class : It is responsible for rendering the gameplay screen, handling game logic, and rendering game elements. Here's a breakdown of the class:

Attributes:

game: The main game instance. maze: The maze for the gameplay. player: The character controlled by the player. camera: Orthographic camera for the game view. key: The key object that needs to be collected to win. CELLSIZE: The size of each cell in the maze. initialFrame: A boolean to trigger the camera's initial position in the first frame. enemies: List of enemy characters. isPaused: A boolean indicating whether the game is paused. hearts, traps, shields, speedBoosts: Lists of collectible objects in the game. timeTaken: Total time taken in gameplay, in seconds. shieldedTime: Time the player has been shielded, in seconds. shieldingTime: Time player can be shielded, in seconds. playerBlinks: A boolean indicating whether the player blinks during shielding. Methods:

GameScreen(game, maze): Constructor to initialize the GameScreen with the main game instance and maze. render(delta): Renders the game on the screen, handling player actions, collisions, and updating game elements. initializePauseMenu(game): Initializes the pause menu with buttons and their functionalities. restartGame(): Resets the game state for a restart. loadRandom(MAX, objectConstructor): Loads random collectible objects based on the specified maximum and object constructor. loadTraps(): Loads traps from the maze. endGame(isWon): Ends the game and transitions to the EndOfGameScreen with the specified win/loss status. drawMazeAndElements(): Draws the maze, characters, and collectible objects on the screen. getTile(type): Returns the corresponding tile based on the given type. drawHUD(): Draws the Heads-Up Display (HUD) showing player information. moveCamera(): Moves the camera to keep the player in view. updateGame(isPaused, delta): Updates character positions, animations, and game state based on whether the game is paused. isAtExit(): Checks whether the player is at the exit tile.

resize(width, height): Resizes the screen, updating the camera and pause stage viewport. pause(): Pauses the game. resume(): Resumes the game (not implemented). show(), hide(): Empty implementations for the Screen interface methods. dispose(): Empty implementation for disposing resources if needed. The class covers a wide range of functionalities, including handling player input, updating game elements, rendering the maze and objects, implementing a pause menu, and managing transitions between screens. Additionally, it includes logic for calculating the score, handling game over conditions, and transitioning to the end-of-game screen. The code is well-structured and organized, utilizing methods and appropriate class attributes to manage different aspects of the gameplay.
