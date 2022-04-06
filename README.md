# Wordle



The shared `Wordle` class includes following `StateFlow`s representing the current set of guesses and updated status info for each letter.

```
val boardGuesses = MutableStateFlow<ArrayList<ArrayList<String>>>(arrayListOf())
val boardStatus = MutableStateFlow<ArrayList<ArrayList<LetterStatus>>>(arrayListOf())
```

The various clients call `WordService.setGuess()` when a user enters a letter and then `WordService.checkGuess()` after row of letters
are entered...UI then reflects any resulting updates to above `StateFlow`'s.  The Compose clients for example do that using following (with any updates to those `StateFlow's` triggering recomposition)

```
val boardGuesses by wordMasterService.boardGuesses.collectAsState()
val boardStatus by wordMasterService.boardStatus.collectAsState()
```
<br>


```

Any updates to `boardStatus` or `boardGuesses` will trigger our SwiftUI UI to be recomposed again.


### Remaining work includes

- check if overall word is valid and show indication in UI if not (ideally with animations!)
- better keyboard navigation
- share Compose code between Android and Desktop
- indicator in UI that correct guess entered (other than all letters being green)



