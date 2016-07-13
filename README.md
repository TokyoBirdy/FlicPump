# Flic-Pump



## Overview

Use Flic, photon and peralstatic pump to water flower regardless of location and time. 

### Step 1: Material 

- Photon from [Particle](https://www.particle.io/)
- Flic button  
- Standard solderless breadboard
- Peralstatic pump(12v)
- Relay (5v)
- Transistor
- Adapter(5V) to charge photon
- Adapter(12v) to charge pump

### Step 2: Theory for setup

![Setup](/Users/ceciliahumlelu/Documents/Cecilia/FlicPump/Theory.jpg)

### Step 3: Set up Photon with transistor and relay

![Setup](/Users/ceciliahumlelu/Documents/Cecilia/FlicPump/setup_0.jpg)
![Setup](/Users/ceciliahumlelu/Documents/Cecilia/FlicPump/setup_1.jpg)
![Setup](/Users/ceciliahumlelu/Documents/Cecilia/FlicPump/setup_2.jpg)
![Setup](/Users/ceciliahumlelu/Documents/Cecilia/FlicPump/setup_3.jpg)


### Step 3: Flic setup

![Flic setup](/Users/ceciliahumlelu/Documents/Cecilia/FlicPump/flic setup.jpg)

PS:URL is photons cloud link with device id which could be found in particle website when logged in.



### Step 4: Code of course

Run rf_receiver.ino on Arduino, you should be able to see output. Mine looks like this

	    int transistorControl = D7;
        Timer timer(10000,stopMotor,true);
        int waterFlower(String command);
        void setup() {
          pinMode(transistorControl,OUTPUT);
          digitalWrite(transistorControl, LOW);
          //create a cloud function
          Particle.function("water",waterFlower);
        }
        
        void loop() {
        }
        
        void stopMotor() {
          digitalWrite(transistorControl,LOW);
        }
        
        
        int waterFlower(String command) {
          Serial.print("command is");
          Serial.print(command);
          if (command == "water") {
            digitalWrite(transistorControl, HIGH);
            timer.start();
            return 1;
          }
          else {
            digitalWrite(transistorControl, LOW);
            return -1;
          }
        }
	
	
### Step 5: Run

Charge both photon and pump with respective adapters. Click flic button, this is what you will see. 

![Flic complete](/Users/ceciliahumlelu/Documents/Cecilia/FlicPump/completion.png) 

### Youtube video

[Flic pump](https://youtu.be/6VNN5ZrYjX0)