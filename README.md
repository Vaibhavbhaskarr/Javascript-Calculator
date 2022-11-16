# A simple calculator in Javascript

## A calculator with all the basic mathematical computation

1. index.html: -This file includes the html code for the program. and it links to "style.css" & "script.js".
2. style.css: -Includes the formating or styling for our program.
4. script.js: -Includes the functionality of the program.


## HTML

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculator</title>
    <link href="styles.css" rel="stylesheet">
    <script src="script.js" defer></script>
</head>
<body>
    <div class="calculator-grid">
        <div class="output">
            <div data-previous-operand class="previous-operand"></div>
            <div data-current-operand class="current-operand"></div>
        </div>
        <button class="span-two" data-all-clear> AC</button>
        <button data-del> DEL</button>
        <button data-operation> ÷</button>
        <button data-number> 1</button>
        <button data-number> 2</button>
        <button data-number> 3</button>
        <button data-operation> *</button>
        <button data-number> 4</button>
        <button data-number> 5</button>
        <button data-number> 6</button>
        <button data-operation> +</button>
        <button data-number> 7</button>
        <button data-number> 8</button>
        <button data-number> 9</button>
        <button data-operation> -</button>
        <button data-number> .</button>
        <button data-number> 0</button>
        <button class="span-two" data-equals> =</button>
    </div>
</body>
</html>
```
A simple HTML code to add all the necessary components for our calculator. We added all the buttons and also an output component. `class` or `data` is used where necessary, as this would make this easier to identify and call the components in our Javascript code.


## CSS 
Styled our HTML components into a simple calculator. 

```CSS
*, *::before,*::after {
    box-sizing: border-box;
    font-family: 'Franklin Gothic Medium', sans-serif;
    font-weight: normal;

}

body {
    padding: 0;
    margin: 0;
    background: linear-gradient(to right, #00AAFF, #00FF6C);

}
.calculator-grid {
    display: grid;
    justify-content: center;
    align-content: center;
    min-height: 100vh;
    grid-template-columns: repeat(4,100px);
    grid-template-rows: minmax(120px,auto)repeat(5,100px);

}

.calculator-grid > button {
    cursor: pointer;
    font-size: 2rem;
    border: 1px solid white;
    outline: none;
    background: rgba(red, green, blue, .75) ;
}
.calculator-grid > button:hover {
    background-color: rgba(255, 255, 255, .90);

}

.span-two {
    grid-column: span 2;
}

.output {
    grid-column: 1 / -1;
    background-color: rgba(0, 0, 0, .75);
    display: flex;
    align-items: flex-end;
    justify-content: space-around;
    flex-direction: column;
    padding: 10px;
    word-wrap: break-word;
    word-break: break-all;
}

.output .previous-operand {
    color: rgba(255, 255, 255, .70);
    font-size: 1.5rem;

}
.output .current-operand {
    color: white;
    font-size: 2.5rem;
    
}
```
In the CSS, it begins with using `begin::` and `after::` selector along with the `*` which selects all the elements. We select the box-sizing and the font-weight and font-family for all the elements in our program. In the `body` element, we set the background color of our calculator and set the padding and margin to 0. Then we style the rest of the buttons and our calculator grid, so get a simple and minimalist design for our calculator. 

## Javascript 
Next, we move on to add the functionalities to our buttons in Javascript. 

```Javascript 
const numberButtons = document.querySelectorAll('[data-number]')
const operationButtons = document.querySelectorAll('[data-operation]')
const equalsButtons = document.querySelector('[data-equals]')
const deleteButtons = document.querySelector('[data-del]')
const allclearButtons = document.querySelector('[data-all-clear]')
const previousoperandTextElement = document.querySelector('[data-previous-operand]')
const currentoperandTextElement = document.querySelector('[data-current-operand]')
```
First we will declare, the const type variables. The variable values are the `data` values that we added to our HTML components.

Then, 
```Javascript
class Calculator {
    constructor(previousoperandTextElement, currentoperandTextElement) {
        this.previousoperandTextElement = previousoperandTextElement
        this.currentoperandTextElement = currentoperandTextElement
        this.clear()
```
Then we create a class `Calculator`, The class has two initial properties: `previousoperandTextElement` and `currentoperandTextElement`. We also add a function `clear()` which will be created next, the clear function is added so that everytime the calculator is started, it starts with a clear output screen.



Now, we start to creat different functions necessary inside our Class `Calculator`

```Javascript
clear() { 
        this.currentoperand = ''
        this.previousoperand = ''
        this.operand = undefined
    }
```
First will be a simple clear(), fnunction, inside which we just add empty strings `''` to `currentoperand` and `previousoperand`. 


Then, we move on to our next function. 
```Javascript
delete () {
        this.currentoperand = this.currentoperand.toString().slice(0,-1)
    }
```
In this function, we use `slice` to remove one of the characters from our `currentoperand`.



After this, 
```Javascript
appendNumber (number) {
        if (number === '.' && this.currentoperand.includes('.')) return
        this.currentoperand = this.currentoperand.toString() + number.toString()
    }
```
We create the function `appendNumber` in which we use the `if` statement, to ensure that the decimal point `.` can only be used once in our `currentoperand`. After that we add add numbers to the `currentoperand` string.


In the next function:
```Javascript
chooseOperation(operation){ 
        if (this.currentoperand === '') return 
        if (this.previousoperand !== '') {
            this.compute()
        }
        this.operation = operation
        this.previousoperand = this.currentoperand
        this.currentoperand = ''
    }
 ```
 In this `choooseOperation` function, we use the `if` statement first to ensure that for any reason our `currentoperand` is empty then `return` and not do this function. Then we use the `if` statement again implying that, if our `previousoperand` operand is not empty, then we can use the function `compute()` which we haven't created as of now. 
 

The next function:
```Javascript
compute () {
        let computation 
        const prev = parseFloat(this.previousoperand)
        const current = parseFloat(this.currentoperand)
        if (isNaN(prev) || isNaN(current)) return
        switch (this.operation) {
            case '+':
                computation = prev + current
                break
            case '-':
                computation = prev - current
                break
            case '*':
                computation = prev * current
                break
            case '÷':
                computation = prev / current
                break
            default: 
                return
        }
    this.currentoperand = computation
    this.operation= undefined
    this.previousoperand = ''
 ```
 This function `compute` is the function where we compute the inputs of the user. In this the addition, subtraction, multiplication and division takes place. To start off we declare two variables `const prev` and `const current`, we assign the variables to  type parseFloat [The parseFloat function converts its first argument to a string, parses that string as a decimal number literal, then returns a number or NaN] and their value is the `previousoperand` and `currentoperand`. 
 Then we use the `if` statement to ensure that if the prev or current isNAN then we `return` and not continue further. 
