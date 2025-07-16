# IOT-SECURITY-SYSTEM

**COMPANY:** CODTECH IT SOLUTIONS

**NAME:** I ROHITH KUMAR

**INTERN ID:** CT04DG1391

**DOMAIN:** INTERNET OF THINGS

**DURATION:** 4 WEEKS

**MENTOR:** NEELA SANTOSH

# DESCRIPTION

The system appears to be a dual-zone security setup, or perhaps a master-slave configuration, where one Arduino (top right) handles user input and initial authentication, and the other Arduino (bottom left) manages output displays and potentially other security functions.

**Components and Their Roles:**
Top Arduino Uno: This Arduino is connected to a keypad, a simple LED indicator, and what looks like a light sensor or a simple switch. It's likely responsible for:
Reading input from the keypad for password entry.Communicating with the second Arduino.Potentially triggering an alarm (the small speaker/buzzer at the top left is connected to this Arduino).

The breadboard connected to this Arduino also has a potentiometer, which could be for adjusting sensitivity or other parameters.

A simple button on the breadboard might be for resetting or a different input.

Keypad: This 4x4 matrix keypad is the primary input device for the user to enter a passcode.

Bottom Arduino Uno: This Arduino is connected to an LCD display and likely receives commands or authentication status from the top Arduino. It's responsible for:Displaying messages like "WELCOME," "INVALID," or "ACCESS GRANTED/DENIED" on the LCD.

Potentially controlling other output devices not explicitly shown but implied by a security system.

LCD Display: A 16x2 character LCD display, used to provide feedback to the user regarding the system's status, such as "WELCOME," "INVALID," or "ACCESS GRANTED."

Buzzer/Speaker: The small black component at the top left is a buzzer, which would likely be used to provide audible feedback or an alarm sound, possibly when an incorrect code is entered or an intrusion is detected.

Breadboards: Used for easy prototyping and connecting components without soldering.

Wiring: Color-coded wires connect the various components to the Arduino boards, establishing the electrical pathways for signals and power.

**CODE:**
**#include <LiquidCrystal.h>**

**#include <Wire.h>**

**int z=0;**

**LiquidCrystal lcd(12, 11, 5, 4, 3, 2);**

**void receiveEvent(int howMany)**
 {
  int x = Wire.read(); 
  z=x;
 }

void setup() 
 {
  pinMode(10,OUTPUT);
  pinMode(9,OUTPUT);
  pinMode(8,OUTPUT);
  pinMode(7,OUTPUT);
  Wire.begin(4);                
  Wire.onReceive(receiveEvent); 
  lcd.begin(16, 2);  
 }

void loop() 
 {
  digitalWrite(9,HIGH);
  digitalWrite(8,HIGH);
  lcd.clear();
  while (z==50)
   { 
    digitalWrite(9,LOW);
    digitalWrite(8,HIGH);
    lcd.setCursor(0, 0);
    lcd.print("WELCOME");
    lcd.setCursor(0, 1);
    lcd.print("HOME");
    delay(500);
   }
  while (z==60)
   { 
    digitalWrite(9,HIGH);
    digitalWrite(8,LOW);
    lcd.setCursor(0, 0);
    lcd.print("INVALID");
    lcd.setCursor(0, 1);
    lcd.print("CREDENTIALS");
    delay(500);
   }
 }
