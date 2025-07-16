# IOT-SECURITY-SYSTEM

**COMPANY:** CODTECH IT SOLUTIONS

**NAME:** I ROHITH KUMAR

**INTERN ID:** CT04DG1391

**DOMAIN:** INTERNET OF THINGS

**DURATION:** 4 WEEKS

**MENTOR:** NEELA SANTOSH

# DESCRIPTION
**WORKING:**
This Arduino-based security system operates through a clear sequence of events. Initially, the user interacts with a keypad connected to one Arduino to enter a secret passcode. This Arduino processes the input, comparing it to a stored correct code.

The result of this authentication (whether the code is correct or incorrect) is then transmitted to the second Arduino via I2C communication. This second Arduino, upon receiving the status, controls a 16x2 LCD display. If the code is valid, the LCD will display a "Welcome" message. Conversely, an "INVALID CREDENTIALS" message appears if the code is wrong. Simultaneously, a buzzer on the first Arduino provides audible feedback, likely sounding an alert for incorrect entries, reinforcing the visual cues on the LCD. This division of labor between the two Arduinos allows for modularity and efficient handling of different system functions.

**Components:**
This Arduino-based security system utilizes two **Arduino Uno boards** as its central controllers. User input is handled by a **keypad** for code entry, while a **16x2 LCD display** provides clear visual feedback on the system's status. An **audible buzzer** delivers alerts and confirmations, supplemented by an **LED** for visual indication. For prototyping and circuit flexibility, the components are wired together on **breadboards** using **jumper wires**. Additional elements like a **potentiometer** (for adjustments) and a **push button** (for auxiliary input) contribute to the system's interactive functionality.

**CODE:**
**#include <LiquidCrystal.h>**

**#include <Wire.h>**

**int z=0;**

**LiquidCrystal lcd(12, 11, 5, 4, 3, 2);**

**void receiveEvent(int howMany)**

 **{**
 
  **int x = Wire.read();**
  
  **z=x;**
  
 **}**

**void setup()**

 **{**
 
  **pinMode(10,OUTPUT);**
  
  **pinMode(9,OUTPUT);**
  
  **pinMode(8,OUTPUT);**
  
  **pinMode(7,OUTPUT);**
  
  **Wire.begin(4);**      
  
  **Wire.onReceive(receiveEvent);**
  
  **lcd.begin(16, 2);**
  
**}**

**void loop()**

 **{**
 
  **digitalWrite(9,HIGH);**
  
  **digitalWrite(8,HIGH);**
  
  **lcd.clear();**
  
  **while (z==50)**
  
   **{**
   
   **digitalWrite(9,LOW);**
    
   **digitalWrite(8,HIGH);**
   
   **lcd.setCursor(0, 0);**
    
   **lcd.print("WELCOME");**
    
   **lcd.setCursor(0, 1);**
    
   **lcd.print("HOME");**
        
  **delay(500);**

  **}**
  
  **while (z==60)**
  
   **{**
   
   **digitalWrite(9,HIGH);**
   
   **digitalWrite(8,LOW);**
    
   **lcd.setCursor(0, 0);**
    
   **lcd.print("INVALID");**
    
   **lcd.setCursor(0, 1);**
    
   **lcd.print("CREDENTIALS");**
    
   **delay(500);**
    
   **}**
   
 **}**
 
 # OVERVIEW OF CODE:
 The Arduino code manages a security system's display and communication. It initializes an LCD and sets up I2C communication to act as a slave device. A `receiveEvent` function captures data sent from another Arduino, storing it in a variable `x`. The main loop then uses `x` to determine the system's state: if `x` is 0, it displays "Welcome HOME"; otherwise, it shows "INVALID CREDENTIALS," effectively reflecting the authentication status received from the master device.

# CIRCUIT:
