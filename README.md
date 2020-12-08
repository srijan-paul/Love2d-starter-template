# LÖVE starter template.

A starter project template for making Love2D games.
Contains the following libraries:

- [middleclass](https://github.com/kikito/middleclass) - Elegant classes and OOP (credits: kikito).
- [Timer](https://github.com/vrld/hump/blob/master/timer.lua) - Timers for tweening and periodic event stuff (credits: vrld).
- [json](https://github.com/rxi/json.lua) - basic JSON string loading and parsing. (credits: rxi)
- [vector2d](https://bitbucket.org/inJuly/love_vector/src/master/) - 2D vector library.
- **sugar** - general utility functions (lerping, stack data structure, hex to RGB colors etc).
- **janim** - simple Animation library for creating animations out of spritesheets.
- **camera** - very simple camera management library. Doesn't support screenshaking or other effects so feel free to roll in your own camera if you need that.

# Build

- Clone the repo using `git clone`.
- Make sure have LÖVE2D version 11.0 or higher installed.
- Fire the terminal and use `love .` to launch the game

# Usage

The entry point for the game is in the file `game.lua`, the functions `load`, `draw` and
`update` from `game.lua` are required into `main.lua` and called from there.
So you will be spending most of the time editing `game.lua`.

# Note

This isn't a library, it's a basic project template so feel free to make
changes to the code as you see fit for your game. In fact, most of the times you might **need** to edit `main.lua` or `conf.lua`.

The majority of the game's code however, resides in `game.lua`.

# FAQ

How do I..

- **Switch to fullscreen ?**
  In `conf.lua`, change `GameSettings.fullscreen` to `true`.

- **Change window width and height?**
  In `conf.lua`, change `_G.WIN_WIDTH` and `_G.WIN_HEIGHT` to your desired dimensions.

- **Make the default cursor visible?**
  In `main.lua`, change `IS_MOUSE_POINTER_VISIBLE` to `true`.

- **Remove the custom cursor?**
  Comment out line 77 in `main.lua` inside `love.draw` that says `draw_cursor()`.

- **Use my own custom cursor?**

  1. Take note of your cursor sprite/image's width and height.
  2. Paste your cursor image in `assets/`, name it `cursor.png`. delete the default one.
  3. Go to `main.lua`, change `CURSOR_SCALE_X` and `CURSOR_SCALE_Y` to youre preferred scale.

- **Use my own shader?**
  Edit the shader posted in shader.lua file.
  To send data to the shader, just write your code in
  the commented region right here in `main.lua`:

  ```lua
  function love.draw()
  main_canvas:renderTo(function()
      lg.clear()
      game.draw()
      draw_cursor()
  end)
  -- send data to `shader` by writing code here. eg:
  -- shader:send('time', love.timer.getTime())
  lg.setShader(shader)
  lg.draw(main_canvas, SCREEN_OFFSET_X, 0, display_scale, display_scale)
  lg.setShader()
  end
  ```

- **Change the window title?**
  In `conf.lua`, line 1. change `GameInfo.name` to the window title you want.
