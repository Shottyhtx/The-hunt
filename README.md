<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Scavenger Hunt Puzzle</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      padding: 20px;
      background-color: #f7f7f7;
    }
    #puzzle-container {
      margin: 20px auto;
      max-width: 600px;
      background: #fff;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    }
    input[type="text"] {
      width: 80%;
      padding: 10px;
      margin: 10px 0;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
    button {
      background-color: #4CAF50;
      color: white;
      padding: 10px 15px;
      border: none;
      border-radius: 4px;
      cursor: pointer;
    }
    button:hover {
      background-color: #45a049;
    }
    #feedback {
      margin-top: 15px;
      font-size: 1.2em;
    }
  </style>
</head>
<body>
  <h1>Scavenger Hunt Puzzle</h1>
  <div id="puzzle-container">
    <p id="puzzle">Loading your puzzle...</p>
    <input type="text" id="answer" placeholder="Enter your answer">
    <button onclick="checkAnswer()">Submit</button>
    <p id="feedback"></p>
  </div>

  <script>
    // Define puzzles and answers
    const puzzles = {
      clue1: { question: "What has to be broken before you can use it?", answer: "egg" },
      clue2: { question: "I’m tall when I’m young, and I’m short when I’m old. What am I?", answer: "candle" },
      clue3: { question: "What month of the year has 28 days?", answer: "all" }
    };

    // Extract the puzzle key from the URL
    const urlParams = new URLSearchParams(window.location.search);
    const puzzleKey = urlParams.get('puzzle');

    // Display the puzzle or an error message
    const puzzleContainer = document.getElementById('puzzle');
    const feedbackContainer = document.getElementById('feedback');
    const currentPuzzle = puzzles[puzzleKey];

    if (currentPuzzle) {
      puzzleContainer.textContent = currentPuzzle.question;
    } else {
      puzzleContainer.textContent = "Invalid puzzle link!";
      document.querySelector('input').style.display = 'none';
      document.querySelector('button').style.display = 'none';
    }

    // Check the submitted answer
    function checkAnswer() {
      const userAnswer = document.getElementById('answer').value.trim().toLowerCase();
      if (userAnswer === currentPuzzle.answer) {
        feedbackContainer.textContent = "Correct! Proceed to the next clue.";
        feedbackContainer.style.color = "green";
      } else {
        feedbackContainer.textContent = "Incorrect answer. Try again!";
        feedbackContainer.style.color = "red";
      }
    }
  </script>
</body>
</html>
