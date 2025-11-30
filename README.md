# Ex06 BMI Calculator

## AIM
To create a BMI calculator using React Router 

## ALGORITHM
### STEP 1 State Initialization
Manage the current page (Home or Calculator) using React Router.

### STEP 2 User Input
Accept weight and height inputs from the user.

### STEP 3 BMI Calculation
Calculate the BMI based on user input.

### STEP 4 Categorization
Classify the BMI result into categories (Underweight, Normal weight, Overweight, Obesity).

### STEP 5 Navigation
Navigate between pages using React Router.

## PROGRAM

App.jsx

```

import { useState } from 'react'
import reactLogo from './assets/react.svg'
import viteLogo from '/vite.svg'
import { BrowserRouter as Router, Routes, Route, Link } from "react-router-dom";
import "./App.css";

function Home() {
  return (
    <div className="page">
      <h2>Welcome to the BMI Calculator 💫</h2>
      <p>
        Use this tool to calculate your Body Mass Index (BMI) and understand your health status.
      </p>
      <Link to="/calculator" className="btn">Go to Calculator</Link>
    </div>
  );
}

function BMICalculator() {
  const [weight, setWeight] = useState("");
  const [height, setHeight] = useState("");
  const [bmi, setBmi] = useState(null);
  const [category, setCategory] = useState("");

  const calculateBMI = () => {
    if (weight && height) {
      const h = height / 100;
      const bmiValue = (weight / (h * h)).toFixed(2);
      setBmi(bmiValue);

      if (bmiValue < 18.5) setCategory("Underweight");
      else if (bmiValue < 25) setCategory("Normal weight");
      else if (bmiValue < 30) setCategory("Overweight");
      else setCategory("Obese");
    }
  };

  return (
    <div className="page">
      <h2>BMI Calculator</h2>
      <div className="form">
        <input
          type="number"
          placeholder="Enter weight (kg)"
          value={weight}
          onChange={(e) => setWeight(e.target.value)}
        />
        <input
          type="number"
          placeholder="Enter height (cm)"
          value={height}
          onChange={(e) => setHeight(e.target.value)}
        />
        <button onClick={calculateBMI}>Calculate</button>
      </div>

      {bmi && (
        <div className="result">
          <h3>Your BMI: {bmi}</h3>
          <p>Category: {category}</p>
        </div>
      )}

      <Link to="/" className="btn back">Back to Home</Link>
    </div>
  );
}

function App() {
  return (
    <Router>
      <div className="app-container">
        <nav className="navbar">
          <h1>BMI Calculator</h1>
          <div>
            <Link to="/">Home</Link>
            <Link to="/calculator">Calculator</Link>
          </div>
        </nav>

        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/calculator" element={<BMICalculator />} />
        </Routes>
      </div>
    </Router>
  );
}

export default App;

```
App.css

```
body {
  font-family: "Poppins", sans-serif;
  background: linear-gradient(to bottom right, #a855f7, #ec4899);
  color: white;
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}

.app-container {
  text-align: center;
  width: 100%;
}

.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(8px);
  color: white;
  padding: 15px 40px;
  border-radius: 12px;
  margin: 20px auto;
  width: 80%;
}

.navbar a {
  color: #ffe4f2;
  margin-left: 15px;
  text-decoration: none;
  font-weight: bold;
  transition: color 0.3s ease;
}

.navbar a:hover {
  color: #fff;
  text-decoration: underline;
}

.page {
  margin-top: 40px;
  text-align: center;
}

.form {
  display: flex;
  flex-direction: column;
  gap: 15px;
  width: 300px;
  margin: 20px auto;
}

input {
  padding: 10px;
  border-radius: 8px;
  border: none;
  text-align: center;
  outline: none;
  font-size: 1em;
}

button {
  padding: 10px;
  border: none;
  background-color: #9333ea;
  color: white;
  border-radius: 8px;
  cursor: pointer;
  font-weight: bold;
  transition: background 0.3s;
}

button:hover {
  background-color: #a855f7;
}

.result {
  margin-top: 20px;
  background: rgba(255, 255, 255, 0.15);
  padding: 15px;
  border-radius: 10px;
  width: 300px;
  margin-left: auto;
  margin-right: auto;
  box-shadow: 0 0 15px rgba(255, 255, 255, 0.2);
}

.btn {
  background-color: #ec4899;
  color: white;
  padding: 10px 15px;
  border-radius: 8px;
  text-decoration: none;
  display: inline-block;
  margin-top: 20px;
  transition: background 0.3s;
}

.btn:hover {
  background-color: #db2777;
}

.back {
  background-color: #9333ea;
}

.back:hover {
  background-color: #7e22ce;
}


```


## OUTPUT



<img width="819" height="436" alt="image" src="https://github.com/user-attachments/assets/4e9d204a-d814-4c5f-9a33-b6dfabdcffd8" />


## RESULT
The program for creating BMI Calculator using React Router is executed successfully.
