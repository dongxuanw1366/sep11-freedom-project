# Entry 4
##### 3/16/24

In this blog I will demonstrate the progress I made towards the MVP and how I have been learning my tool.

So far, I have made the basic layouts of my clicker game. Which means that I already have the canvas and the clicking function set up.

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

This is the starter code I have so far which contains a basic upgrade button and an object (not added yet, probably going to be a sprite) that I can click on to increase my score points so I can buy upgrades. The `create()` function creates the upgrade buttons and a score text that updates to keep track of how much score point I have. (This is probably going to be changed into something like how much money I have). The onClick function basically increases the score I get and the score can be increased based on the upgrade I have. `buyUpgrade()` function helps me set the stats of an upgrade button, like what happens if I buy the upgrade.

Then I tried to improve my project by adding special upgrade that doesn't just boost the muliplier of the points I get. I got an upgrade that helps you click automatically, this can be very useful in a game like mine because contsantly clicking by myself can get reall boring. So I learned the timer function in phaser.

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
* `delay`: The time delay (in milliseconds) before the timer event is triggered.
* `callback`: The function to be called when the timer event is triggered.
* `callbackScope`: The scope in which the callback function will be executed.
* `loop (optional)`: Set to true if you want the timer event to repeat indefinitely.

This is the function I made that can help me click automatically and I might have to add it into an upgrade area which I still need to make. Keeping the upgrades in one area will make it look nice and neat. Then I should add more functions that can make the auto click go faster and higher multiplier for each click.

After this I feel like I have some sort of the basics of an mvp (still need css). So I decided to learn something called localStorage in javascript which is a way to store small amount of data. This is needed in a game like mine because no one wants to have their progress resetted after exiting the game.

So far this is what I learned about localStorage:
* The localStorage object stores data with no expiration date.

* The data is not deleted when the browser is closed, and are available for future sessions.

* To use localStorage you would need a name and a value
`localStorage.setItem('key', 'value');` This is how localStorage works. You need a key which is the name you will use when you want to retrieve your data and the value would be the data it stores.

```js
var storedValue = localStorage.getItem('key');
console.log(storedValue);
```
This would be how you can retrieve the data like this. The output of the console.log would just be "value" in this example.

* localStorage is usually used to track user preferences and language, theme or status, like if they are logged in or not.

However, I saw an example from [w3schools](https://www.w3schools.com/jsref/prop_win_localstorage.asp) that can track how much times an user clicked something.

```js
if (localStorage.clickcount) {
  localStorage.clickcount = Number(localStorage.clickcount) + 1;
} else {
  localStorage.clickcount = 1;
}
```

After looking at this example, I feel like I can use this to create some sort of data because people usually like to see how much times they click or to see some sort of achievement in the game. I can also uses this to give back the progress maybe. For example I track the amount of score and update they have and give it back when they refresh the page.

One downside about localStorage is that it can't store large amounts of data.

Currently, I am on step 4 and 5 of the **Engineer Design Process**. I am trying to plan out my game and see what I should learn and add to my game to make the game more attractive and interesting. Then I will be starting to create my game, so far I think I just started to create my game because I can still add so much more features to this game but I am still not sure how much stuff I should add. I should definitely add some css because the game looks very ugly so far.

The skills I used for this blog is **Consideration**, **how to google** and **how to read**. Consideration because I need to consider what people would like so I can decide on what to add next, I need to be considerate and try to make the game more fun and enjoyable for everyone. How to google because I needed to know what to learn and find it on google so I can study it and apply it to my code. How to read because I had to read through many documentations to get the code I needed and understand how the code works or I won't be able to use it in my project.




[Previous](entry03.md) | [Next](entry05.md)

[Home](../README.md)
