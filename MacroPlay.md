# `MacroPlay`
Plays macro saved under first pressed key. If first pressed key is `2/@` then plays last played/recorded macro. Uses register `1` to store last played macro.

Use [`MacroRecord`](MacroRecord.md) to record new macros.

```
setLedTxt 0 PLY
postponeKeys ifNotPending 1 goTo @0
ifNotKeyPendingAt 0 66 setReg 1 %0
consumePending 1
playMacro #1
setLedTxt 1
```
