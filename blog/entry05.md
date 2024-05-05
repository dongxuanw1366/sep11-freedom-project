# Entry 5
##### 5/4/24

As time passes I feel like I have learned enough information about phaser.js. Now I can start moving towards my MVP. I started off by making my canvas.

```js
var config = {
    type: Phaser.AUTO,
    parent: 'game-container', // Parent element ID
    width: window.innerWidth, // Set canvas width to match window width
    height: window.innerHeight, // Set canvas height to match window height
    scene: {
        preload: preload,
        create: create
    }
};
```
This is the javascript for the canvas and with this you just have to add a div to create the canvas `<div id="game-container"></div>`. You have to create it with the parent element id however.

After I made the canvas, I need to add an image as my object for clicking. For the image I used a gold-colored button and I made it interactive, whenever I click the button it shrinks and whenever I release the mouse it grows back to normal size.
```js
 // Create a button sprite
button = this.add.image(0, 0, 'button');
button.setOrigin(0.5); // Set the origin to the center of the button
button.setScale(0.35);

// Position the button initially
updateButtonPosition();

// Add pointer events to the button
button.setInteractive();
button.on('pointerdown', onClick);
button.on('pointerup', onRelease);
```
This creates a button and adds animation to it. Then I created a scoreboard and the score will increase as you click the button.

After all of those, I needed to have upgrades so the multiplier increases, or clicking on 1x multiplier would be really slow and boring. I wanted to learn how to store upgrades together, so I learned objects in javascript. From this [Javascript object website](https://www.w3schools.com/js/js_objects.asp) I learned that you can store objects like this in javascript: `const car = {type:"Fiat", model:"500", color:"white"};`. Then I tried it in my project and created the following upgrades.
```js
var upgrades = [
    { category: 'Mouse', name: 'Mouse', cost: 10, multiplier: 0.5 },
    { category: 'Human', name: 'Human', cost: 100, multiplier: 3 },
    { category: 'Robot', name: 'Robot', cost: 500, multiplier: 10 },
    { category: 'Gun', name: 'Gun', cost: 5000, multiplier: 50 },
    { category: 'Rocket', name: 'Rocket', cost: 100000 , multiplier: 500 }

];
```
This way I can keep track of how much multiplier the upgrade gives and what is the cost of every upgrade.

```js
// Create upgrade buttons
for (var i = 0; i < upgrades.length; i++) {
    var upgradeButton = this.add.text(-30, 80 + 130 * i, upgrades[i].name + '\nCost: ' + upgrades[i].cost, { fontFamily: 'Arial', fontSize: 25, color: '#ffffff', wordWrap: { width: 1000 } });
    upgradeButton.setOrigin(1, 0);
    upgradeButton.setInteractive();
    upgradeButton.upgradeData = upgrades[i]; // Store upgrade data in the button
    upgradeButton.on('pointerdown', function () {
        upgradeMultiplier(this.upgradeData);
    });
    upgradeSection.add(upgradeButton);
    upgradeButtons.push(upgradeButton); // Store the upgrade buttons in an array
    // Initialize upgrade count for this category
    upgradeCounts[upgrades[i].category] = 0;
}
```
Then I used a for loop to iterate through the upgrades and create them as buttons. Then I can track how much upgrades I brought for that one category and how much the cost is because the cost increases with every purchase. With all of this I am basically done with the MVP.

Currently, I am on step 5 and 6 of the **Engineer Design Process**. I am now creating my game and testing it to see if it works out and find whatever to improve on. I am using all the knowledge I have so far to create the "prototype"/MVP, and I have to test the code and make sure that it works the way I wanted and check for bugs.

The skills I used for this blog are **Problem Decomposition**, **Debugging** and **How to Google**. Problem decomposition was important because I need to break down my game into smaller piece so I can visualize it better and code it out. I need to know what I should have in the game and what I need, for example I knew I need a place to track the score from clicking and an object to click on, and upgrades to earn score faster. Debugging because when I tried to make the game I often run into errors like the animation doesn't work or score isn't going up when I click the button and the upgrade counts would go up for every upgrade even though you didn't buy it. To fix all these issues I had to debug my code and figure out what to fix and should I add any code. How to google because sometime I might be stuck and I needed to find some ways to solve the problem, for example, I didn't know how to use objects in javascript so I went to google it and it worked out for me.







[Previous](entry04.md) | [Next](entry06.md)

[Home](../README.md)
