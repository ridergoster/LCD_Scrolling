# LCD Scrolling

This is a very simple module meant to be used with Johnny-five on your arduino/Raspberry Pie project.
The module detect if your text is bigger than the space offered by your LCD. If it's bigger the module will apply a sort of scrolling effect on the text so all the information is displayed and readeable.

This module remain very simple and don't offer many features yet but feel free to post pull request. I'll extend this module with multiple animation in the future.

## Example

```javascript
var five = require("johnny-five"),
    scroll = require('LCD_Scrolling'),
    board, lcd;

board = new five.Board();

board.on("ready", function() {

    lcd = new five.LCD({
        // LCD pin name  RS  EN  DB4 DB5 DB6 DB7
        // Arduino pin # 7    8   9   10  11  12
        pins: [7,8,9,10,11,12],
        rows: 2,
        cols: 16


        // Options:
        // bitMode: 4 or 8, defaults to 4
        // lines: number of lines, defaults to 2
        // dots: matrix dimensions, defaults to "5x8"
    });
    
    scroll.setup({
        lcd: lcd, /* Required */
        
        // Optional parameters defaults
        // debug: false, - true will enable console.log()
        // char_length: 16, - Number of characters per line on your LCD
        // row: 2, - Number of rows on your LCD
        // firstCharPauseDuration: 4000, - Duration of the pause before your text start scrolling
        // lastCharPauseDuration: 1000, - Duration to wait before restarting the animation
        // scrollingDuration: 300, - Time of per step (speed of the animation)
        // full: true - Extend text with white space to be animated out of the screen completely

    });
    
    
    scroll.line( 0, "Text of the first line" );
    scroll.line( 1, "Second line here" );

});
```