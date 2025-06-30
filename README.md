# Voice Assistant using Python

This project is a guide to creating a basic but functional voice assistant using Python. The assistant can understand spoken commands and perform various tasks such as searching the web, telling the time, and sharing jokes. It utilizes core Python libraries for speech recognition and text-to-speech synthesis to create an interactive experience.

## Table of Contents
- [Project Summary](#project-summary)
- [Features](#features)
- [Required Libraries](#required-libraries)
- [Installation](#installation)
- [Project Workflow](#project-workflow)
  - [1. Initialization](#1-initialization)
  - [2. Greeting the User](#2-greeting-the-user)
  - [3. Taking Commands](#3-taking-commands)
  - [4. Processing Commands](#4-processing-commands)
- [How to Run the Assistant](#how-to-run-the-assistant)
- [Conclusion](#conclusion)

## Project Summary
This project walks through the development of a command-line voice assistant in Python. The assistant listens for user commands and responds by performing a variety of actions. It leverages the `SpeechRecognition` library to convert speech to text (or simulates it with text input for environments like Google Colab) and the `pyttsx3` library for text-to-speech (TTS) output, making the interaction feel conversational.

The assistant is structured with modular functions for speaking, greeting the user based on the time of day, and a main loop that continuously listens for commands. It is designed to handle specific keywords to trigger actions like searching Wikipedia, opening websites (YouTube, Google), telling the current time, or cracking a joke. The modular design makes it easy to extend and add new functionalities.

## Features
The voice assistant can perform the following tasks:
- **Greet the user** with a time-appropriate message (Good Morning, Good Afternoon, or Good Evening).
- **Search Wikipedia** for any query and read out a two-sentence summary.
- **Open websites** like YouTube and Google in a web browser.
- **Tell the current time**.
- **Tell a random programming joke**.
- **Exit** the program gracefully with a goodbye message.

## Required Libraries
The project depends on the following Python libraries:
- `SpeechRecognition`: For converting spoken words into text.
- `pyttsx3`: A text-to-speech conversion library.
- `wikipedia`: For easy access to the Wikipedia API.
- `pyjokes`: To get a collection of programming jokes.
- `webbrowser`: To open web pages.
- `os`: Used for system-level operations.
- `datetime`: To fetch the current date and time.

## Installation
To set up the project, you need to install the necessary libraries.

1.  **Ensure you have Python installed.**
2.  **Open your terminal or command prompt and run the following command:**
    ```bash
    pip install SpeechRecognition pyttsx3 wikipedia pyjokes
    ```
    *Note: `pyttsx3` might require additional system dependencies for speech synthesis on some operating systems.*

## Project Workflow
The assistant is built in a series of logical steps, each encapsulated in a function.

### 1. Initialization
- **Import Modules:** All required libraries are imported at the beginning.
- **Initialize Speech Engine:** A `speak()` function is created to handle the text-to-speech output. It initializes the `pyttsx3` engine, makes it say the provided text, and then waits for the speech to complete. This function also prints the assistant's response to the console.

### 2. Greeting the User
- A `wish_user()` function is defined to create a friendly and personalized interaction. It checks the current hour using the `datetime` module and greets the user with "Good Morning," "Good Afternoon," or "Good Evening" accordingly. After the greeting, it introduces itself.

### 3. Taking Commands
- The `take_command()` function is responsible for capturing user input.
- In a typical setup, this function would use `SpeechRecognition` to listen to the microphone and convert the audio to text.
- **For compatibility with environments like Google Colab** where microphone access is not supported, this function is simplified to take typed input from the user via the `input()` function. The input is converted to lowercase to ensure case-insensitive matching.

### 4. Processing Commands
- The core logic resides in the `run_assistant()` function.
- It starts by calling `wish_user()` to greet the user.
- It then enters an infinite `while True` loop to continuously listen for commands.
- Inside the loop, it calls `take_command()` to get the user's query.
- It uses a series of `if/elif/else` statements to check for keywords in the query:
  - If **'wikipedia'** is found, it searches Wikipedia for the rest of the query.
  - If **'open youtube'** or **'open google'** is found, it uses the `webbrowser` module to open the respective site.
  - If **'time'** is found, it gets the current time and speaks it.
  - If **'joke'** is found, it uses the `pyjokes` library to fetch and tell a joke.
  - If **'exit'** or **'bye'** is found, it says goodbye and `break`s the loop to terminate the program.
  - If no keywords are matched, it responds that it didn't understand.

## How to Run the Assistant
1.  Save the complete code as a Python file (e.g., `assistant.py`).
2.  Open your terminal or command prompt.
3.  Navigate to the directory where you saved the file.
4.  Run the script with the following command:
    ```bash
    python assistant.py
    ```
5.  The assistant will greet you and prompt you to type your command. Type a command and press Enter to interact with it.

## Conclusion
This project provides a solid foundation for building a personal voice assistant in Python. By combining powerful libraries for speech processing, web interaction, and API access, it's possible to create a useful and entertaining tool. The modular structure allows for easy expansion, so you can add new features like sending emails, getting weather updates, controlling smart home devices, and more.
