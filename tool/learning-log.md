# Tool Learning Log

Tool: **Phaser**

Project: **Clicker Game**

---

10/29/23:
* This is the first [youtube video](https://www.youtube.com/watch?v=hI_LS8bdkM4) I tried and it teached me how to start the set up with phaser. I didn't finish the whole video yet because all I really wanted to know for know is how to start
* I tried my first test with the cdn. I saw some tutorial using npm but it was too confusing for me so I decided to try the cdn method which is way easier since all you have to do is put the script in the head of the code.
* After I am done setting everything up I needed to learn what to do next so I went on the [Phaser website](https://phaser.io/tutorials/getting-started-phaser3/part5) to learn the basic codes of Phaser. As shown below:
```js
<!DOCTYPE html>
<html>
<head>
    <script src="https://cdn.jsdelivr.net/npm/phaser@3.60.0/dist/phaser-arcade-physics.min.js"></script>
</head>
<body>

    <script>
    class Example extends Phaser.Scene
    {
        preload ()
        {
            this.load.setBaseURL('https://labs.phaser.io');

            this.load.image('sky', 'assets/skies/space3.png');
            this.load.image('logo', 'assets/sprites/phaser3-logo.png');
            this.load.image('red', 'assets/particles/red.png');
        }

        create ()
        {
            this.add.image(400, 300, 'sky');

            const particles = this.add.particles(0, 0, 'red', {
                speed: 100,
                scale: { start: 1, end: 0 },
                blendMode: 'ADD'
            });

            const logo = this.physics.add.image(400, 100, 'logo');

            logo.setVelocity(100, 200);
            logo.setBounce(1, 1);
            logo.setCollideWorldBounds(true);

            particles.startFollow(logo);
        }
    }

    const config = {
        type: Phaser.AUTO,
        width: 800,
        height: 600,
        scene: Example,
        physics: {
            default: 'arcade',
            arcade: {
                gravity: { y: 200 }
            }
        }
    };

    const game = new Phaser.Game(config);
    </script>

</body>
</html>
```
This was one of the code I saw in the tutorial page and just from looking at this I can figure out many things by changing the numbers. For example I learned that config is used to set the basic stats for the whole game or the coe you use to configure your Phaser game. Width and height would change the size of the game by increasing or reducing the width or height of the screen. I also learned that there are many syntax you can use to add physics to your game.





11/05/23:
* Today I am still learning the basics of Phaser but I didn't do much today since I am just exploring the foundations.
* I went to yesterday's example code and documentation again and learn the function of `type`. `type` is to set the redering context of your game.
* I also tried exploring on another [Phaser Tutorial Website](https://phaser.io/tutorials/making-your-first-phaser-3-game/part1). In this website I learned what `preload` and `create` do. You can use `preload` to store your image or sprites, its basically where you load your assents hence the name preload. And of course as you can tell by the name `create` is what you use to create your game which is where you put the basic codes in.


11/12/23
* I learned that `this.add.image` is used to create new Image Game Object which is a very essential part of phaser because you need a game object for any game or it would just be the background.
* `this.` is very powerful it can be used to add physics and text.
* I followed an example and learned how to add and create a score board. This would help me with my clicker game because I need a way to earn points after clciking on something.
* I tried to create a score board and its not that hard. You just have to create two variables that serves as the global scope. One called score and one called scoreText. Then you set the score to 0 and you can start using the two variable in your function. I learned that you can make the score increase or decrease after you do something and then you use this code `scoreText.setText('Score: ' + score);` to create a score text that would change as you add score.


11/19/23
* Today I am learning about a new variable called `player`. This basically allows you create a sprite or chracter that can move or be interacted with in game.
```js
player = this.physics.add.sprite(100, 450, 'dude');

player.setBounce(0.2);
player.setCollideWorldBounds(true);

this.anims.create({
    key: 'left',
    frames: this.anims.generateFrameNumbers('dude', { start: 0, end: 3 }),
    frameRate: 10,
    repeat: -1
});

this.anims.create({
    key: 'turn',
    frames: [ { key: 'dude', frame: 4 } ],
    frameRate: 20
});

this.anims.create({
    key: 'right',
    frames: this.anims.generateFrameNumbers('dude', { start: 5, end: 8 }),
    frameRate: 10,
    repeat: -1
});
```
* I tinkered with this code today and it teached me many things. `player = this.physics.add.sprite(100, 450, 'dude')` adds a new sprite called player positioned at 100 x 450 pixels from the bottom of the game. By tinkering with this code it allows me to modify the starting sprite position. Then I learned how to use the this.anims.create function. I think what this functions does is to create a set of animation that I can use to make my sprite move and this is very important when making a game because almost every game needs a moving character.


11/26/23
* Today I am learning about keyboard controls which is essential for any game.
* I looked through the documentations and saw that there are ways to manipulate your player using this function `cursors = this.input.keyboard.createCursorKeys();`. This populates the cursors object with four properties: up, down, left, right, that are all instances of Key objects.

Then I tinkered with this set of code from the [documentation](https://phaser.io/tutorials/making-your-first-phaser-3-game/part7):
```js
if (cursors.left.isDown)
{
    player.setVelocityX(-160);

    player.anims.play('left', true);
}
else if (cursors.right.isDown)
{
    player.setVelocityX(160);

    player.anims.play('right', true);
}
else
{
    player.setVelocityX(0);

    player.anims.play('turn');
}

if (cursors.up.isDown && player.body.touching.down)
{
    player.setVelocityY(-330);
}
```
I think this code is just a set of if/else statements basically if you hold down the left arrow then the character moves toward the left and if you hold down the right arrow you would move to the right. If you aren't pressing any key the velocity would be set to 0 meaning you would stop moving. By tinkering with the numbers I can changed how fast the character is moving in one direction. Later on this function can be modified to something more advance, I think by changing the code inside the if statements can change what the character would do after pressing a key.



12/3/23
* Today I was learning how to make a scoreboard which can be quite helpful for me because I need to have a kind of socre board to keep track on the amount of points they earned by clicking and there was a tutorial for it in the phaser [website](https://phaser.io/tutorials/making-your-first-phaser-3-game/part9).
* You can make text game objects like this:
```js
var score = 0;
var scoreText;
```
Then you put this set of code in the create function `scoreText = this.add.text(16, 16, 'score: 0', { fontSize: '32px', fill: '#000' });` This would essentially create a score display on the coordinate of 16 x 16. The font-size: 32px and fill is for the size of the text and the color, respectively. You can also change the font size but if you don't specify it then it would be Courier.

I tried to tinker with it and I realized that you can change the postion of the score board and color and the font. Then you can create object or actions for the player to do and that would either increase or decrease the point by simply doing something like "if player touches this: (insert something)" then `score += 2`, of course you can change how much points they get.



12/10/23
* Today I went to research on the [Phaser API Documentations](https://newdocs.phaser.io/docs/3.60.0/Phaser.Input.InputManager#events). In here I learned how to use input managers. These are very important because I need to make my object clickable or it wouldn't be a clicker game.

`this.input.on('pointerdown', onClick);` This line of code helps me create a click event. Now when the player clicks anywhere on the game screen, the onClick function is triggered. Then I will apply this to my object or upgrade button to help increase the score I earn from clicking.

```js
function onClick() {
    // Increase the score based on the click multiplier
    score += 1 * clickMultiplier;
    scoreText.setText('Score: ' + score); // update the score
}
```

12/17/23
* Today I tried to learn animations on the [Phaser 3 Doc](https://photonstorm.github.io/phaser3-docs/Phaser.Animations.Events.html#event:ADD_ANIMATION).
* The add animation event is dispatched when a new animation is added to the global Animation Manager. These animations can be applied to your character or your game objects. I also learned that you can combine phaser animations with the input manager I learned last week, so you can trigger an animation everytime you click.
* I learned the tweens class on the [Phaser documentation](https://photonstorm.github.io/phaser3-docs/Phaser.Tweens.Tween.html) for classes and it is a powerful class added in phaser that helps you create animations. A Tween is able to manipulate the properties of one or more objects to any given value, based on a duration and type of ease.

```js
// play a scale up animation on the clickableObject
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
I made this function after reading the documentation which adds a tween to the tween manager and runs a scale up animation to the clickable object.






2/4/24:
* Today I went to research on animations for my Clicker game and I learned that animations is hard because you have to understand a lot of concepts. The basic animation for phaser is to create an animation event for a sprite and this can be added to the global animation manager.
* This is the animation flow for Phaser:
    * ANIMATION_START
    * ANIMATION_UPDATE (repeated for however many frames the animation has)
    * ANIMATION_REPEAT (only if the animation is set to repeat, it then emits more update events after this)
    * ANIMATION_COMPLETE (only if there is a finite, or zero, repeat count)
    * ANIMATION_COMPLETE_KEY (only if there is a finite, or zero, repeat count)
* I learned that you need to specify the key, the frames and the frame rate of the animation.
* First, I need to create a sprite, then I just add the animation and play it with `sprite.anims.play`.
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
* This code just generates an animation on my testing clicking object when I click it. However, I didn't specify any animation yet.



2/11/24
* Today I tried to learn local storage in Javascript because I feel like I have most of the basics done at this point. I wanted to create upgrades that can make it so that the game can click the game object by itself
* This meant that I had to learn about the phaserTimer function
* In Phaser, timers are used to schedule and manage recurring events, delays, and callbacks.
* You can create a timer by using the `time` property and use the addEvent method to define the event or function with the parameter you want.
```js
 autoClickTimer = this.time.addEvent({
        delay: 1000,  // Automatic click every 1000 milliseconds (1 second)
        callback: autoClick,
        callbackScope: this,
        loop: true
    });
function autoClick() {
        score += 1;
        updateScoreText();
    }
```

This is an autoClicker function I made and the parameters are simple:
* `delay`: The time delay (in milliseconds) before the timer event is triggered.
* `callback`: The function to be called when the timer event is triggered.
* `callbackScope`: The scope in which the callback function will be executed.
* `loop (optional)`: Set to true if you want the timer event to repeat indefinitely.

I used loop because I want the autoclicker to continue the whole time.

* You can cancel timer events like this: `timerEvent.remove();`

3/3/24
* Today I tried studying about [local storage](https://www.w3schools.com/jsref/prop_win_localstorage.asp). I learned that local storage is a simple web storage that allows your website to store data.

* The localStorage object stores data with no expiration date.

* The data is not deleted when the browser is closed, and are available for future sessions.

* To use localStorage you would need a name and a value
`localStorage.setItem('key', 'value');` This is how localStorage works. You need a key which is the name you will use when you want to retrieve your data and the value would be the data it stores.

```js
var storedValue = localStorage.getItem('key');
console.log(storedValue);
```
You can then retrieve the data like this. The output of the console.log would just be "value".

* If I can use this in my Clicker game then I can track the stats of players. Maybe how much times they have clicked.



<!--
* Links you used today (websites, videos, etc)
* Things you tried, progress you made, etc
* Challenges, a-ha moments, etc
* Questions you still have
* What you're going to try next
-->
