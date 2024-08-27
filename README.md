# Quizzler: A GUI-Based True/False Quiz Game

Quizzler is a fun and interactive true/false quiz game built using Python and the Tkinter library for the GUI. The quiz questions are fetched from the Open Trivia Database API, and the user's progress is tracked through an intuitive interface.

## Features

- **Dynamic Quiz Content:**
  - Questions are fetched from the Open Trivia Database API, ensuring a variety of questions every time the game is played.

- **Interactive GUI:**
  - The game features a simple, user-friendly interface built with Tkinter, making it easy to navigate through questions and see your score.

- **Score Tracking:**
  - The user's score is displayed in real-time, with feedback provided after each question to indicate whether the answer was correct.

## How It Works

### 1. Fetch Questions
The `data.py` file sends a request to the Open Trivia Database API to retrieve 10 true/false questions, which are then used in the quiz.

### 2. Question and Answer Handling
The `question_model.py` defines a `Question` class, which stores the question text and the correct answer. The `quiz_brain.py` file handles the logic of moving through the quiz, checking answers, and updating the score.

### 3. User Interface
The `ui.py` file contains the `QuizInterface` class, which manages the graphical user interface. It displays questions, handles user input, and provides feedback on whether the selected answer is correct.

### 4. Main Application
The `main.py` file ties everything together, creating the question bank, initializing the quiz logic, and launching the GUI.

## Code Overview

### `data.py`
This file handles fetching questions from the Open Trivia Database API.

```python
import requests

params = {
    'amount': 10,
    'type': 'boolean'
}

response = requests.get(url='https://opentdb.com/api.php', params=params)
response.raise_for_status()
data = response.json()

question_data = data['results']
