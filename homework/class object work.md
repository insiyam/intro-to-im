# documentation #
for this assignment i wanted to create a scene inspired from nature and farms. i was deciding between bees or strawberries before settling on the latter.

i first started by creating a blue sky background and began working on making my strawberry. i created my shapes in the draw function. i used simple shapes like ellipses and traingles to create this drawing. i have (thankfully) learned from my classmates and i used the 

if (mouseIsPressed === true) {
    print(mouseX, mouseY);
    
code to create precise shapes. i then moved this into a new seperate drawStrawberry function and created a class. i then also converted all the points in my shapes to be variable based so all parts of the strawberries would be proportional. i aslo added a bush i=behind all my stawberries.

next i started working on the most challenging part of my idea: animating these strawberries. this part took the most trial and error as i kept trying different ideas including making a mousePressed function and many others. i created a new attribute in my class called 'size' and tried to create different functions.[at this point]<> i had already decidited of a starting size of 40 and final stage of 80 but i i was struggling to find a function that create smooth transition between them. then i remembered the first self portrait hw we did and that my friend bato had created a cool bubblegum animation where the ellipse smoothly increased. i looked to his code for inspiration and realized i could use the modulo function to make this smooth change. i applied this to the seed ellipses as well but despite trying i could not firgure out how to increase the triangles smoothly as they dont have a 'size' argument. although i had created this msooth transition i could not figured how to set extra paramters on the modulo to adjusting the starting size. i decided on a simple fix of overlaying a size 40 ellipse to give the illusion of a starting point
