# Simple-Stacker
Arcade game Stacker for the embedded LaFortuna board (at90usb1286 microprocessor)<br/>


THIS project is made ONLY for the LaFortuna board with at90usb1286 microprocessor.<br/>
Used libraries for LCD ,LED and rotary used are from Steve Gunn.<br/>

This game is inspired by the arcade stacker game, with the rigged winnings.(Simple stacker is not rigged!)<br/>
It uses the device's internal interrupts to take register of the game logic and drawing on screen.<br/>

## [Compilation]
In order to compile the game onto your LaFortuna you need to be in the same directory as the 'stacker.c'.<br/>
Then enter the command: `make` <br/>
The Simple Stacker will load on your board.

Another way to load the game is to go to the directory **_build**, where the **main.hex** is
Use the commands:
  * `dfu-programmer at90usb1286 erase --force`
  * `dfu-programmer.exe at90usb1286 flash main.hex`

This will flash the hex file to your board without compiling and using the make command for the make file

The project also includes my .vscode folder, you can change the file locations to accomodate for your installaton, if you need syntax highlighting.



## [Guide]
The game is played with the LaFortuna positioned HORIZONTALLY, meaning that for sake of in game logic it means that:  
East Button(Vertical) -> North Button(UP Horizontal)  
South Button(Vertical)  -> East Button(Right Horizontal)  
North Button(Vertical)  -> West Button(Left Horizontal)  
Further mentions of the buttons will talk about their Horizontal positioning.  

## [Menu Screen]

<img src="https://user-images.githubusercontent.com/59044933/115999501-f1ee0800-a5e3-11eb-9e2c-41dd5cdf7d2b.jpg" width="400" height="300" />

* You can Start a new Game by pressing the UP button
* You can change the size of the block, which will update the shown block on the bottom of the Screen and update the Block Size variable on screen
  * Press Left to lower block size, an indicator '<' will show for a moment as feedback
  * Press Right to increase block size, an indicator '>' will show for a moment as feedback
  * Block Sizes are between 10 pixels and 70pixels

## [Gameplay]

<img src="https://user-images.githubusercontent.com/59044933/115999517-fe726080-a5e3-11eb-8ade-f0a32941f4f5.jpg" width="400" height="300" />

* The only button to press is the CENTER button, After each press the block will stop for '1250 ms' for you to see where you have hit and will
  place a green block on that place, moving the new red block on the top level to the side.
* Make sure you hold the button on press for a little, due to interrupts and delays, if you release the button too fast on being on a certain block, it will not register.
  * To be exact when you see the red block move to the desired space, there is a delay before updating the location for the next Red block,
    if you press the button in that time, and the delay ends it will then register and go on the next level.

## *Ongoing Bugs:*
*  Sometimes the LaFortuna won't register a fast click. (Try holding it for a bit after pressing, there is a 1250ms delay after each press
   so it will be safe to hold for a bit)
