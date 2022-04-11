# documentation
### final circuit
https://user-images.githubusercontent.com/98390884/162731566-c79b8ddc-01c9-4cac-b20f-58e87e50fb77.mp4

![20220405_124314](https://user-images.githubusercontent.com/98390884/162731625-f3755bd0-4a08-4862-9797-1b2725fc0a3e.jpg)
### process
##### stage 1 : idea
for this assignment, i was a bit stuck wit the idea because i was not sure how to incorporate but the analog reader as well as the digital reader so i tried to go for a simple idea. i know of a lamp they sell at kiea which allows you to adjust the brightness of the light and i wante dto try and recreate this feauture all by myself. i wanted there to be a switch that must be turned on and then use the potentiometer to adjust the brightness.

##### stage 2 : creating a switch
i decided to work on this circuit in sections because i was a bit overwhelmed with the code and circuitry so i started first by creating a full circuit with the switch. i followed the same principles as the button in class and i also deicided to connect my leds with a series circuit. i thought this would work best as it would making controlling the brightness of both leds simpler kind of like how fairy lights work when you control them all together. after adding the circuits i wrote the code to make the switch function properly, following the example on github. i created the if statements that control the ```switchState``` to check if the switch was off or on. i also learned that the word ```switch``` seems to be a preestablished term so i renamed it accordingly.

##### stage 3 : adjusting brightness
after creating a working switch i added the potentiometer to seperate pins so it almost acts like a seperate circuit which only gathers input. i commented out all the code i had written thus far to work only on the potentiometer. i figured out how to adjust the dimness based on what we did in class and i was able to control both lightbulbs.

##### stage 4 : combining both controls
this was a very tricky stage for me because i had written seperate variables for both controls and i was unsure of which lines of code to delete. i also struggled a lot to figure out what i had done wrong because i find troubleshooting very hard for the arduino. in p5js i would always just type ```print("hello")``` or something to test each function and i really miss a feature like that for the arduino. one of the problems i had was that after adjusting the pins i had plugged in the led to a pin that wasnt pwm but it took an embarrasingly long time to figure out a simple mistake like that. eventually i got both of them to work in harmony and my circuit was complete

### final code
here is the final code i put in the arduino
```jsx
// constants
const int switchpin = 6;
const int led =  3;
int switchState = 0;
int value = 0;
const int dial = A1;

void setup() {
pinMode(led, OUTPUT);
Serial.begin(9600);
pinMode(switchpin, INPUT);
}

void loop() {
switchState = digitalRead(switchpin);
// switch on
if (switchState == HIGH) {
//control dimness
int  dialValue = analogRead(dial);
Serial.println(dialValue);
int ledValue = dialValue / 4;
analogWrite(led, ledValue);
//
} else {
// switch off led
digitalWrite(led, LOW);
}
}
```
### reflection
i feel like this was another simple project, similar to last week. although i still like it, i wish i was able to make something more creative but i really struggle to come up with ideas. i feel that thinking with circuits is a bit unfamiliar to me and i have to get used to it more because i often find that most of my ideas come visually to me. for example, in p5js i would always have a visual idea and then i would try to figure out a code that would help me achieve it. but unfortunately, i cant really imagine the possibilities of a circuit as well and not being able to visualize it means i usually have to find other sources of insiration aka my real practical life which definetely is not as fun as my ideas in p5js. i hope this will improve as i work more in circuits and i think the musical instrument assignment will be a good way to to explore interactive creativity in a new way for me.
