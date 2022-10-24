# `MacroRecord`
Starts recording macro under first pressed key. Uses register `0` to track if macro is being recorded - if so, then running macro again stops recording and saves associated key in register `1`.

Use [`MacroPlay`](MacroPlay.md) to play saved macros.

```
begin:
    ifNotRegEq 0 0 goTo stop
        postponeKeys ifNotPending 1 goTo begin
        setReg 0 %0
        consumePending 1
        recordMacro #0
        goTo end
stop:
        stopRecording
        setReg 1 #0
        setReg 0 0
end:
```
