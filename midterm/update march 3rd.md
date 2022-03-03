# documentation
### [most current succesful version](https://editor.p5js.org/insiyam/sketches/qzSbPWrcM)
because i duplicate and create a new file everytime i try to add/modify a feature this is the most recent working game although it is not the one i am currently working on
### progress
ill just be following up from my previous update in this new file as otherwise it gets very slow
##### stage 3 : story and artboard
as mentioned before, since i know this will the section i enjoy the most and hence can very perfectionist about, i've decided to delay making all the original art work till i know exactly what i need to draw. to combat this, ive just been making relatively quick sketches of the images i need as i go along writing the code. because of that i've had to exclusively work from library/copier room deskstops so i can use adobe and then aslo directly upload to p5js since it wouldn't work on my laptop. the designs of the original art will follow the sketches to an extent but i want to create a more cutesy and retro aesthetic almost inspired by scrapbooky illustartions like [this](). ive rented out a wacom tablet from the library and i'm very excited because ive never created actual digital art before even though it seems a bit intimidating currently. i plan on completely finishing the code this weekend so in the days leading up to deadline i can just relax and focus on creating drawings.
##### stage 4 : coding
this has been the main focus of my work so far as i really am figuring it out as i go and i want to finalize this section before moving onto the drawings so i'm not doing unecessar artwork. since the last update my code has changed very very drastically. i used the ```grabbed = true``` strategy from the simple ellipse drawing and actually used an array for the first time so i could create the draggable objects. i used the ```function mousePressed(){
  let d = dist(mouseX,mouseY,sbx,sby);
  let f = dist(mouseX,mouseY,sgx,sgy);
  if (d<sbsize){
    print("hello")
    grabbed[0] = true;
  }
   else if (f<sbsize){
    //print("hello")
    grabbed[1] = true;
  }else{
    grabbed[0] = false;
    grabbed[1] = false;
  }
}
function mouseReleased(){
  grabbed[0] = false
  grabbed[1] = false
}
function mouseDragged(){
if(grabbed[0]){
  sbx = mouseX
  sby = mouseY
} else if(grabbed[1]){
  sgx = mouseX
  sgy = mouseY
  ``` which i adapted from a tutorial from the most helpful person i've found on youtube, william mclean. i pretty much watched all his videos along with the coding train where i learned about setting up code to acheive something and then adapted from there. i also created my first sprite so i could play a cute little animation when the ingredients hit the pot. as you know, i found a way to control when the images appeared with your idea of creating new conditions based on the progress of the jam process. i used this sae idea again by creating another condition ```jamcooking``` which controls the ingredients along with ```isjamready``` which i set to control if the pot and jam jar was there.
  
  after achieving the entire jam making loop, i decided to move onto creating the story with code. using another william mclean tutorial, i created a ```screen``` variable and used a series of if statements to play through the slides of the game. originally i wanted to shift through the slides by ```mouseClicked``` or ```mousePressed``` functions but i think it was inteferring with the dragging ingredients mechanic so i shifted to using the left and right arrow to click through. i added a simple background story to give some details and explain directions on how to play. i plan on adding more screens to create more storytelling still.
  
  next i (surprisingly) used another array to add different types of fruits to create more diversity i gameplay and give the player more freedom. i struggled a bit to find a way to be able to pick which fruit to use and tried to use a for loop for a long time before settling on the ```keyPressed``` function and using the indiviudal keycodes to set the index of the array.
  
  unfortuantely, i still hadnt added any actual obejcts to my code which is a requirement of the midterm. i tried to create 'recipes' with objects but since the recipes were just serieses of if statement it wasnt really working out. then while i was looking over my code and spcfially the dragging mechanism i had i realized the repitiveness of and i actually stumbled upon the idea of creating an object of 'ingredient'. this object would give any image the charactertics of being dragged around like my items from before. sadly, this wonderful dream of the perfect objects has been a bit harder to acheieve than i though. because i cant use the ```mouseDragged``` or any other functions i've been struggling to create a way to rewrite my code. i tried using the ```mouseIsPressed``` variable but i still havent cracked it yet. i think this will be the final big challenge of my code because if i can accomplish this object ill be easily able to add in more fruits as well as add screens for collecting the fruits and then i would create the series of for loops to make 'recipes'.
 
### reflection
overall, im very happy with how my game is coming along because i really didn't think i had it in me after my series of unfrotunate events on monday. i stil have a lot of work to do but i think i have a good enough of foundation of the game to keep me motivated so i can keep working hard and create a fun game! i also want to try and use my skills from the web development series ive been partictapating in to use html to create a nicer fullscreen version of the game.
