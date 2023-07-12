## Encryption and decryption of morse code using a flash light
**About this project:**

**Decoder components:**
For decoder, we need a photo resistor (LDR) and 1K ohm resistor to make voltage divider. The analog input A0 is used to read the voltage level.

**Photo resistor as Morse code sensor:**
A photo resistor is designed to read intensity of ambient light.
Decoder code can dynamically adjust its light level using adaptive logic. The code is designed to read maximum value, minimum value and cut-off value dynamically.
Caveat: This code cannot identify feeble light level differences.

**Timer Interrupt to read sensor:**
 I used timer interrupt to read sensor values at every 1ms interval recurrently, regardless of commands executed in loop.
This requires a buffer to store the signal, so that loop can consume the signal, when it is ready.

**Classes in Decoder program:**
I have used classes exhaustively during my project to improve maintenance of code and re-usability.
>•	AdaptiveLogicLevelProcessor is responsible for dynamically adjusting logic level.
>•	MorseCodeElementProcessor is responsible for detecting individual Morse code signal.
>•	MorseCodeProcessor is responsible for decoding Morse.
>•	MorseCodeBuffer is responsible for buffering Morse code so that interrupt routine can share the code to loop.

