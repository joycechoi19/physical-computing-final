# Final Project - Physical Computing and the Internet of Things

This is a template for your final project documentation.  Please replace <content like this> with your own.  For help with the syntax of Github markdown, visit: [Mastering Markdown](https://guides.github.com/features/mastering-markdown/)

*Name:*  Joyce Choi

*Date:* 12/12/2017

## Project:  Clothes Forecast

This is an analog clock representation of what to wear based on the weather outside. There are two clock handles that point towards outerwear and acessories based on precipitation, respectively. It also has a digital LCD display component that displays the temperature outside at the moment which is updated every 10 minutes based on information pulled online from a weather API.

### Detailed Project Description

< Explain the "what" of your project:   What is it?   What does it do?   Explain the "why" of your project:  What problem is it responding to?  What issue is it engaging?   
Clothes Forecast is an analog clock-like visualization of what to wear based on weather conditions outside. It has two clock needles, one that tells what clothes/outerwear to wear based on the windchill temperature (t-shirt weather, light jacket weather, heavy sweater weather, parka weather), and the other needle that points to the sunny (sunglasses), rainy (umbrella), or snow (snow boots) based on the precipitation outside. 

Each morning when I got up, the first thing that I would check on my phone used to be my weather app. However, this wasn't just checking the weather--it was getting pulled in my all of the notifications to my phone and so checking the weather was the first thing that chained me to technology from the start of the morning. The design of this clock was to remove me from mindless addiction of my phone from the start of my day, thus freeing up my morning. Having this analog-like clock interface to check the weather was a very different experience for me because I had always checked the weather through a digital interface either through an app or through the T.V. on the news. It had an analog, aesthetically pleasing interface but it also had a digital display that would let me know the temperature as well so I could associate the temperature with the suggestions the clock was giving.

Also, when I used to check my phone app for the weather, I would see a temperature like 47 degrees and would still not be completely sure what that meant in terms of translation into what I'm wearing. I would even go to my window to touch it to see what type of temperature the numbers I would be seeing would translate into. So this removes that step and is actually faster than me pulling out my phone to check the app as well since it's constantly running in the background and updating every ten minutes.

### Technical Description

Explain the "how" of your project.  What are the hardware components?  What are the software components?  How do they interact with each other?
For the hardware, I used a particle photon redboard, two servo motors, a SparkFun LCD display, two 3D printed clock handles, and a laser cut wooden frame. 
For the software, I wrote a particle webhook that pulls weather information from a weather API from weather.gov (the National Weather service). The firmware code is what ties together the hardware and software. Using the photon, I wrote arduino firmware code that updates the hardware components (moves the servo's to the correct positions and updates the temperature on the LCD display).

You can also explain the development process here
To laser cut the frame, I first designed the frame using Adobe Illustrator, and then used the laser cutter in the CoLab. I made many drafts of this design to make the design as aesthetically pleasing as possible and make the "clock" seem balanced since the number of items that I originally had to put on it was 7 items (just for the clothing/accessories items) but then when I thought of adding in the LCD display, there were 8 items so I was able to make a more balanced layout. For the 3D printed needles, I used the 3D printers in the CoLab as well. For the code, for servo control, I used some of my code from my midterm project because I had created a light switch using a servo. When first turned on, the needle's make a loop around the clock to show the ranges that they move in before pointing to the result based on the current weather. For the webhook, I wrote some code in C++ and created web interfaces using Javascript before settling on using the webhook integration through the particle console. For the firmware code, I processed the weather information from the weather API by looking at windchill temperature (which is more similar to how one would feel the temperature outside rather than the normal temperature) to determine the outerwear to indicate, and relative humidity and temperature to indicate the right accessory based on precipitation. 

#### Hardware Wiring Diagram

![Wiring Diagram](images/WiringDiagram.png)
< Insert Picture and explanation of Your Wiring Diagram here >


#### Code

< Explain your code.  You might include code snippets, either `inline` or
```c++
//Multiline
bool photon_fun = TRUE;
```
You should link to your full code, either included in the repository (e.g. [my_code.ino](code/my_code.ino)  or to the Shared Revision in your Particle IDE. >


### Design / Form

< Explain the device's form, the aesthetic choices made and how they relate to the concept/function the device is intended to engage >

< include photos of your device >

https://stackoverflow.com/questions/34341808/is-there-a-way-to-add-a-gif-to-a-markdown-file

### Evaluation / Reflection

< What is your own evaluation of your project?   What did you learn through this project?  What would you do differently in the future? >
