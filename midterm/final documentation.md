# documentation
### [final fullscreen playing link](https://editor.p5js.org/insiyam/full/2M6Da1miN)

### [final code link](https://editor.p5js.org/insiyam/sketches/2M6Da1miN)

### complete process

##### stage 1: idea

for this project, i wanted to create a very simple but fun game about making jam. growing up i used to play all those cooking games on my mom’s phone and i still enjoy them now although less intensely. i added a background story and wanted to create a cute aesthetic to make a relaxing game.

##### stage 2: research

i researched many different games that i personally enjoy like stardew valley but i also looked up p5js  games because i was very lost in how to start the game making process. i came across the game, florp farming, online which was a very simple but fun game and i really liked the mechanics of it so i decided to base my game off of the same mouse drag gameplay.

##### stage 3: coding

since i went through so many trials and errors during this stage , for this documentation i will just go over my final code and comment as necessary.

the first js file to run in my code is my class called ingredients

```jsx
class Ingredient {
  constructor(img, x, y) {
    this.x = x;
    this.y = y;
    this.img = img;
    this.grabbed = false;
  }

  drawFruit() {
    imageMode(CENTER);
    image(this.img, this.x, this.y, 65, 60);
  }

  //dragging
  pressFruit() {
    let r = dist(mouseX, mouseY, this.x, this.y);
    if (r < 20) {
      this.grabbed = true;
    } else {
      this.grabbed = false;
    }
  }

  releaseFruit() {
    this.grabbed = false;
  }

  dragFruit() {
    if (this.grabbed == true) {
      this.x = mouseX;
      this.y = mouseY;
    }
  }
}
```

this is my class that controls the main gameplay and is a general code so i can adjust everything about the game but this mechanic will still work as its using external values only.

```jsx
function doubleclickButton() {
  fill(209, 172, 109);
  rect(width / 2, height - 49, 300, 40, 20);
  fill(153, 114, 72);
  textSize(20);
  text("doubleclick anywhere to move on", width / 2, height - 50);
}
function reset() {
  isjamready = false;
  jamcooking = false;
  let potx = 615;
  let poty = 330;
  let sbx = 200;
  let sby = 165;
  let sgx = 46;
  let sgy = 190;
  let jarx = 475;
  let jary = 360;
  count = 0;
  jamloop = 0;
  for (let i = 0; i <= 3; i++) {
    jam[i].x = jarx;
    jam[i].y = jary;
    fruit[0].x = sbx;
    fruit[1].x = sbx;
    fruit[2].x = sbx + 50;
    fruit[3].x = sbx + 50;
    fruit[0].y = sby;
    fruit[1].y = sby - 100;
    fruit[2].y = sby;
    fruit[3].y = sby - 100;
  }
  sugar.x = sgx;
  sugar.y = sgy;
}

//dragging
function mousePressed() {
  for (let i = 0; i <= 3; i++) {
    jam[i].pressFruit();
    fruit[i].pressFruit();
  }
  sugar.pressFruit();
}

function mouseReleased() {
  for (let i = 0; i <= 3; i++) {
    jam[i].releaseFruit();
    fruit[i].releaseFruit();
  }
  sugar.releaseFruit();
}

function mouseDragged() {
  for (let i = 0; i <= 3; i++) {
    jam[i].dragFruit();
    fruit[i].dragFruit();
  }
  sugar.dragFruit();
}
```
next, i created a separate js file with all my functions. i created a reset game function as well as a click anywhere to continue button. i actually got the idea of saying ‘double click anywhere’ from class on thursday when i saw fahad’s game. before that it was bit harder to tell when to click through screens since sometimes people expected the screen to move on its own like after the jam was finished so this cleared up things. i also moved the mouse pressed/releases/drag functions here to clear up space in the main sketch

this is the final script of the game and it includes the preload, setup and draw functions as well as the double clicked and keypressed which run the screen mechanics. 

