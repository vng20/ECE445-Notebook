# Vincent's ECE445 Lab Notebook

Week 1 Feb 10 - 14 | General Research and Proposal Writing
=========================================================
We have gotten our project approved and will be working on the “Driver Fatigue System”  
This week I completed the soldering assignment and have gained new skills for this project  
We will also be attending our first TA meeting on Tuesday  
We met up with Maanas and disucessed everything from locker assignments to logistics  
Our proposal for the Driver Fatigue System is written up  
We have talked to Gregg of the Machine Shop for advice on our project  
Given an initial sketch of what we want the device to look like, it was deemed as viable  


Week 2 Feb 17 - 21 | Project Proposal Review + Inital Design Stage
===================================================================
This week we will be reviewing our project proposal with Instructors and TAs  
Overall, the project proposal review went well  
We did not have to make any changes other than adding a references/citations section for future resources/research that we will be doing  
We will also be starting our pcb design and making a list of all the parts that we need  
![image](https://github.com/user-attachments/assets/291930f4-accf-4d20-933c-cd622ed13f3c)



Week 3 Feb 24 - 28 | Inital Design Completed
================================================
This week we will be creating our initial PCB design and attending the PCB review session  
This is the initial schematic we created with each part that we intend on using  
![image](https://github.com/user-attachments/assets/4bf3857f-e0a9-475c-8549-b0684e168363)  
This is the initial pcb design we created with each part that we intend on using  
![image](https://github.com/user-attachments/assets/ac67e749-906b-42ea-b384-ae0386b26f5c)  
The PCB review session went great and no changes were made to our inital PCB design  
Some challenges that we had while building the schematic include:  
No native schematic block for most of our parts  
Had to import parts from many different websites  
For the parts with no schematics online, we had to find parts with similar layouts  
same pinholes, same size, etc  



Week 4 Mar 3 - 7 | Teamwork Evaluation + Design Document + Inital Subsystem Implementation
========================================================================
This week our first round of PCB orders, Teamwork Evaluation, and Design Document are due  
We will not be submitting a PCB order for this round due to the fact that we decided to make some small changes to the PCB  
So far, teamwork has been great and Teamwork Evaluation was submitted successfully  
Our Design Document is due this week, and we have documented our entire design process so far with plans for the future  
We have been continuing research for each subsystem in our device  
So far our BAC alcohol sensor subsystem has been set up on the breadboard for breadboard demos next week  
![image](https://github.com/user-attachments/assets/20775189-d6e7-4bfd-9275-6ccf1831d15e)  
By configuring GPIO 34 as an analog input and adjusting the resolution to 12 bits, we were able to read and convert raw ADC values into voltage  
The live readings confirmed stable and responsive sensor output, validating our connection and code setup  




Week 5 Mar 10 - 14 | Breadboard Demos
===================================================================
This week we will be having our breadboard demo and submitting 2nd PCB order  
Breadboard demo went well, and we successfully demonstrated a working MQ3 sensor and BAC conversion through an arduino  
We have been continually testing our parts up until this point and we discovered that the ESP32 that we borrowed from the ECE Lab Lockers is actually broken  
After setting up the ESP development environment and ensuring correct port connects, we were unable to flash a naive program onto the ESP  
This actually set us back quite some time because we did not realize an ESP from the ECE Lab would be defective  
![image](https://github.com/user-attachments/assets/6e4219d0-7ec4-429f-bf84-c30ef08136ac)  
![image](https://github.com/user-attachments/assets/9df8a3fd-18e2-48c7-9b1f-bf75bf71ef8f)  
However, after discovering that the ESP was broken, we immediately went to the Supply Center and got another ESP32  
We went ahead and met up with Gregg at the ECE Machine Shop again to confirm the timeline of our project  


Week 6 Mar 17 - 21 | Spring Break
=================================================
BREAK

Week 7 Mar 24 - 28 | Research and Building Software
==================================================================================
This week there is nothing due, continuation of research and building software  
After getting a working ESP we were able to start programming onto the board  
I was in charge of handling all the backend algorithm for EAR(Eye Aspect Ratio) MAR(Mouth Aspect Ratio) and Fatigue Score  
After some research I decided to use the Dlib library for handling facial landmarks  
For my initial testing, we decided to run the program locally on my laptop camera due to the fact that our OV2640 camera was not set up with the ESP yet
Everything was working fine and there was no hiccups  
The basic logic of this algorithm is that the facial landmarks such as different points in the eye are marked by the Dlib dataset  
The algorithm that we are using implements Elucidean Distances and calculates when the landmarks in the eyes are at a certain distance  
So whenever the eyes are closed, the landmarks that track the eyes will be close together in distance  
Once a certain calculated distance is met, the eye will be given a "closed" state also known as a blink
The mouth aspect ratio works the same way, but instead once a certain calculated distance is met, the mouth is in a "open" state or a yawn
![image](https://github.com/user-attachments/assets/4aee8be1-5f81-43e9-98e8-6d30ed247e6c)  
![image](https://github.com/user-attachments/assets/351cb76f-1329-4315-9412-6c12c5967923)  
![image](https://github.com/user-attachments/assets/eaefc7f3-26f3-4539-ab43-4dd61ccf1fcd)  


Week 8 Mar 31 - Apr 4 | 3rd Round PCB order
==================================================================================
This week we will be submitting our 3rd round PCB order  
After we submitted the PCB order, we realized that the usbc port had the wrong orientation  
This was a setback for us in terms of testing our PCB  
We were ultimately able to test all of our components seperately on the breadboard  
One major setback we realized from testing was the fact that our OV2640 camera module was actually incompatible with the ESP  
This OV2640 camera module was ultimately unusable in our system due to missing documentation and incomplete pin functionality  
Notably, it lacks an exposed XCLK (external clock) pin, which is required to drive the camera sensor with a 10–20 MHz clock signal from the ESP32  
![image](https://github.com/user-attachments/assets/65310033-fdbd-4324-bf12-bd80f2ac812c)  
As a result, we replaced it with a more standardized ESP32-CAM board that included proper XCLK routing and a proven working configuration  
Due to the fact that we will be using a completely different ESP32, we must also make changes to our PCB design  
![image](https://github.com/user-attachments/assets/093395bb-0ffb-4bb9-a4ba-db46021874c1)  
This schematic reflects the new PCB design we implemented  
Also note that the PCB design from the 3rd Round also had an ESP schematic block that had the incorrect size  
We were not able to insert the pins of the ESP through the pinholes on the PCB  
We made note of this for our final PCB order  


Week 9 Apr 7 - 11 |
==================================================================================
This week we will be submitting our final PCB order  
![image](https://github.com/user-attachments/assets/7b4684db-385d-49df-b066-2ac92760e329)  
This is our revised PCB design, created after addressing the limitations of our initial prototype  
In this version, we correctly positioned the micro-USB connector along the edge of the board to ensure full cable compatibility and structural alignment  
The layout was reworked for improved functionality and cleaner trace routing to support components like the MQ-3 sensor, OLED display, buzzer, and LED indicator  
This version also finalized mounting holes and better spacing to accommodate enclosure constraints and mechanical stability  
Overall, the design reflects a more production-ready and functional board that integrates all project subsystems reliably  



Week 10 Apr 14 - 18 |
==================================================================================
This week we will be turning in the Team Contract Assignment

Week 11 Apr 21 - 25 | MOCK DEMO
==================================================================================
This week we will be conducting the mock demo  
Currently we have finished the EAR Algorithm and connecting all the endpoints of our system  
Things left to do are:  
Fatigue Score System  
Soldering PCB after fully programmed and working device on breadboard    


Week 12 Apr 28 - May 2 | DEMO WEEK
==================================================================================
This week we are finalizing up our device for demo on Tuesday  
Some issues that we ran into were:  



Week 13 May 5 - 9 | FINAL WEEK WRAPPING UP
==================================================================================
In this week, we made finishing touches to our Final Presentation Slides.  
Successfully presented our project to Professor, TAs, and peers.  
Finishing up our Final Paper  
Turned in our Final Paper  
Checking out Lab with TA Maanas  
Attending the Awards Ceremony  
  
Final Entry before turning in LAB NOTEBOOK!!! WOOHOO!!!



