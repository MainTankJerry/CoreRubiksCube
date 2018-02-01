# Core Rubik's Cube



<img src="http://safecrackermethod.com/images/rubiks-cube-simple-ten-solution-070-200x.jpg" title="Rubik's Cube">

Core Rublik's Cube is a piece of code to implement basic implementation of Rubik's Cube.  It does not offer any graphical user interface nor feature to solve the cube.  It does, however, provide turn faces or to reverse those turns to find the state of the cube programmatically.

### Usage

You may instantiate a cube with initialized positions, and print it as follows.

```.swift
let cube1 = Cube()
print(cube1)
```

The cube's state should be printed to console as follows.

```
|   |   |   |U18|U19|U20|   |   |   |   |   |   |
|   |   |   |U10|U11|U12|   |   |   |   |   |   |
|   |   |   |U01|U02|U03|   |   |   |   |   |   |
|L18|L10|L01|F01|F02|F03|R03|R12|R20|B20|B19|B18|
|L21|L13|L04|F04|F05|F06|R06|R14|R23|B23|B22|B21|
|L24|L15|L07|F07|F08|F09|R09|R17|R26|B26|B25|B24|
|   |   |   |D07|D08|D09|   |   |   |   |   |   |
|   |   |   |D15|D16|D17|   |   |   |   |   |   |
|   |   |   |D24|D25|D26|   |   |   |   |   |   |
```

Then you may turn front face counter clockwise and print as follows. 

```.swift
let cube2 = cube1.makeFront(.counterclockwise)
print(cube2)
```
 You will find front face and it's related cubelets are rotated counter clockwise.
 

```
|   |   |   |U18|U19|U20|   |   |   |   |   |   |
|   |   |   |U10|U11|U12|   |   |   |   |   |   |
|   |   |   |R03|R06|R09|   |   |   |   |   |   |
|L18|L10|U03|F03|F06|F09|D09|R12|R20|B20|B19|B18|
|L21|L13|U02|F02|F05|F08|D08|R14|R23|B23|B22|B21|
|L24|L15|U01|F01|F04|F07|D07|R17|R26|B26|B25|B24|
|   |   |   |L01|L04|L07|   |   |   |   |   |   |
|   |   |   |D15|D16|D17|   |   |   |   |   |   |
|   |   |   |D24|D25|D26|   |   |   |   |   |   |
```

You may provide a sequence of `Movement` which describes face and turn direction to perform multiple turns in once just like following example.


```.swift
let moves: [Movement] = [
	.front(turn: .clockwise), .back(turn: .clockwise),
	.left(turn: .counterclockwise), .right(turn: .counterclockwise),
	.up(turn: .double), .down(turn: .double)
]
let cube3 = cube.makeMoves(moves)
```

You may perform the same sequence backward to reverse the operation.

```.swift
let cube4 = cube3.reverseMoves(moves)
```

Since, `Cube` conforms `Equatable` protocol,  you may make sure reversing operation actually work.

```.swift
cube4 == cube // true
```

### Types

| Type  | Description |
|:------------|:------------|
| Face       	| Specifies a face direction of cube |
| Surface    	| Specifies a face of cube that contains tiles |
| Tile       	| A suface of a cubelet.  A surface contains 3x3, 9 `Tile`s. |
| Turn       	| A turn direction either `clockwise`, `counterclockwise`, or `double` |
| Movement   	| A single turn action which face and which turn direction |
| Cube   		| A whole cube with six surfaces |


### Environment

```
Xcode 9.2
Apple Swift version 4.0.3 (swiftlang-900.0.74.1 clang-900.0.39.2)
Target: x86_64-apple-macosx10.9
```

