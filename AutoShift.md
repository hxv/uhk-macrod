# `AutoShift`
Outputs "normal" key after pressing it for less than 150ms, and Shift+key after pressing it for more than 150ms. Uses register 3 to store pressed key.

In all variants I remapped all character keys to the macro - so keyboard glows purple all the time :)

## Attempt #1
I created two layers - fn4 with all remapped keys, and fn5 with all remapped keys with shift modifier.

Pros - macro is shorter, holding key works (outputs key multiple times)  
Cons - any unmapped key pressed right after mapped key can be outputted first, so basically everything (except for modifiers) must be mapped, also a looot of clicking is required to prepare layers

Despite some problems right now this is preferred way for me.

```
loop:
    postponeKeys ifAnyMod goTo normal
    postponeKeys ifPlaytime 150 goTo shift
    postponeKeys ifNotReleased goTo loop

normal:
    activateKeyPostponed atLayer fn4 #key

    break

shift:
    activateKeyPostponed atLayer fn5 #key

    break
```

## Attempt #2
No extra layers needed, but macro is very long, and uses register 3 to store pressed key.

Pros - seems to work better if not everything is remapped, and does not require extra layers (which are pretty time consuming to set up)  
Cons - I can't get multiple keypresses to work, keys need to be manually mapped

```
loop:
    setReg 3 #key
    postponeKeys ifAnyMod goTo normal
    postponeKeys ifPlaytime 150 goTo shift
    postponeKeys ifNotReleased goTo loop

normal:
    # left half
    ## row 0
    ifRegEq 3 64 tapKey graveAccentAndTilde
    ifRegEq 3 65 tapKey 1
    ifRegEq 3 66 tapKey 2
    ifRegEq 3 67 tapKey 3
    ifRegEq 3 68 tapKey 4
    ifRegEq 3 69 tapKey 5
    ifRegEq 3 70 tapKey 6

    ## row 1
    ifRegEq 3 72 tapKey q
    ifRegEq 3 73 tapKey w
    ifRegEq 3 74 tapKey e
    ifRegEq 3 75 tapKey r
    ifRegEq 3 77 tapKey t

    ## row 2
    ifRegEq 3 79 tapKey a
    ifRegEq 3 80 tapKey s
    ifRegEq 3 81 tapKey d
    ifRegEq 3 82 tapKey f
    ifRegEq 3 84 tapKey g

    ## row 3
    ifRegEq 3 87 tapKey z
    ifRegEq 3 88 tapKey x
    ifRegEq 3 89 tapKey c
    ifRegEq 3 90 tapKey v
    ifRegEq 3 91 tapKey b

    # right half
    ## row 0
    ifRegEq 3 0 tapKey 7
    ifRegEq 3 1 tapKey 8
    ifRegEq 3 2 tapKey 9
    ifRegEq 3 3 tapKey 0
    ifRegEq 3 4 tapKey minusAndUnderscore
    ifRegEq 3 5 tapKey equalAndPlus

    ## row 1
    ifRegEq 3 14 tapKey y
    ifRegEq 3 7  tapKey u
    ifRegEq 3 8  tapKey i
    ifRegEq 3 9  tapKey o
    ifRegEq 3 10 tapKey p
    ifRegEq 3 11 tapKey openingBracketAndOpeningBrace
    ifRegEq 3 12 tapKey closingBracketAndClosingBrace
    ifRegEq 3 13 tapKey backslashAndPipe

    ## row 2
    ifRegEq 3 21 tapKey h
    ifRegEq 3 15 tapKey j
    ifRegEq 3 16 tapKey k
    ifRegEq 3 17 tapKey l
    ifRegEq 3 18 tapKey semicolonAndColon
    ifRegEq 3 19 tapKey apostropheAndQuote

    ## row 3
    ifRegEq 3 22 tapKey n
    ifRegEq 3 23 tapKey m
    ifRegEq 3 24 tapKey commaAndLessThanSign
    ifRegEq 3 25 tapKey dotAndGreaterThanSign
    ifRegEq 3 26 tapKey slashAndQuestionMark

    break

shift:
    # left half
    ## row 0
    ifRegEq 3 64 tapKey S-graveAccentAndTilde
    ifRegEq 3 65 tapKey S-1
    ifRegEq 3 66 tapKey S-2
    ifRegEq 3 67 tapKey S-3
    ifRegEq 3 68 tapKey S-4
    ifRegEq 3 69 tapKey S-5
    ifRegEq 3 70 tapKey S-6

    ## row 1
    ifRegEq 3 72 tapKey S-q
    ifRegEq 3 73 tapKey S-w
    ifRegEq 3 74 tapKey S-e
    ifRegEq 3 75 tapKey S-r
    ifRegEq 3 77 tapKey S-t

    ## row 2
    ifRegEq 3 79 tapKey S-a
    ifRegEq 3 80 tapKey S-s
    ifRegEq 3 81 tapKey S-d
    ifRegEq 3 82 tapKey S-f
    ifRegEq 3 84 tapKey S-g

    ## row 3
    ifRegEq 3 87 tapKey S-z
    ifRegEq 3 88 tapKey S-x
    ifRegEq 3 89 tapKey S-c
    ifRegEq 3 90 tapKey S-v
    ifRegEq 3 91 tapKey S-b

    # right half
    ## row 0
    ifRegEq 3 0 tapKey S-7
    ifRegEq 3 1 tapKey S-8
    ifRegEq 3 2 tapKey S-9
    ifRegEq 3 3 tapKey S-0
    ifRegEq 3 4 tapKey S-minusAndUnderscore
    ifRegEq 3 5 tapKey S-equalAndPlus

    ## row 1
    ifRegEq 3 14 tapKey S-y
    ifRegEq 3 7  tapKey S-u
    ifRegEq 3 8  tapKey S-i
    ifRegEq 3 9  tapKey S-o
    ifRegEq 3 10 tapKey S-p
    ifRegEq 3 11 tapKey S-openingBracketAndOpeningBrace
    ifRegEq 3 12 tapKey S-closingBracketAndClosingBrace
    ifRegEq 3 13 tapKey S-backslashAndPipe

    ## row 2
    ifRegEq 3 21 tapKey S-h
    ifRegEq 3 15 tapKey S-j
    ifRegEq 3 16 tapKey S-k
    ifRegEq 3 17 tapKey S-l
    ifRegEq 3 18 tapKey S-semicolonAndColon
    ifRegEq 3 19 tapKey S-apostropheAndQuote

    ## row 3
    ifRegEq 3 22 tapKey S-n
    ifRegEq 3 23 tapKey S-m
    ifRegEq 3 24 tapKey S-commaAndLessThanSign
    ifRegEq 3 25 tapKey S-dotAndGreaterThanSign
    ifRegEq 3 26 tapKey S-slashAndQuestionMark

    break
```
