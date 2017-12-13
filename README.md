# Final Project - Physical Computing and the Internet of Things
*Name:*  Joyce Choi

*Date:* 12/12/2017

## Project:  Clothes Forecast
  This is an analog clock representation of what to wear based on the weather outside. There are two clock handles that point towards outerwear and acessories based on precipitation, respectively. It also has a digital LCD display component that displays the temperature outside at the moment which is updated every 10 minutes based on information pulled online from a weather API.

### Detailed Project Description
  Clothes Forecast is an analog clock-like visualization of what to wear based on weather conditions outside. It has two clock needles, one that tells what clothes/outerwear to wear based on the windchill temperature (t-shirt weather, light jacket weather, heavy sweater weather, parka weather), and the other needle that points to the sunny (sunglasses), rainy (umbrella), or snow (snow boots) based on the precipitation outside. 

  Each morning when I got up, the first thing that I would check on my phone used to be my weather app. However, this wasn't just checking the weather--it was getting pulled in my all of the notifications to my phone and so checking the weather was the first thing that chained me to technology from the start of the morning. The design of this clock was to remove me from mindless addiction of my phone from the start of my day, thus freeing up my morning. Having this analog-like clock interface to check the weather was a very different experience for me because I had always checked the weather through a digital interface either through an app or through the T.V. on the news. It had an analog, aesthetically pleasing interface but it also had a digital display that would let me know the temperature as well so I could associate the temperature with the suggestions the clock was giving.

  Also, when I used to check my phone app for the weather, I would see a temperature like 47 degrees and would still not be completely sure what that meant in terms of translation into what I'm wearing. I would even go to my window to touch it to see what type of temperature the numbers I would be seeing would translate into. So this removes that step and is actually faster than me pulling out my phone to check the app as well since it's constantly running in the background and updating every ten minutes.

### Technical Description
  For the hardware, I used a particle photon redboard, two servo motors, a SparkFun LCD display, two 3D printed clock handles, and a laser cut wooden frame. 
  
  For the software, I wrote a particle webhook that pulls weather information from a weather API from weather.gov (the National Weather service). The firmware code is what ties together the hardware and software. Using the photon, I wrote arduino firmware code that updates the hardware components (moves the servo's to the correct positions and updates the temperature on the LCD display).
  
  To laser cut the frame, I first designed the frame using Adobe Illustrator, and then used the laser cutter in the CoLab. I made many drafts of this design to make the design as aesthetically pleasing as possible and make the "clock" seem balanced since the number of items that I originally had to put on it was 7 items (just for the clothing/accessories items) but then when I thought of adding in the LCD display, there were 8 items so I was able to make a more balanced layout. For the 3D printed needles, I used the 3D printers in the CoLab as well. For the code, for servo control, I used some of my code from my midterm project because I had created a light switch using a servo. When first turned on, the needle's make a loop around the clock to show the ranges that they move in before pointing to the result based on the current weather. For the webhook, I wrote some code in C++ and created web interfaces using Javascript before settling on using the webhook integration through the particle console. For the firmware code, I processed the weather information from the weather API by looking at windchill temperature (which is more similar to how one would feel the temperature outside rather than the normal temperature) to determine the outerwear to indicate, and relative humidity and temperature to indicate the right accessory based on precipitation. 

#### Hardware Wiring Diagram

![Wiring Diagram](images/WiringDiagram.png)
< Insert Picture and explanation of Your Wiring Diagram here >


#### Code
```c++
//Multiline
bool photon_fun = TRUE;
```
Link to my code (shared revision in particle IDE): https://go.particle.io/shared_apps/5a2b11995977912c3700199d
Here are some significant lines from my code. 

This line was used to subscribe to the weather updates from the weather API through the webhook responses.
```c++
Particle.subscribe("hook-response/get_weather", gotWeatherData, MY_DEVICES);
```
This line of code was in the loop to trigger the webhook.
```c++
Particle.publish("get_weather");
```
To parse the json responses with the weather data information, I used this method that did string parsing and then I casted certain values into integers later to process:
```c++
tryExtractString
```
To control the servo's based on the appropriate values, I did:
```c++
myservo.write(90); //with the value being different based on the appropriate output
```

### Design / Form
  The device has an analog clock-like interface. It feels very natural to look at a clock the first thing in the morning after getting up so this fits that concept. Aesthetically, since there are 8 items along the rim, the symbols looked balanced. There are two needles on the clock, one for outerwear and one for accessories. I did two needles because this is similar to how analog clocks have two needles as well (one for the hour and one for the minutes). Although it is analog, there's one part that has a digital display which updates the temperature every 10 minutes as well as updates the needles on the clock. It's a nice blend of analog with the digital. It also creates less dependence on technology and getting chained by phone notifications from the start of the morning because now I don't have to check my phone for the weather to figure out what to wear; I can just use this clock that is always updated. 
  
  It also touches upon the concept of how people have little say over their actions now. They are very much governed or heavily influenced by suggestions given by technology so it is almost as if we are just biometric machines that just do what the technology suggests us to do. Which makes one question how much autonomy we have left and whether more technology/innovation is really as "freeing" in terms of mindspace and time as we used to think with technological innovations such as the washing machine.

![Outer_enclosure](outer_enclosure.jpg)

Video demo:
https://www.youtube.com/watch?v=RB5mpC5Y8H0&feature=share


### Evaluation / Reflection
I think learning to use the webhooks was the most interesting part of this project for me. Webhooks were much more flexible and could handle more personalization than the IFTTT and so it opened up a lot more opportunities to use the photon in different ways. I went through many tutorials while learning to use webhooks and wrote some interfaces for the webhook while learning through tutorials as well using JavaScript and c++ coding for the firmware. I think this will help me incorporate the photon into any software projects I work with in the future by hooking it up with an API. In the future, I would add in a second mini clock within the clock to give predictions on weather the next day. I would also change my code or use a different weather API to give a precipitation forecast of whether there is any predicted precipitation at all for the entire day instead of just at the moment. I also learned how to use the laser cutter and the 3D printer well through this project. Overall, I think this project was a good blend of hardware and software challenges and it's definitely given me ideas and inspiration for future IoT side projects. 
