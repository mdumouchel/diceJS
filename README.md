# diceJS

Just a repo for http://a.teall.info/dice/
All credit for the code should go to him.

He has offered the code up for use and to make it a bit easier. 
I decided to try and document it's uses.  
Also a starting point for making whatever changes are nesscary.

Basic Example

```
//Get the canvas area.
//$t could be exhanged with anything to can get a dom element.
var canvas = $t.id('canvas');

//Set the height and width of the canvas area.
canvas.style.width = window.innerWidth - 1 + 'px';
canvas.style.height = window.innerHeight - 1 + 'px';

//Not sure if this is needed.
$t.dice.use_true_random = false;

//Build the dice_box area.
var box = new $t.dice.dice_box(canvas, { w: 500, h: 300 });

//Set the state for rolling.				
box.rolling = false;

//The three callbacks nesscary to throw a dice.
function notation_getter() {
	return $t.dice.parse_notation("6d20");
}

function before_roll(vectors, notation, callback) {
	callback();
}

function after_roll(notation, result) {
	console.log(notation, result)
}

//Throw them!
box.start_throw(notation_getter, before_roll, after_roll);
```

before_roll


TODO - Some of the things I would like to do with this.
  * Continue to document the features available
  * Decouple some of the interface options from the dice.
  * Decouple the THREE render and initialization.
  * Decouple the cannon render and initialization.
