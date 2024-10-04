Here’s a structured README file for your React Quiz App:

---

# React Quiz App

## Overview

The **React Quiz App** is an interactive quiz platform designed to test your knowledge of React concepts. It dynamically loads questions from a local API and allows users to answer multiple-choice questions, track their progress, and view their final score with a custom feedback screen based on performance. The app also features a countdown timer for each quiz session and saves the user's high score.

## Features

- **Dynamic Quiz Loading**: Fetches questions from a local API at startup.
- **Multiple-Choice Questions**: Users select their answers from four options.
- **Progress Tracking**: Shows the user's current question and score.
- **Timer**: A countdown timer for the entire quiz session, ensuring the user completes the quiz within a limited time.
- **High Score**: Stores the highest score achieved by the user.
- **Interactive UI**: Provides visual feedback on correct/incorrect answers, and the final score is accompanied by an emoji-based performance indicator.
- **Restart Functionality**: Allows users to retake the quiz to improve their score.

## Getting Started

### Prerequisites

To run this app, you'll need:

- Node.js installed on your system
- Basic knowledge of React

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/react-quiz-app.git
   ```

2. Navigate to the project directory:

   ```bash
   cd react-quiz-app
   ```

3. Install the necessary dependencies:

   ```bash
   npm install
   ```

4. Start the development server:

   ```bash
   npm start
   ```

5. Ensure you have a local server running to provide the questions data. For testing purposes, you can use `json-server` to mock the API:

   ```bash
   npx json-server --watch data/questions.json --port 8000
   ```

### Folder Structure

The project structure is designed to ensure clarity and modularity. Below is an overview of the main files and their responsibilities:

```
├── public
│   ├── index.html
│   └── logo512.png
├── src
│   ├── components
│   │   ├── Error.jsx           # Displays an error message when data fetching fails
│   │   ├── FinishScreen.jsx    # Shows results and high score with a restart button
│   │   ├── Footer.jsx          # Footer component wrapping child elements (Timer, NextButton)
│   │   ├── Header.jsx          # Header component for app title
│   │   ├── Loader.jsx          # Loader component while fetching data
│   │   ├── Main.jsx            # Main component as the app's core container
│   │   ├── NextButton.jsx      # Button to move to the next question
│   │   ├── Options.jsx         # Renders answer options for a question
│   │   ├── Progress.jsx        # Tracks and displays user progress
│   │   ├── Questions.jsx       # Displays the current question and answer options
│   │   ├── StartScreen.jsx     # Initial screen with the quiz start button
│   │   ├── Timer.jsx           # Countdown timer for the quiz
│   ├── App.js                  # Main application logic, handling state and UI flow
│   ├── index.js                # Entry point for the React application
│   └── data
│       └── questions.json      # Sample questions for the quiz
```

### Components Breakdown

- **App.js**: The core logic of the app, where state management using `useReducer` controls quiz flow, handles data fetching, and dispatches actions based on user interaction and timer updates.
  
- **Error.jsx**: Renders an error message when there's a problem fetching questions from the API.

- **FinishScreen.jsx**: Displays the final score and high score, with an emoji that reflects user performance.

- **Footer.jsx**: Wraps the timer and navigation buttons, keeping them in the footer for consistent UI.

- **Header.jsx**: Shows the title of the quiz along with the React logo.

- **Loader.jsx**: Indicates that the app is loading data.

- **Main.jsx**: Acts as the container for the main content of the app, rendering children based on the current state.

- **NextButton.jsx**: Moves the user to the next question or finishes the quiz if it's the last question.

- **Options.jsx**: Displays the answer options for each question and provides feedback (correct or incorrect) after the user submits an answer.

- **Progress.jsx**: Tracks the user's current position in the quiz and displays the current score.

- **Questions.jsx**: Responsible for rendering the current question and options for the user.

- **StartScreen.jsx**: Initial screen that welcomes users and provides a start button to begin the quiz.

- **Timer.jsx**: A countdown timer that tracks the time left for the quiz session, updating every second.

## State Management

This project leverages `useReducer` to manage the app's state, providing a clean way to handle multiple pieces of state and complex transitions. The state consists of:

- **questions**: Array of questions loaded from the API.
- **status**: The current state of the app (`loading`, `ready`, `active`, `finished`, or `error`).
- **index**: The current question index.
- **answer**: Tracks the user's selected answer.
- **points**: User's score based on correct answers.
- **highscore**: Stores the highest score the user has achieved.
- **secondsRemaining**: Tracks time left for the quiz session.

The reducer handles actions such as `start`, `nextQuestion`, `newAnswer`, `finish`, `restart`, and more, each managing the relevant state transitions.

## Customization

- **Questions Database**: You can easily swap the questions by replacing or adding to the `questions.json` file located in the `data/` folder. Ensure that the structure follows the existing format for consistency.

- **Styling**: The app uses basic CSS for styling. To customize the UI, you can modify the styles in the `index.css` or add more styles as needed.
