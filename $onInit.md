# `$onInit`
Macro executed after powering on the keyboard - enables extended commands, sets fade timeout to 5 minutes and executes `lcd` macro.

```
set macroEngine.extendedCommands 1
set leds.fadeTimeout 5

exec lcd
```
