## EXP 5  SPEECH RECOGNITION USING SCILAB

### AIM: 

To perform and verify speech recognition using SCILAB. 

### APPARATUS REQUIRED: 
PC installed with SCILAB and Python IDE. 

## PROGRAM : 
PYTHON CODE
```Python
import speech_recognition as sr
r = sr.Recognizer()

try:
    with sr.AudioFile("harvard.wav") as source:
        audio = r.record(source)

    text = r.recognize_google(audio)
    print("Recognized:", text)

except Exception as e:
    print("Error:", e)
    text = "ERROR"

# Always create output file
with open("output.txt", "w") as f:
    f.write(text)
```
SCILAB CODE
```python
clc;
clear;
close;

cd("D:\SEMESTER 4\TERM 1\DTSP\SPEECH RECOGNITION\");

disp("Calling Python Speech Recognition...");

host("python speech_to_text.py");

// wait for python to finish
sleep(5000);

text = mgetl("output.txt");

disp("Recognized Speech:");
disp(text);

```
### AUDIO 
[harvard.wav](https://github.com/user-attachments/files/26216204/harvard.wav)

## OUTPUT: 
<img width="734" height="172" alt="image" src="https://github.com/user-attachments/assets/fcac0d79-a48a-400e-9b7e-ddbff745e6b1" />


## RESULT: 
Thus the speech recognition using SCILAB and Python IDE was performed and verified.
