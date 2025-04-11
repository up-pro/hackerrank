# Word Omitter
You are tasked with creating a simple React application called "Word Omitter" that dynamically filters out specific words from the user input in real-time. The application requirements are detailed below, and the finished application must pass all of the unit tests.

## Detailed Requirements
1. The WordOmitter component takes an array of words to mit as a prop called omitWords. Each element of this array is a string representing a word that should be filtered out of the user's input.
2. The application should display a text input field where the user can type a sentence.
3. As the user types, the output area below the input field should display the sentence with the specified words omitted.
4. The application should have a toggle button to switch between mitting the specified words and showing all words.
5. The application should have a clear button that clears both the input field and the output area.
6. If the input field is empty, the output area should also be empty.

## Sample Interaction
### Initial State
- The input field is empty.
- The output area is empty.
- The button displays "Show All Words" i,e. Omit Mode is enabled.

### User Action 1
- User types "This is a test sentence." in the input field.
- The output area displays "This is test sentence." (assuming "a" is omitted).

### User Action 2
- User clicks the toggle button
- The output area now displays "This is a test sentence." (showing all words).

### User Action 3
- User clicks the clear button.
- Both the input field and the output area are cleared.

## Solution
### src/components/wordOmitter.js
```
import React, { useState } from "react";

const OMITTED_WORDS = ["a", "the", "and", "or", "but"];

function WordOmitter() {
  const [inputText, setInputText] = useState("");
  const [omitWords, setOmitWords] = useState(true);

  const handleInputChange = (e) => {
    setInputText(e.target.value);
  };

  const toggleOmitWords = () => {
    setOmitWords(!omitWords);
  };

  const clearFields = () => {
    // TODO: Add your changes here
    setInputText("");
  };

  const getProcessedText = () => {
    // TODO: Add your changes here
    if (!inputText) return "";
    if (!omitWords) return inputText;

    const words = inputText.split(" ");
    const filtered = words.filter(
      (word) => !OMITTED_WORDS.includes(word.toLowerCase())
    );
    return filtered.join(" ");
  };

  return (
    <div className="omitter-wrapper">
      <textarea
        placeholder="Type here..."
        value={inputText}
        onChange={handleInputChange}
        data-testid="input-area"
      />
      <div>
        <button onClick={toggleOmitWords} data-testid="action-btn">
          {omitWords ? "Show All Words" : "Omit Words"}
        </button>
        <button onClick={clearFields} data-testid="clear-btn">
          Clear
        </button>
      </div>
      <div>
        <h2>Output:</h2>
        <p data-testid="output-text">{getProcessedText()}</p>
      </div>
    </div>
  );
}

export { WordOmitter };
```
### src/App.js
```
import { WordOmitter } from "./components/wordOmitter";

import "./App.css";

import "h8k-components";

function App() {
  return (
    <>
      <h8k-navbar header="Word Omitter"></h8k-navbar>
      <div className="App">
        <WordOmitter />
      </div>
    </>
  );
}

export default App;
```