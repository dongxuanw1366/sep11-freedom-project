# Entry 2
##### 12/16/23

After I selected my code which is Phaser, I needed to start learning Phaser and move on from just the basics. This meant that I tried to learn something more advanced. One thing I tried to learn was keyboard controls which is essential for many game because everyone loves shortcut keys when you are playing a game. Then you can either use these keyboard controls to manipulate your character or call "functions" to run in the game. I tried to understand how to do keyboard controls by looking at a tutorial on the [phaser website](https://phaser.io/tutorials/making-your-first-phaser-3-game/part7). In the tutorial I learned this function: `cursors = this.input.keyboard.createCursorKeys();` which creates the cursor keys. Then I tried to tinker with the following code which is this:
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
So basically this set of code checks what key you are clicking on and runs a certain function. For example in the code above whenever you move left or right it will change your location. I tried changing the numbers and it gave me different results. I also tried putting other functions like a loop but it didn't work out correctly probably because this if/else statement is used to control the sprite or its because I needed to put a phaser related code. Then I learned something else that I need for my clicker game which is the input manager on the [Phaser API Documentations](https://newdocs.phaser.io/docs/3.60.0/Phaser.Input.InputManager#events) website.

Something I learned and can be applied to my game is this function `this.input.on('pointerdown', onClick);` this basically triggers the onClick funtion everytime I click.

```js
function onClick() {
    // Increase the score based on the click multiplier
    score += 1 * clickMultiplier;
    scoreText.setText('Score: ' + score); // update the score
}
```
I can apply this code to every of button and I can also create a upgrade button that increases my clickMultiplier.

I also had to learn a scoreboard function `scoreText = this.add.text(16, 16, 'score: 0', { fontSize: '32px', fill: '#000' });`. This would essentially create a score display on the coordinate of 16 x 16. The font-size: 32px and fill is for the size of the text and the color, respectively. I tried to tinker with it and I realized that you can change the postion of the score board and color and the font. Then you can create object or actions for the player to do and that would either increase or decrease the point by simply doing something like "if player touches this: (insert something)" then `score += 2`, of course you can change how much points they get.

My freedom project goal for this Chrismas is to learn my tool even further by learning the events and game objects section on the [phaser3 doc](https://photonstorm.github.io/phaser3-docs/index.html), like input managers and animations (maybe also maps, graphic and sprite) and start creating and setting up my freedom project. I want to at least have a base game where I can just click on something and earn points. I also want to create some upgrade buttons for my clicker game so I can make my game more interesting. One of the upgrade would definitely be an auto clicker because I am trying to make my game more idle and can be farmed, so I probably have to dig in to how to make the game auto click, might also change the theme so something would happen when you start clicking (maybe this is where animation comes in).

Currently, I am on step 2 and 3 of the **Engineer Design Process**. I am still researching on how to create my Phaser game and I am also brainstorming on what I can make and add to this clicker game. During my winter break I will research on Phaser and think of things I can do to make my clicker game more entertaining and more interesting. I have to make up plans on what I can do and slowly come up with the best one.

The skills I used during this period of time are **how to google**, **consideration** and **problem decomposition**. I used how to google to help me find documentations and sources for me to learn phaser and gain ideas on what to do for my freedom project. I used consideration to make sure what I should add into my game to make the game fun and interactive. I also used problem decomposition to breakdown my project into parts so I know what I should start first and what how I should create my game step by step. The parts of my project are probably going to be the base, game object and upgrades.

[Previous](entry01.md) | [Next](entry03.md)

[Home](../README.md)
