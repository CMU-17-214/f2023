# Lab 9: Introduction to React.js

React is a declarative, efficient, and flexible JavaScript library for building interactive and dynamic user interfaces. It lets you compose complex UIs from small and isolated pieces of code called “components”.In this lab, students will learn the fundamentals of React.js and create an interactive quiz application.

## Deliverables
- [ ] Modify the implementation to retrieve questions and answer options from an external quizData file and correctly display them in the quiz interface.
- [ ] Enhance the user interface to indicate the selected answer, providing a more visually appealing user experience
- [ ] Extend the Quiz component to record user choices and display the total score of the selected options when the "Submit" button is pressed

## Instructions
Clone the Quiz App repository from: https://github.com/CMU-17-214/f23-rec09 and run

```
npm install
npm start
```
![Local Image](https://github.com/CMU-17-214/f23-rec09/blob/main/src/image/starterPic.png)

This will start the front-end server. You will be able to see a simple quiz GUI from the link http://localhost:3000/. You can update the front-end code as the server is running in the development mode (i.e., `npm start`). It will automatically recompile and reload.

In this starter code, you are provided with a Quiz class component.
The initial state includes a sample question, answer options, and a `selectedAnswer` value.
The `handleOptionSelect` function allows selecting an answer option and updates the `selectedAnswer` in the component's state.
The `render` method displays the question, answer options, and the selected answer.

### Display Quiz Questions 
In the starter code, you'll notice that the question and answer options are currently hardcoded within the Quiz component. To make the application more flexible, the first task is to modify the Quiz component to retrieve questions and answer options from an external `quizData` file. The file `quizData.js` is provided at [front-end/src/data/quizData.ts](https://github.com/CMU-17-214/f23-rec09/blob/main/src/data/quizData.ts), and your goal is to read and render questions and answer options from this file.

### Enhance User Experience
The starter code directly displays the user's current selection. Your task is to enhance the user experience by making is more visually appealing.  You have the creative freedom to improve the user interface.One way is to highlight the selected option. When a user clicks on an answer, it should be visually highlighted.

> Hint: You can consider using CSS to change the background color or apply a border to the selected option

### Manage User Interaction and Scoring
In the current implementation, the correctness of users' options are not stored and displayed when the "Submit" button is clicked. In this task, you will modify the Quiz component to store the value of each selected option and display total score of the selected options when the "Submit" button is pressed.
