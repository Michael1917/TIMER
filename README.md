# SKILL ASSESMENT - 2      - BY MICHAEL JUSTUS W
## AIM
To write an assembly language program in 8051 microcontroller to generate a 2-second delay using Timer 0 in Mode 1 and to blink an LED connected to Port 3.7 continuously.
## APPARATUS REQUIRED
- Personal Computer  
- Keil µVision Software

## ALGORITHAM
1. Start the program.
2. Set Timer 1 in Mode 1 (16-bit timer) using TMOD = #10H.
3. Make LED OFF initially using CLR P3.7.
4. Load R7 = 31 for delay count.
5. Start timer and wait till TF1 = 1 (timer overflows).
6. Stop timer and clear TF1 flag.
7. Repeat steps 5–6 until R7 becomes zero (to get 2 sec delay).
8. Toggle LED using CPL P3.7.
9. Go back and repeat the whole process (LED blinks continuously).
10. Stop.

   
## PROGRAM
```C
ORG 0000H
MAIN: MOV TMOD, #10H      
      CLR P3.7           
AGAIN: MOV R7, #31        
DELAY_LOOP: MOV TH1, #00H  
            SETB TR1      
WAIT:       JNB TF1, WAIT 
            CLR TR1       
            CLR TF1       
            DJNZ R7, DELAY_LOOP  
      CPL P3.7            
      SJMP AGAIN          
END
```
<img width="1919" height="1199" alt="Screenshot 2025-10-30 213143" src="https://github.com/user-attachments/assets/654f8f04-3f39-4eca-ab40-d705a351ed68" />

## OUTPUT
<img width="1919" height="1195" alt="Screenshot 2025-10-30 213818" src="https://github.com/user-attachments/assets/57c8a3a9-d7e9-433d-945a-530375af8de4" />


## RESULT


The LED connected to Port 3.7 of the 8051 microcontroller blinks continuously with a delay of approximately 2 seconds between each ON and OFF state, successfully demonstrating Timer 0 operation in Mode 1 for time delay generation.
