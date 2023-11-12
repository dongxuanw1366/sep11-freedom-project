# Entry 1
##### 11/11/23

The tool I decided on for the SEP11 was Phaser. At the start, I was really confused on what I should make for this year's freedom project because with the tools avaliable it looked like there was an unlimited amount of things you can do with Javascript. However, I still decided to focus more on games. So, the two tools I had left was Kaboom and Phaser, I was really conflicted on which one to pick because they both are good for making games, but after a bit of tinkering and research on both tools I decided to do Phaser. Phaser has more features and flexibility as well as more doucumentation and tutorials since its been out longer than Kaboom. Now, I have to decide on what kind of game I should make, this was a really tricky one because there a many options out there for me to click and I don't know which one to pick, but I still decided to do a clicker game that was inspired by [Cookie Clicker](http://orteil.dashnet.org/cookieclicker/).

Then I started to tinker with Phaser, as shown below:

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
I learned that config is used to set the basic stats for the whole game or the coe you use to configure your Phaser game. Width and height would change the size of the game by increasing or reducing the width or height of the screen. I also learned that there are many syntax you can use to add physics to your game. Then I just messed around with the numbers in this code, for example, changing the velocity and speed can increase the rate of bounce with the particle. These information might be good when it comes to making my clicker game since these are the fundamentals of phaser. You need to use `config`, `preload ()` and `create ()` almost everytime you start a phaser project.

Some links I used to learn Phaser was: [Phaser tutorial youtube video](https://www.youtube.com/watch?v=hI_LS8bdkM4) (I didn't watch the whole video, I only watched a bit to get started) and [the Phaser tutorial website](https://phaser.io/tutorials/getting-started-phaser3/part5). I also tried the [Kaboom tutorial website](https://kaboomjs.com/doc/intro) to see if I would use Kaboom or Phaser.

As of now, I am on the first stage of the engineering design process and maybe a bit on the second step. The "problem" I am trying to define is basically my clicker game using Phaser because that's what I want to create. To solve this "problem", I need to first learn how to use Phaser to create a game which is the goal of my researches. I plan on reading through the tutorials and watch some youtube video to get started on my clicker game project.

The skills I used to make this blog are **how to google**, **consideration** and **how to read**. I had to google a lot to find the correct sources that I am going to use to study Phaser and I needed to research for ideas on my project, like what kind of features am I going to have in my clicker game. The skill "how to read" really comes with "how to google" because after I googled about the Phaser documentations I had to read it throughly and take down notes so I will understand what everything does and apply it in my project. The skill consideration is very important during the start of the freedom project because I had to really consider what am I going to make and would this project fit me. I also have to consider what I am going to add to my project after I decide on one and also decide on which tool is the best for this project.


[Next](entry02.md)

[Home](../README.md)
