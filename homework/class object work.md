# documentation #
for this assignment i wanted to create a scene inspired from nature and farms. i was deciding between bees or strawberries before settling on the latter.

i first started by creating a blue sky background and began working on making my strawberry. i created my shapes in the draw function. i used simple shapes like ellipses and traingles to create this drawing. i have (thankfully) learned from my classmates and i used the 

if (mouseIsPressed === true) {
    print(mouseX, mouseY);
    
code to create precise shapes. i then moved this into a new seperate drawStrawberry function and created a class. i then also converted all the points in my shapes to be variable based so all parts of the strawberries would be proportional. i aslo added a bush i=behind all my stawberries.

next i started working on the most challenging part of my idea: animating these strawberries. this part took the most trial and error as i kept trying different ideas including making a mousePressed function and many others. i created a new attribute in my class called 'size' and tried to create different functions.[at this point]() i had already decidited of a starting size of 40 and final stage of 80 but i i was struggling to find a function that create smooth transition between them. then i remembered the first self portrait hw we did and that my friend bato had created a cool bubblegum animation where the ellipse smoothly increased. i looked to his code for inspiration and realized i could use the modulo function to make this smooth change. i applied this to the seed ellipses as well but despite trying i could not firgure out how to increase the triangles smoothly as they dont have a 'size' argument. although i had created this msooth transition i could not figured how to set extra paramters on the modulo to adjusting the starting size. i decided on a simple fix of overlaying a size 40 ellipse to give the illusion of a starting point. now that my strawberries were growing nicely i started trying to add a colour changing aspect. i wanted to mimic the real life growth of a strawberry as it starts from a green bulb into the bright red fruit. after consulting some of my friends i tried using the noise function in this code

 let r = 255* noise(t+10);
    let g = 255* noise(t+20);
    let b = 255* noise(t);
    fill(r, g, b);
    t=t+0.01;
    
but no matter how i tried to tweak it, it was still changing to fast in a range too wide. i then decided to use the frameCount variable again to adjust the color direclty in the fill section. although this working better i still couldnt get it to sync with the growing loop. i finmally had an epiphany of using the same frameCount % this.size value as it would have the same computation and everything would all sync up. 

finally! i had finished creating my looping animation and everything was working smoothlly.

now i was on to decorating and creating a prettier background for my strawberries! although i tried to creat an automated system for creating the clouds i struglled to create a randomized scene of clouds without them sifting constantly.

let cloudx = random(50, 300);
  let cloudy = random(20, 80);
  for (let k = 0; k < width; k = k + 45) {
    for (let l = 0; l < 0.4 * height; l = l + 3) {
      fill(218, 230, 235);
      ellipse(k, l, cloudx,cloudy);
    }
  }

i know this is because of the recurring nature of the draw loop but i was also not able to put it in set up so i just manually created some clouds for the background. i alsoe addes some extra leaves to the bushes to fill up the negative space.

lastly i cleaned up my code and reorganized it to create my [final work.](https://editor.p5js.org/insiyam/sketches/SQB4oCeKu-)
