# A simple calculator in Javascript

## A calculator with all the basic mathematical computations

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
