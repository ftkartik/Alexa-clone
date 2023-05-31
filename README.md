Readme for Voice Assistant
This is a simple voice assistant script written in Python that uses various libraries to perform tasks such as speech recognition, text-to-speech conversion, and interacting with Google services. The assistant can recognize voice commands and perform actions like playing songs on YouTube and providing the current time.

Installation
Make sure you have Python installed on your system (version 3.6 or higher).
Install the required libraries by running the following command:
Copy code
pip install speech_recognition pyttsx3 pywhatkit
Download or clone the script file voice_assistant.py to your local machine.
Usage
To use the voice assistant, follow these steps:

Import the required libraries:
python
Copy code
import speech_recognition as sr
import pyttsx3
import pywhatkit
import datetime
Create an instance of the speech recognizer and text-to-speech engine:
python
Copy code
listener = sr.Recognizer()
engine = pyttsx3.init()
voices = engine.getProperty('voices')
engine.setProperty('voice', voices[1].id)
Define the talk() function to convert text to speech:
python
Copy code
def talk(text):
    engine.say(text)
    engine.runAndWait()
Implement the take_command() function to listen for voice commands and convert them to text:
python
Copy code
def take_command():
    try:
        with sr.Microphone() as source:
            print('Listening...')
            voice = listener.listen(source)
            command = listener.recognize_google(voice)
            command = command.lower()
            if 'google' in command:
                command = command.replace('google', '')
                print(command)
    except:
        pass
    return command
Define the run_google() function to process the voice commands and perform actions:
python
Copy code
def run_google():
    command = take_command()
    if 'play' in command:
        song = command.replace('play', '')
        talk('Playing ' + song)
        pywhatkit.playonyt(song)
    elif 'time' in command:
        current_time = datetime.datetime.now().strftime('%H:%M')
        talk('The current time is ' + current_time)
Finally, call the run_google() function to start the voice assistant:
python
Copy code
run_google()
Example Usage
When you run the script and the assistant is listening, you can say commands like:

"Play [song name]" to play a song on YouTube.
"What's the time?" to get the current time.
The assistant will respond to your commands using text-to-speech.

Note: The script currently uses the default system microphone and voice. If you want to change these settings, refer to the documentation of the speech_recognition and pyttsx3 libraries.

Feel free to modify the code to add more functionality or customize it according to your needs.

Enjoy using the voice assistant!
