# Detection-of-Corona-Disease-by-Thermal-Screening-and-automatic-sanitizer-using-8051-Microcontroller

ABSTRACT
COVID – 19 is spreading at a great rate all over the world. The most common symptoms of corona disease include cough, cold, sore throat and mainly fever. Fever leads to increase in the body temperature. Some fevers do not include cough, cold and it becomes hard to detect the cause. It is been stated by the organizations, social distancing is the only way to minimize the spread of corona virus. To implement social distancing in the everyday life, we can make use of the 8051 microcontroller. 
Our model can be used to maintain social distancing. A temperature sensor reads the body temperature of the person. This is given as input to the 8051 microcontroller. Using the ASM code the normal body temperature is compared with the person’s body temperature. On detecting a normal temperature it glows the green LED and displays “YOU ARE SAFE” on 
the LCD. Otherwise in the case of an abnormal temperature, it will glow the RED LED, buzz the buzzer and display “PLEASE TEST FOR COVID” on the LCD screen.
The project will include the use of temperature sensor, LED, LCD and buzzer interfaced with 8051 microcontroller. The model will automatically pump some sanitizer into the hands of the person irrespective of the temperature,Obeying rules of social distancing, the project will be surely useful to detect COVID – 19 patients.

INTRODUCTION
COVID 19 is mainly a disease of fever and failure of internal organs. Our model is useful to decrease the spread of COVID 19 cases. The model is handy to use and can be fitted at any place. It uses a temperature sensor and has various alerting components such as LED, buzzer and LCD display. The 8051 Microcontroller is used to operate all the sensors and the output devices. The assembly code is responsible for the working of the microcontroller in the desired manner. At the end of the process after the message is displayed on the LCD screen, the model pumps sanitizer into the hands of the person, to insure the proper sanitization, The model is surely useful and can help the government, people around to detect the COVID infected people. The model would also protect other people from getting infected.

OVERVIEW
The model is completely automated, it measures the temperature and computes it with the normal body temperature. Then detects whether the person is infected by corona or not. Finding the corona infected person is a very tough task which our model would identify easily. The approach used for the model is assembly level coding, declaring the ports for the output components such as LED, BUZZER, LCD. As we know the body temperature available in proteus is LM35 which when interfaced with 8051 microcontroller needs ADC0808 and op amp 741. All the circuit components are connected in proteus. The assembly level code is written on keil software, through which a hex file is generated. This hex file is uploaded to the 8051 microcontroller in proteus.The motor for the barrier and the motor pump for the sanitizer is interfaced with the 8051 microcontroller.