```jsx
//initial positions
let potx = 615;
let poty = 330;
let sbx = 200;
let sby = 165;
let sgx = 46;
let sgy = 190;
let jarx = 475;
let jary = 360;
let bsktx = 120;
let bskty = 320;

//other variables
let jpotsprites = [];
let jpot;
let count = 0;
let w;
let h;
let jamcooking = false;
let isjamready = false;
let jamloop = 0;
let fruits = []; //for images
let fruit = []; //for objects
let jams = []; //for images
let jam = []; //for objects
let screen = 0;
let myfont;

function preload() {
  img = loadImage("assets/kitchen background.jpg");
  fruits[0] = loadImage("assets/strawberry.png");
  fruits[1] = loadImage("assets/apple.png");
  fruits[2] = loadImage("assets/grape.png");
  fruits[3] = loadImage("assets/orange.png");
  sgr = loadImage("assets/sugar.png");
  jpot = loadImage("assets/pot sprite.png");
  jams[0] = loadImage("assets/jam0.png");
  jams[1] = loadImage("assets/jam1.png");
  jams[2] = loadImage("assets/jam2.png");
  jams[3] = loadImage("assets/jam3.png");
  fruitbasket = loadImage("assets/fruit basket.png");
  basket = loadImage("assets/basket.png");
  myfont = loadFont("assets/Gaegu-Bold.ttf");
  click = loadSound("assets/click.mp3");
  twinkle = loadSound("assets/twinkle.mp3");
}
function setup() {
  imageMode(CENTER);
  rectMode(CENTER);

  createCanvas(800, 600);
  //sprite
  w = jpot.width / 4;
  h = jpot.height / 3;
  for (let i = 0; i < 4; i++) {
    for (let j = 0; j < 3; j++) {
      let spriteSmall = jpot.get(j * w, i * h, w, h);
      jpotsprites.push(spriteSmall);
    }
  }
  textFont(myfont);
  textAlign(CENTER, CENTER);
  //loading objects
  fruit[0] = new Ingredient(fruits[0], sbx, sby);
  fruit[1] = new Ingredient(fruits[1], sbx, sby - 100);
  fruit[2] = new Ingredient(fruits[2], sbx + 50, sby);
  fruit[3] = new Ingredient(fruits[3], sbx + 50, sby - 100);
  sugar = new Ingredient(sgr, sgx, sgy);
  for (let i = 0; i <= 3; i++) {
    jam[i] = new Ingredient(jams[i], jarx, jary);
  }
}

function draw() {
  //game beginning
  noStroke();

  //start screen
  if (screen == 0) {
    background(224, 191, 120);
    doubleclickButton();
    fill(153, 114, 72);
    textSize(95);
    text("THATS MY JAM", width / 2, height / 2 - 30);
    textSize(40);
    text("the life of a humble jam maker", width / 2 + 5, height / 2 + 30);

    image(jams[0], 80, 70, 60, 60);
    image(jams[1], 545, 430, 60, 60);
    image(jams[3], 670, 50, 60, 60);
    image(fruits[2], 165, 540, 65, 60);
    image(fruits[0], 100, 335, 65, 60);
    image(fruits[1], 350, 400, 70, 60);
    image(fruits[1], 460, 116, 70, 60);
    image(fruits[3], 690, 530, 70, 60);
    image(fruits[0], 670, 210, 70, 60);
    image(fruits[2], 230, 150, 60, 60);
  }

  //intro page
  else if (screen == 1) {
    background(224, 191, 120);
    textSize(35);
    text(
      "you live in small town where you sell jam",
      width / 2,
      height / 2 - 25
    );
    text(
      "at the weekly farmers market to make a living",
      width / 2,
      height / 2 + 25
    );
    doubleclickButton();
    reset();
  }
  //kitchen tutorial
  else if (screen == 2) {
    background(224, 191, 120);
    image(img, width / 2, height / 2, 830, 608); //background
    image(fruitbasket, 211, 185, 140, 85);
    doubleclickButton();
    fill(209, 172, 109);
    rect(width / 3 + 20, 470, 530, 90, 40);
    fill(153, 114, 72);
    textSize(20);
    text(
      "this is your home kitchen where the magic happens!! \n you can drag around the ingredients like sugar \n and fruits to make special  recipes to make delicious jam! ",
      width / 3 + 20,
      470
    );

    fruit[0].drawFruit();
    sugar.drawFruit();
  }
  //recipe hint/directions page
  else if (screen == 3) {
    background(224, 191, 120);
    textSize(35);
    // textWrap(WORD);
    text(
      "the farmers market is coming up so \n we need to get to work! \n remember that to make good jam,\n you need the finest of fruits \n and a little bit of sugar",
      width / 2,
      height / 2
    );
    doubleclickButton();
  }
  //jam reset page
  else if (screen == 4) {
    background(224, 191, 120);
    textSize(50);
    text("time to make some jam!!!!", width / 2, height / 2);
    doubleclickButton();
    reset();
  }
  //jam making screen
  else if (screen == 5) {
    background(220);
    image(img, width / 2, height / 2, 830, 608); //background
    image(basket, bsktx, bskty, 150, 150); //turn into basket image!
    image(fruitbasket, 211, 76, 140, 85);
    image(fruitbasket, 211, 190, 140, 85);

    if (jamcooking == false) {
      sugar.drawFruit();
      for (let i = 0; i <= 3; i++) {
        fruit[i].drawFruit();
      }
    }

    if (isjamready == false) {
      image(jpotsprites[count], potx, poty, 150, 112); //jam pot
    }
    for (let i = 0; i <= 3; i++) {
      if (
        dist(potx, poty, fruit[i].x, fruit[i].y) < 70 &&
        dist(potx, poty, sugar.x, sugar.y) < 70
      ) {
        jamcooking = true;
        if (jamloop < 1) {
          if (frameCount % 15 == 0) {
            count = (count + 1) % jpotsprites.length;
            if (count == 0) {
              count = 1;
              jamloop += 1;
            }
          }
        }

        if (jamloop == 1) {
          isjamready = true;
        }

        if (isjamready == true) {
          jam[i].drawFruit();
          fill(209, 172, 109);
          rect(width / 3, 490, 430, 40, 20);
          fill(153, 114, 72);
          textSize(20);
          text(
            "drag the jam to the selling basket to complete!",
            width / 3,
            490
          );
        }
        if (dist(bsktx, bskty, jam[i].x, jam[i].y) < 30) {
          doubleclickButton();
        }
      }
    }
  }
  //success page
  else if (screen == 6) {
    background(224, 191, 120);
    textSize(40);
    text("yay! you've succesfully made some jam!!", width / 2, height / 2);
    doubleclickButton();
  }
  //reloading page
  else if (screen == 7) {
    background(224, 191, 120);
    text(
      "thanks for playing! \n doubleclick anywhere to make more jam! \n click enter to restart the game",
      width / 2,
      height / 2
    );
  }
}
function doubleClicked() {
  if (screen < 5) {
    screen++;
    click.play();
  }

  if (isjamready == true) {
    if (screen >= 5) {
      screen++;
      click.play();
      twinkle.play();
    }
  }

  if (screen > 7) {
    screen = 4;
    click.play();
  }
}
function keyPressed() {
  print(mouseX, mouseY);
  if (screen >= 7) {
    if (keyCode == ENTER) {
      screen = 0;
      click.play();
    }
  }
}

```
i have a lot of initializing variables as the different objects all require their own unique position since the results are calculated through dist().i also preloaded my fruit and jam images into separate arrays but their index corresponds which is how i was able to align the jam colours to each fruit. 

