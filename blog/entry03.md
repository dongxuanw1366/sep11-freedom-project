# Entry 3
##### 2/5/24

After learning the basics and tutorials of Phaser, I decided to move on and study more on things that will help me make my clicker game. Somethings I learned were animation and tweens. During this time I also started to create a bit of a start for my clicker game.

```js
const config = {
    type: Phaser.AUTO,
    width: 800,
    height: 600,
    scene: {
        preload: preload,
        create: create,
        update: update
    }
};

const game = new Phaser.Game(config);
let score = 0;
let clickMultiplier = 1;
let scoreText;
let upgradeText;

function preload() {
    // Load any assets (images, sprites)
    // don't know what images/sprites to add yet
}

function create() {
    // Create the main game objects

    // Display the score
    scoreText = this.add.text(16, 16, 'Score: 0', { fontSize: '32px', fill: '#fff' });

    // Display the upgrade button
    upgradeText = this.add.text(16, 60, 'Upgrade Click (+1) Cost: 10', { fontSize: '16px', fill: '#fff' });
    upgradeText.setInteractive({ useHandCursor: true });
    upgradeText.on('pointerdown', buyUpgrade);

    // Set up the click event on the game
    this.input.on('pointerdown', onClick);
}

function onClick() {
    // Increase the score based on the click multiplier
    score += 1 * clickMultiplier;
    scoreText.setText('Score: ' + score);
}

function buyUpgrade() {
    // Check if the player has enough points to buy the upgrade
    if (score >= 10) {
        // Deduct the cost of the upgrade
        score -= 10;

        // Increase the click multiplier
        clickMultiplier += 1;

        // Update
        scoreText.setText('Score: ' + score);
        upgradeText.setText('Upgrade Click (+' + clickMultiplier + ') Cost: ' + (10 + clickMultiplier * 5));
    }
}
```

These are the functions I have so far, so basically I created a clicker game layout for now. This is the very basic I need which contains a basic upgrade button and an object (not added yet, probably going to be an image) that I can click on to increase my score points so I can buy upgrades. The `create()` function creates the upgrade buttons and a score text that updates to keep track of how much score point I have. (This is probably going to be changed into something like how much money I have). The onClick function basically increases the score I get and the score can be increased based on the upgrade I have. `buyUpgrade()` function helps me set the stats of an upgrade button, like what happens if I buy the upgrade.

After this I decided to learn tweens and animation which is very similar in a way. I used [Tweens Phaser documentation](https://photonstorm.github.io/phaser3-docs/Phaser.Tweens.Tween.html) to learn about Tweens. Tweens in Phaser basically mean "animation", a Tween is able to manipulate the properties of one or more objects to any given value, based on a duration and type of ease.

```js
// the game object gets better when clicked
this.tweens.add({ // creates and manage tweens (animations)
    targets: clickableObject, //specify the target so the animation is only applied to this target
    duration: 200, // how long in milliseconds
    // target scaling
    scaleX: 1,
    scaleY: 1,
    onComplete: () => {
        // Increase the score based on the click multiplier
        score += 1 * clickMultiplier;
        scoreText.setText('Score: ' + score);
    }
});
```
The add animation event is dispatched when a new animation is added to the global Animation Manager. I also learned that you can combine phaser animations with the input manager so you can trigger an animation everytime you click.

[Animations](https://photonstorm.github.io/phaser3-docs/Phaser.Animations.Animation.html#frameRate__anchor) in phaser is something else I learned. The difference between animation and tweens is that animations is usually used for displaying a sequence of frames in a sprite sheet to create motion and tweens is used for smoothly animating properties (position, scale, alpha, etc.) of game objects. Animations are based on frames while tweens are based on duration (time units).

* This is the animation flow for Phaser:
    * ANIMATION_START
    * ANIMATION_UPDATE (repeated for however many frames the animation has)
    * ANIMATION_REPEAT (only if the animation is set to repeat, it then emits more update events after this)
    * ANIMATION_COMPLETE (only if there is a finite, or zero, repeat count)
    * ANIMATION_COMPLETE_KEY (only if there is a finite, or zero, repeat count)

```js
this.load.spritesheet('test', 'assets/clickingObject.png', { frameWidth: 64, frameHeight: 64 });

// Create a sprite in the create function
var test = this.add.sprite(400, 300, 'test`);

// Add the animation to the sprite
this.anims.create({
    key: 'click',
    frames: this.anims.generateFrameNumbers('test', { start: 0, end: 3 }),
    frameRate: 10,
    repeat: 0
});

// Play the animation on the sprite when it is clicked
test.setInteractive();
test.on('pointerdown', function () {
    test.anims.play('click');
});
```
This is a testing code I sort of made to see how animation would work on my clicker game but after a few rounds of testing I realized that tweens is still better for a clicker game because I don't technically need an animation since I have no sprites that I need to animate in a clicker game.

I am definitely planning on learning how to make the game automatically click the gaming object. I did a bit of research and I feel like the timer function in phaser would be useful because I can manipulate the interval of time when the game automatically clicks. Another thing I want to learn is how to make my game run offline since I am trying to make an idle clicker game and you can afk on it. This meant that I need to have a way to store my data, I think I should study what localStorage are in javascript to help me store the data of players.

Currently, I am on step 4 and 5 of the **Engineer Design Process**. I am trying to plan out my game and see what I should learn and add to my game to make the game more intresting and farm-able. Then I will be starting to create my game, so far I think I just started to create my game because I can still add so much more features to this game but I am still not sure how much stuff I should add.

The skills I used for this blog is **Debugging**, **how to google** and **how to read**. Debugging because I need to read through my code carfully and see if I made any mistake because when I was trying to create the basic layout of my game, I encountered many issues like the upgrade button doesn't work sometime or when things aren't positioned properly. I had to see where I made an error and fix it. How to google because I needed to know what to learn and find it on google so I can study it. How to read because I had to read through many documentations to get the code I needed and understand how the code works.

[Previous](entry02.md) | [Next](entry04.md)

[Home](../README.md)
