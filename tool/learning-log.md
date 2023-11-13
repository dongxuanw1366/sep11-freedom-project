# Tool Learning Log

Tool: **Phaser**

Project: **Clicker Game**

---

10/28/23:
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


11/13/23
* I learned that `this.add.image` is used to create new Image Game Object which is a very essential part of phaser because you need a game object for any game or it would just be the background.
* `this.` is very powerful it can be used to add physics and text.
* I followed an example and learned how to add and create a score board. This would help me with my clicker game because I need a way to earn points after clciking on something.
* I tried to create a score board and its not that hard. You just have to create two variables that serves as the global scope. One called score and one called scoreText. Then you set the score to 0 and you can start using the two variable in your function. I learned that you can make the score increase or decrease after you do something and then you use this code `scoreText.setText('Score: ' + score);` to create a score text that would change as you add score.









<!--
* Links you used today (websites, videos, etc)
* Things you tried, progress you made, etc
* Challenges, a-ha moments, etc
* Questions you still have
* What you're going to try next
-->