in setup i created a for loop for the sprite as well which runs every time the jam is cooking. i also used for loops through out my code to avoid rewriting the lines of code since everything was organized through arrays.

in draw(), the actual game screens are set up using if statements. the first page is the title page where i just added some text and images. (btw the screen numbers ad the ‘pages’ i’m mentioning here don’t line up perfectly since the screen starts at zero but you can still follow along.) page 2 and 4 are helpful storytelling pages but page 3 is the more tutorial type page that you can drag around the strawberry and sugar in. page 5 is the ‘reset’ page so every time the game loops at the end it lands here to make sure all the functions are reset since it would glitch if i ran the reset() function on page 6, where the jam is actually made. this is the main page of the game and i had created this first ( as visible in the previous documentation) before adding into the click screen mechanism. page 7 and 8 are just endgame pages and they also play a cute success sound. 

lastly i used what i learned in the web development workshop with jack to add a background to the page to a create a  more cozy experience

this coding experience was a rollercoaster for me, like my other projects as well. nonetheless, i think it turned out okay at the end and although im sure there were ways to simplify my code in many ways, i think its pretty organized and definitely my best work.

##### stage 4: story and art board

this stage was the one i started first but ended last and was my personal favourite part of the project. i actually didn't realize we could use images from the internet so i decided to create all my images myself. in hindsight, i probably would have still drawn all my images anyways because i had a specific artistic vision. i wanted to create warm and inviting kitchen inspired by some pictures online (and also dakota johnson’s kitchen if you know what that is). i worked entirely in adobe illustrator at the library computers using a wacom tablet i checked out. this was my first time doing actual drawn digital art and there was a lot of learning but i was surprised by how quickly i got a hang of it. first i created a sketch page where i finalized my colour pallete. it was very important to me that all the colours went well together and because i wanted a simplistic style i tried to reuse colours instead of creating varying shades. then i drew all of my images which can all be viewed in the assets folder  in the google drive. i tried to make the design very simple and also used some tactics like outlining all the draggable objects in special colour which help with user experience. unfortunately, the images warped a bit when they became objects because the fruits all vary a bit in proportions but i had preset the size for the all in my class. this would have been easily fixed by adding more constructors and allowing you to add the size in set up but i felt it wasn’t too noticeable, i just think the images look cuter in their original proportions haha. 

### reflection

overall i really enjoyed making this game and im pretty happy with the result. i like how it pays homage to my earlier projects like the strawberry loop etc and it feels very authentic to me. i would love to work more on it perhaps and create more elements to the story so its not just a jam simulator but a full fledged rpg type game with player choices and everything. i would also want to add some more interactive details in the non jam making page like maybe animating the text on other screens to make it more fun. i definitely learned a lot during this process but it was also very rewarding to see how much i already knew and how comfortable i have become with just trying out code ideas instead of becoming stuck.