![image](https://user-images.githubusercontent.com/43086002/137740376-5bc513c4-29e1-475a-b55c-5a851b165fac.png)

![image](https://user-images.githubusercontent.com/43086002/137740415-bcae7354-bb93-4a64-8b4e-5764e717380c.png)

As shown in the block diagram Port P0 of the 8051 microcontroller is connected to the ADC, P1 is connected to the LCD, P2 is connected to the Output LED, ALE, OE, SOC, EOC and port P3 is connected to the barricade and pump.

Input Devices
• The input from temperature sensor is the deciding factor of output devices.
• The VCC input is given to the 8051 Microcontroller.
• Assembly level coding will be used to run the simulation.
• All the simulations will be done on proteus and code will be written on Keil software (hex 
file uploaded to 8051 microcontroller).
• Motor will be used instead of a pump in proteus(As pump not available in proteus).

Output Devices

![image](https://user-images.githubusercontent.com/43086002/137740524-4ae367e8-20cf-4b8c-9b32-d80febd987c3.png)

![image](https://user-images.githubusercontent.com/43086002/137740557-730669c3-c459-4176-abec-0adc489168b9.png)

COMPONENTS USED
• 8051 Microcontroller
• LCD display LM016L 16X2
• LED
• Buzzer 
• Op Amp 741 
• ADC 0808
• Resistors
• Clock
• Motor
• Moto pump

FLOWCHART

![image](https://user-images.githubusercontent.com/43086002/137740833-e108dbb3-336b-4c02-9ef9-3618777f803c.png)

WORKING OF THE MODEL

To detect the temperature of the human, a temperature sensor is attached. MAX30205 is a human body temperature sensor.MAX30205 digital thermometer temperature sensor is accurate to 0.1°C over the measurement range of 37°C to 39°C and the resolution is 16 bits (0.00390625 °C). Thus an accurate reading of the temperature of the person is obtained. The output of MAX30205 is given as an input to the 8051 Microcontroller. The assembly code in the microcontroller is designed to compare the normal body temperature with the output of MAX30205. If the body temperature exceeds the normal body temperature, the LED displays “Test For COVID” and the motor of the barrier turn clockwise by 90 degree. The motor is brought back to normal position after 15 seconds. When the body temperature does not exceed the normal body temperature, the motor remains stationary and the LED displays “You are SAFE”. The project would not only detect the temperature of the person but also restrict the person from entering if the temperature detected is HIGH. A LED and Buzzer is also placed for visual and sound warnings about the temperature of the person. As prescribed by World Health Organization, any physical contact will lead to increase in the 
number of corona virus cases. The next step to decrease the number of cases would be converting our model contactless.As an advancement, the model could be developed as a product with the xcluma LX90614 Contactless Temperature Sensor. This sensor will convert the model completely contactless, hence obeying the rules of social distancing The model is designed in such a way that itself decides whether the person is fit to enter the place.At the end of every temperature detection the model sprays a bit of sanitizer into the hands of the person, irrespective of the temperature.

CODE WITH COMMENTS  
;*********************************************************************
;TOTAL : TEMPERATURE ALARM FOR COVID 19 SITUATION USING LM35
;**********************************************************************
; P0.0 = ADC D0
; P0.1 = ADC D1
; P0.2 = ADC D2
; P0.3 = ADC D3
; P0.4 = ADC D4
; P0.5 = ADC D5
; P0.6 = ADC D6
; P0.7 = ADC D7
;
; P1.0 = LCD D0
; P1.1 = LCD D1
; P1.2 = LCD D2
; P1.3 = LCD D3
; P1.4 = LCD D4
; P1.5 = LCD D5
; P1.6 = LCD D6
; P1.7 = LCD D7
;
; P2.0 = ADC A
; P2.1 = ADC B
; P2.2 = ADC C
; P2.3 = OUTPUT LED
; P2.4 = ALE
; P2.5 = OE
; P2.6 = SOC
; P2.7 = EOC
;
; P3.0 = 
; P3.1 = 
; P3.2 = LCD RS
; P3.3 = LCD R/W
; P3.4 = LCD E
; P3.5 =
; P3.6 = SANITIZER
; P3.7 = BARRIGATE
;
; 53H = TEMPERATURE SET POINT
;Program starts here
 ORG 0000H ;START
LCALL INIALIZE_SYSTEM
REPEAT: LCALL ADC_INTERFACING
 LCALL TEMP_DISPLAY
 LCALL TAKE_ACTION
 SJMP REPEAT
;--------------------------------------------------------------------------
;--------------------------------------------------------------------------
INIALIZE_SYSTEM:
CLR P2.3 ;LED OFF
CLR P3.6 ;SANITIZER OFF
CLR P3.7 ;BARRIGATE CLOSED
 MOV A,#38H ;INITIALIZE LCD 38 - 16 x 2 LCD and 8 bit mode (byte mode)
LCALL COMMAND
MOV A,#0EH ;0E - Screen on cursor ON
LCALL COMMAND
MOV A,#06H ;06 - Shift cursor Right
LCALL COMMAND
MOV A,#01H ;01 - clear LCD
LCALL COMMAND
 MOV 53H,#37H ;SET TEMP SETPOINT
 MOV 73H,#00H ;
 MOV A,#082H ;INITIALIZE LCD 80H - select 1st line - 82 1st line 
3rd location
LCALL COMMAND
MOV A,#'T'
LCALL DISPLAY
MOV A,#'E'
LCALL DISPLAY
MOV A,#'M'
LCALL DISPLAY
MOV A,#'P'
LCALL DISPLAY
MOV A,#' '
LCALL DISPLAY
MOV A,#'='
LCALL DISPLAY
MOV A,#' '
LCALL DISPLAY
CLR P2.0 ;SELECT ADC CHANNEL 0
CLR P2.1
CLR P2.2
RET
;--------------------------------------------------------------------------
ADC_INTERFACING:
 LCALL SEND_SOC
 LCALL CHECK_EOC
 LCALL READ_OUTPUT_OF_ADC
 LCALL HEX2BCD
 MOV 73H,A
 RET
;--------------------------------------------------------------------------
SEND_SOC:
 SETB P2.4 ;soc = 1
 SETB P2.6 ;ale = 1
 LCALL DELAY ;DELAY
 CLR P2.4 ;SOC =0
CLR P2.6 ;ALE = 0
RET
;--------------------------------------------------------------------------
CHECK_EOC:
 JB P2.7,RETURN ;JUMP IF EOC = 1
 SJMP CHECK_EOC
RETURN: RET 
;--------------------------------------------------------------------------
READ_OUTPUT_OF_ADC:
 MOV A,P0
 RET 
;--------------------------------------------------------------------------
HEX2BCD:
 MOV 40H,A ;SAVE THE HEX TEMPERATURE AT 40H LOCATION
 CJNE A,#1DH,CHECK_30H
 MOV A,#29H
 SJMP RETURN_RE
CHECK_30H:
 CJNE A,#1EH,CHECK_31H
 MOV A,#30H
 SJMP RETURN_RE
CHECK_31H:
 CJNE A,#1FH,CHECK_32H
 MOV A,#31H
 SJMP RETURN_RE
CHECK_32H:
 CJNE A,#20H,CHECK_33H
 MOV A,#32H
 SJMP RETURN_RE
CHECK_33H:
 CJNE A,#21H,CHECK_34H
 MOV A,#33H
 SJMP RETURN_RE
CHECK_34H:
 CJNE A,#22H,CHECK_35H
 MOV A,#34H
 SJMP RETURN_RE
CHECK_35H:
 ANL A,#0F0H ;LOWER NIBBLE IS MASKED
 SWAP A ;SWAP THE NOBBLE
 MOV R3,A ;R3 IS COUNTER
 CLR A ;A = 00H
UP123: ADD A,#16H ;ADD 16 IN A
 DA A ;CONVERT IT INTO BCD
 DJNZ R3,UP123 ;DO ADDITION UNTILL R3 = 0 
 MOV R3,A ;SAVE THE RESULT OF MULTIPLICATION INTO R3
 MOV A,40H ;TAKE THE NUMBER FROM 40H INTO A
 ANL A,#0FH ;MASK THE MSB
 ADD A,R3 ;DO ADDITION OF R3 AND LSB
 DA A ;CONVERT IT INTO BCD
RETURN_RE:
 MOV 40H,A ;SAVE THE BCD TEMPERATURE AT 40H LOCATION
 RET
;--------------------------------------------------------------------------
BCD2ASCII: ;Converting from BCD to ASCII
MOV R3,A
 ANL A,#0F0H
 SWAP A
 LCALL CONVERT_IT
 MOV R4,A
 MOV A,R3
 ANL A,#0FH
 LCALL CONVERT_IT
 MOV R3,A
 RET
;--------------------------------------------------------------------------
CONVERT_IT:ORL A,#30H
 RET
;--------------------------------------------------------------------------
TEMP_DISPLAY: MOV A,#089H ;STARTING ADDRESS OF LINE 1 OF LCD RAM
 ACALL COMMAND
 MOV A,73H
 LCALL BCD2ASCII
 MOV A,R4
 LCALL DISPLAY
 MOV A,R3
 LCALL DISPLAY
 MOV A,#0DFH
 LCALL DISPLAY
 MOV A,#'C'
 LCALL DISPLAY
 MOV A,#'.'
 LCALL DISPLAY
 RET
;-----------------------------------------------------------------------------
TAKE_ACTION:
 MOV A,73H
 CJNE A,53H,NEXT_LOWER
T_HIGH: SETB P2.3
SETB P3.6 ;SANITIZER ON
LCALL DISPLAY_DO_TEST
LCALL DELAY
LCALL DELAY
LCALL DELAY
LCALL DELAY
LCALL DELAY
CLR P3.6 ;SANITIZER OFF
RET
NEXT_LOWER:
JNC T_HIGH
 CLR P2.3
SETB P3.6 ;SANITIZER ON
SETB P3.7 ;BARRIGATE OPEN
LCALL DISPLAY_NORMAL
LCALL DELAY
LCALL DELAY
LCALL DELAY
LCALL DELAY
CLR P3.6 ;SANITIZER OFF
LCALL DELAY
LCALL DELAY
LCALL DELAY
LCALL DELAY
CLR P3.7 ;BARRIGATE CLOSED
RET
;--------------------------------------------------------------------------
DISPLAY_DO_TEST:
MOV A,#0C0H ;INITIALIZE LCD C0H - select 2ND line - "TEST 
FOR COVID19"
LCALL COMMAND
MOV A,#'T'
LCALL DISPLAY
MOV A,#'E'
LCALL DISPLAY
MOV A,#'S'
LCALL DISPLAY
MOV A,#'T'
LCALL DISPLAY
MOV A,#' '
LCALL DISPLAY
MOV A,#'F'
LCALL DISPLAY
MOV A,#'O'
LCALL DISPLAY
MOV A,#'R'
LCALL DISPLAY
MOV A,#20H
LCALL DISPLAY
MOV A,#'C'
LCALL DISPLAY
MOV A,#'0'
LCALL DISPLAY
MOV A,#'V'
LCALL DISPLAY
MOV A,#'I'
LCALL DISPLAY
MOV A,#'D'
LCALL DISPLAY
MOV A,#'1'
LCALL DISPLAY
MOV A,#'9'
LCALL DISPLAY
RET
;--------------------------------------------------------------------------
DISPLAY_NORMAL:
MOV A,#0C0H ;INITIALIZE LCD C0H - select 2ND line - " 
"YOU ARE SAFE ""
LCALL COMMAND
MOV A,#20H
LCALL DISPLAY
MOV A,#'"'
LCALL DISPLAY
MOV A,#'Y'
LCALL DISPLAY
MOV A,#'O'
LCALL DISPLAY
MOV A,#'U'
LCALL DISPLAY
MOV A,#' '
LCALL DISPLAY
MOV A,#'A'
LCALL DISPLAY
MOV A,#'R'
LCALL DISPLAY
MOV A,#'E'
LCALL DISPLAY
MOV A,#' '
LCALL DISPLAY
MOV A,#'S'
LCALL DISPLAY
MOV A,#'A'
LCALL DISPLAY
MOV A,#'F'
LCALL DISPLAY
MOV A,#'E'
LCALL DISPLAY
MOV A,#'"'
LCALL DISPLAY
MOV A,#' '
LCALL DISPLAY
RET
;--------------------------------------------------------------------------
 DELAY: MOV R7,#0FFH ;Delay loop
 LOOP1: MOV R6,#0FFH
 LOOP: DJNZ R6,LOOP
 DJNZ R7,LOOP1
 RET
;-----------------------------------------------------------------------------
;LCD Strobe Command
 COMMAND: ACALL DELAY
 MOV P1,A ;Command Character in Port P1
 CLR P3.2 ;Command resister chosen
 CLR P3.3 ; write enable
 SETB P3.4 ; Strobe Character to display
 CLR P3.4
 RET ;Return
;-----------------------------------------------------------------------------
 DISPLAY: ACALL DELAY
 MOV P1,A ;Take data to be displayed
 SETB P3.2 ;RS=P3.2= 1 to select data register
 CLR P3.3 ;Write enable
 SETB P3.4 ;Strobe character to be displayed
 CLR P3.4
 RET ;Return
;-----------------------------------------------------------------------------
END

ADVANTAGES
• Detects people affected from corona virus
• Reduces labor by converting the temperature sensor contactless, the model can be fitted at 
any place.
• Prevents Spreading of Corona virus
• Helps people to stay safe and spreads awareness.
• Sanitizes the person without contact.

RESULTS (SNAPSHOTS)

![image](https://user-images.githubusercontent.com/43086002/137741270-fe83e470-14b2-4c50-940b-19dafc245bde.png)

Red LED: Body temperature is greater than threshold temperature (37°C )
Green LED: Body temperature is less than or equal to threshold temperature(37°C)
Blue LED: Barricade 
Yellow LED: Sanitizer


![image](https://user-images.githubusercontent.com/43086002/137741335-421212be-733f-49fb-8ba9-b9c7e1b43ce0.png)

![image](https://user-images.githubusercontent.com/43086002/137741373-1f1b717f-e440-4a0c-b34f-2f4a2b411fee.png)

![image](https://user-images.githubusercontent.com/43086002/137741403-8e2d3a2a-21a3-4b9b-8f3a-c11ad0d6bb66.png)

LCD screen displays the temperature and “YOU ARE SAFE”
Green LED glows
Barricade rotates by 90 degree
Sanitizer sprays liquid into the person.

![image](https://user-images.githubusercontent.com/43086002/137741468-29745c66-b1a6-484f-929c-3cc3cbcb5846.png)

LCD screen displays the temperature and TEST FOR COVID19
Red LED glows
Barricade doesn’t rotate
Sanitizer sprays liquid into the person.

CONCLUSION
This model is useful to detect corona patients. The model will not only detect the patients but also would alert the nearby people about the detection. It also sprays sanitizer on the hands of the person irrespective if the person is infected or not. Hence, sanitizing the patient. The model will reduce the number of cases and prevent corona virus from spreading. Assembly code is used to program the 8051 microcontroller. An OP AMP and ADC is used to interface the IR sensor and the 8051 microcontroller. All the project output screenshots have been attached.

