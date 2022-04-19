### done with bato

### task 1

##### p5 code:
https://editor.p5js.org/insiyam/sketches/aZKDbrgGR

##### arduino:

const int POT = A0;
const int PR = A1;

void setup() {
  Serial.begin(9600);

}

void loop() {

 // send information to p5
  int potValue = analogRead(POT);
  int prValue = analogRead(PR);
  Serial.print(potValue);
  Serial.print(",");
  Serial.println(prValue);

}
##### process
the arduino code is based off the one we did in class but we tried to simplify the code but for some reason the code would stop working if i deleted the photo resistor code from arduino. i think this is probably due to inconsitencies with the code we get from serial control but we couldn't figure out the problem so we just left it as it is. i also think there is a bit of a lag in sending information as the ellipse glitches sometimes but we couldn't figure out the problem.

### task 2

##### p5 code:

https://editor.p5js.org/batoxpr/sketches/iUUjxHgDT

##### arduino:

const int LED = 3;
void setup() {
  Serial.begin(9600);
  pinMode(LED, OUTPUT);
  while (Serial.available() <= 0) {
    Serial.println("hello"); // send a starting message
    delay(300); //wait 1/3 second
  }
}

void loop() {

  // read information from p5
  if (Serial.available() > 0) {
    int ledValue = Serial.read();
    if (ledValue == 0) {
      analogWrite(LED, ledValue);
    } else {
      analogWrite(LED,ledValue);
    }  
  }
  }

##### process
this example was also a simplification of the in-class work so we created a led circuit and then connected it to p5js where it is controlled by ```mouseisPressed```. we tried to advance this a bit more by creating a variable in p5js so that it would be a scale of dimness instead of just between two predertmined states but we were confusedon how to create a variable with ```serial.write``` and if we would need a series of if statements or for loops so we decided to make it simple instead.

### task 3
upload video
