# Ex06 BMI Calculator
## Reg NO: 212223220026
## Name: Gowshik S
## Date:

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
#APP.JSX
```
import React, { useState } from 'react';

export default function App() {
  const [weight, setWeight] = useState('');
  const [height, setHeight] = useState('');
  const [bmi, setBmi] = useState(null);
  const [message, setMessage] = useState('');
  const [unit, setUnit] = useState('cm'); // 'cm' or 'm'

  function calculateBMI(e) {
    e.preventDefault();
    const w = parseFloat(weight);
    let h = parseFloat(height);

    if (!w || !h || w <= 0 || h <= 0) {
      setMessage('Please enter valid positive numbers for weight and height.');
      setBmi(null);
      return;
    }

    // Convert height to meters if needed
    if (unit === 'cm') {
      h = h / 100;
    }

    const value = w / (h * h);
    const rounded = Math.round(value * 10) / 10;
    setBmi(rounded);
    setMessage(getCategory(rounded));
  }

  function getCategory(v) {
    if (v < 16) return 'Severe Thinness';
    if (v < 17) return 'Moderate Thinness';
    if (v < 18.5) return 'Mild Thinness';
    if (v < 25) return 'Normal';
    if (v < 30) return 'Overweight';
    if (v < 35) return 'Obese Class I';
    if (v < 40) return 'Obese Class II';
    return 'Obese Class III';
  }

  function colorForBmi(v) {
    if (v == null) return '#888';
    if (v < 18.5) return '#1976d2';
    if (v < 25) return '#2e7d32';
    if (v < 30) return '#f57c00';
    return '#d32f2f';
  }

  function resetForm() {
    setWeight('');
    setHeight('');
    setBmi(null);
    setMessage('');
    setUnit('cm');
  }

  return (
    <div className="app">
      <div className="card">
        <h1>BMI Calculator</h1>
        <form onSubmit={calculateBMI} className="form">
          <label>
            Weight (kg)
            <input
              type="number"
              step="0.1"
              min="0"
              value={weight}
              onChange={(e) => setWeight(e.target.value)}
              placeholder="e.g. 70"
            />
          </label>

          <label>
            Height ({unit})
            <div className="height-row">
              <input
                type="number"
                step="0.1"
                min="0"
                value={height}
                onChange={(e) => setHeight(e.target.value)}
                placeholder={unit === 'cm' ? 'e.g. 175' : 'e.g. 1.75'}
              />
              <select value={unit} onChange={(e) => setUnit(e.target.value)}>
                <option value="cm">cm</option>
                <option value="m">m</option>
              </select>
            </div>
          </label>

          <div className="buttons">
            <button type="submit" className="btn">Calculate</button>
            <button type="button" className="btn btn-secondary" onClick={resetForm}>Reset</button>
          </div>
        </form>

        <div className="result" style={{ borderColor: colorForBmi(bmi) }}>
          <h2>Result</h2>
          {bmi != null ? (
            <>
              <p className="bmi-number" style={{ color: colorForBmi(bmi) }}>{bmi}</p>
              <p className="bmi-category">{message}</p>
              <p className="bmi-tip">{tipForCategory(message)}</p>
            </>
          ) : (
            <p className="placeholder">Enter your details and press Calculate</p>
          )}
        </div>

        <div className="legend">
          <h3>Categories</h3>
          <ul>
            <li><span className="dot" style={{background:'#1976d2'}}></span>Underweight &lt; 18.5</li>
            <li><span className="dot" style={{background:'#2e7d32'}}></span>Normal 18.5 - 24.9</li>
            <li><span className="dot" style={{background:'#f57c00'}}></span>Overweight 25 - 29.9</li>
            <li><span className="dot" style={{background:'#d32f2f'}}></span>Obese &ge; 30</li>
          </ul>
        </div>
        <footer className="footer">Note: BMI is a rough estimate. Consult a healthcare professional for medical advice.</footer>
      </div>
    </div>
  );
}

function tipForCategory(cat) {
  switch (cat) {
    case 'Normal':
      return 'Great — maintain your healthy lifestyle!';
    case 'Overweight':
      return 'Consider balanced diet and regular exercise.';
    case 'Severe Thinness':
    case 'Moderate Thinness':
    case 'Mild Thinness':
      return 'Consider consulting a nutritionist for a healthy weight gain plan.';
    default:
      return 'If concerned, consult a healthcare professional.';
  }
}
```
# index.html
```
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>BMI Calculator By Gowshik S 212223220026</title>
</head>
<body>
  <div id="root"></div>
</body>
</html>
```


## OUTPUT
<img width="1902" height="912" alt="image" src="https://github.com/user-attachments/assets/6b95a3fd-49fd-4164-9b30-f4ab3740956e" />
<img width="1915" height="832" alt="image" src="https://github.com/user-attachments/assets/90bcf643-09c7-4c54-83d4-369a73c0dcef" />



## RESULT
The program for creating BMI Calculator using React Router is executed successfully.
