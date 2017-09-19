# x-tic-tac-toe

Tic Tac Toe exercise.

This exercise does not use `package.json`, every files can be left at the
repository root.

## Steps

### HTML

In the `body` of `index.html`, create:
- a `header` tag
- a `main` tag which contains:
  - a `div` with the class `player`
  - a 3x3 cells `table`
  - a `div` with the class `winner`
- a `footer` tag

### CSS

Download the `cross.svg` and `circle.svg` files to your directory.

Create a `style.css` (and add the `link` in the `head` of your
`index.html`) with the following content:

````css
*,
*:before,
*:after {
  box-sizing:/* fill here */;
}


body {
  font-family:/* fill here */;
}

header,
main {
  width:/* fill here */;
  margin:/* fill here */;
}

table {
  width:/* fill here */;
  height:/* fill here */;
  border:/* fill here */;
  border-collapse:/* fill here */;
  margin:/* fill here */;
}

td {
  border:/* fill here */;
  width:/* fill here */;
  height:/* fill here */;
}

.border-vertical,
.border-horizontal {
  border:/* fill here */;
}
.border-vertical {
  border-left-width:/* fill here */;
  border-right-width:/* fill here */;
}
.border-horizontal {
  border-top-width:/* fill here */;
  border-bottom-width:/* fill here */;
}

.circle,
.cross {
  background-repeat:/* fill here */;
  background-position:/* fill here */;
}
.circle {
  background-image:/* fill here */;
}
.cross {
  background-image:/* fill here */;
}

.player,
.winner {
  text-align:/* fill here */;
}
.winner:empty {
  visibility:/* fill here */;
}
````

**Notes:**
- You will have to add the right (`border-vertical` and `border-horizontal`) classes to the `td` elements
- In order to make the design, add the classes `circle` and `cross` to a `td` (and remove them when you are done ;) ).

Make the result look like:

![image](https://user-images.githubusercontent.com/65971/30580345-7d1285a2-9d1c-11e7-962a-c93b6ffefd23.png) 

### JavaScript

Create a `index.js` file (add the `script` tag just before the closing `body` tag
of your `index.html`).

In your `index.js` add the following content and complete where indicate by the comments.

````js
var matrix = [];
var currentPlayer = 'O';
var currentPlayerElement = /* fill here */;
var winnerElement = /* fill here */;



function clearMatrix() {
  for (var rowNum = 0; rowNum < 3; rowNum++) {
    matrix[rowNum] = [];
    for (var colNum = 0; colNum < 3; colNum++) {
      matrix[rowNum].push(null);
    }
  }
}

function clearClasses() {
  /* fill here */
}



function checkWinner() {
  for (var rowNum = 0; rowNum < matrix.length; rowNum++) {
    var joinedRow = matrix[rowNum].join('');
    if (joinedRow === 'OOO') {
      return 'O';
    }
    else if (joinedRow === 'XXX') {
      return 'X'
    }
  }

  /* fill here */

  var diagonal1 = matrix[0][0] + matrix[1][1] + matrix[2][2];
  /* fill here */

  var diagonal2 = /* fill here */;
  /* fill here */
}


function checkFinished() {
  var hasEmptyCell;
  /* fill here */
  // if there is an empty cell, then the game is not finished
  return !hasEmptyCell;
}


function clearGame() {
  /* fill here */
}


function choose(rowNum, colNum, cellElement) {
  var cellClass = 'cross';
  /* fill here */

  cellElement.classList.add(cellClass);
  /* do something with the "matrix" here */

  var winner = checkWinner();
  if (winner) {
    clearGame();
    winnerElement.textContent = '"' + winner + '" has won!';
    return;
  }
  winnerElement.textContent = '';

  if (checkFinished()) {
    /* fill here */
  }

  /* fill here */
  currentPlayerElement.textContent = 'It is "' + currentPlayer + '" turn';
}


/* fill here */.forEach(function(tdElement, index) {
  var rowNum = Math.floor((index / 3) % 3);
  var colNum = Math.floor(index % 3);

  tdElement.addEventListener('click', /* fill here */);
});


clearMatrix();
clearClasses();
currentPlayerElement.textContent = 'It is "' + currentPlayer + '" turn';
````

### Bonus 1

Add local persistence with `localStorage` so that if the page is reloaded the state
of the game is restored (current player and cells).

### Bonus 2

Find the bug in the game logic (there's at least 1) and fix it.
