# `MacroRecord`
Starts recording macro under first pressed key. Uses register `0` to track if macro is being recorded - if so, then running macro again stops recording and saves associated key in register `1`.

Use [`MacroPlay`](MacroPlay.md) to play saved macros.

```
ifNotRegEq 0 0 goTo stop
    setLedTxt 0 REC
    postponeKeys ifNotPending 1 goTo @0
    setReg 0 %0
    consumePending 1
    recordMacro #0
    goTo end
stop:
    stopRecording
    setReg 1 #0
    setReg 0 0
    setLedTxt 2000 END
end:
```
