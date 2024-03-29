# MAD - Exercise 01
## Tasks
* Watch the Kotlin Crashcourse Video in Moodle or complete the tutorials **[Introduction to programming in Kotlin](https://developer.android.com/courses/pathways/android-basics-compose-unit-1-pathway-1)** and **[Kotlin fundamentals](https://developer.android.com/courses/pathways/android-basics-compose-unit-2-pathway-1
)**.
* Answer the questions inside this Readme.md file and push it to your repository.
* Submit your coding solution of the Number Guessing Game inside the repository.
* Submit the link to your repository in Moodle.

## Questions
### Describe how Kotlin handles null safety. What are nullable types and non-null types in Kotlin? (0,5 points)

<span style="color:blue">Bei Kotlin ist der Wert null bei normalen Variablen ausgeschlossen. (Code Example 1) Diese Variablen können erst verwendet werden, nachdem sie mit einem konkreten Wert initialisiert wurden. Das schließt zwar eine NullPointerException aus, ist aber für manche Anwendung zu restriktiv. Es gibt eine Möglichkeit, null explizit zu erlauben. Beim Typ muss ein Fragezeichen erfolgen. (Code Example 2) Möglichkeit zur Testung von "null" ist auf Code Example 3 zu sehen. Es gibt auch den Safe-Call-Operator "?.", dieses wird mird mit obj?.property bzw. obj?.method() ausgewertet, aber auch nur, wenn das Objekt Daten enthält. (example 4) nullable types: sind Variablen, die auch null annehmen können, diese werden bei der Initialisierung mit einem "?" initialisiert. (Code example 5) non-null types: sind Variablen, die kein null aufnehmen können, da ihnen bei der Initialisierung das "?" fehlt. (Code Example 6) Force Null kann man mit !! erreichen. </span>
<span style="color:blue"> </span>

> Note: you can also use code snippets to illustrate your answer.

```kotlin
// Code example 1
val x = "Hallo" //oder
val x: String = "Hallo"
// Code example 2
val x: String?

// Code example 3
val x = getPerhapsAnything()
if (x is Int)
    println("x=$x")
//Code example 4
val x = getPerhapsAnything()
println("x=${p?.variable1}")
// Code example 5
val a: String? = "value" // nullable type
// Code example 6
val a: String = "value" // non-null type
```

### What are lambda expressions and higher order functions in Kotlin? Why would you store a function inside a variable? (0,5 points)

<span style="color:blue">Lambda Expressions sind Funktionen, welche im Code gleichzeitig definiert und ausgeführt werden können. Zweckmäßigkeit: wenn man eine Funktion nur an einer Stelle braucht. Man kann dazu auch sagen, dass sie anonyme Funktionen sind, welche als Inline Funktionen behandelt werden können. Higher-order functions sind Funktionen, welche andere Funktionen als Parameter haben und Funktionen zurückgeben können. Why would you store a function inside a variable?: Um gegebenfalls die Codebasis zu verbessern und auch erweitern zu können. Es bietet eine leistungsstarke Möglichkeit die Codebasis zu strukturieren und wiederverwendbare Komponenten zu erstellen. Beispiele: Das Speichern einer Funktion in einer Variable ermöglicht es u.a. das Verhalten des Programms dynamisch zur Laufzeit zu verändern. Weiteres Beispiel ist die Modularität. Man kann somit verschiedene Verhaltensweisen oder Operationen kapseln, welche die Wartung, Lesbarkeit und Erweiterung des Codes erleichtern. </span>

### Provide a solution for the following number guessing game inside `App.kt`. (3 points)

## Number Guessing Game in Kotlin
The game is a simple number guessing game. The task is to generate a random, max 9-digit, number. The number must **not contain repeating digits**. Valid digits are 1-9.
Ask the user to guess the max 9-digit number. The game is finished when the user guesses the correct digits in the correct order.
In each round, the user gets feedback about the number of correct digits and the number of correct digits in the correct position.
The output should be in the format "n:m", where "n" is the number of digits guessed correctly regardless of their position, 
and "m" is the number of digits guessed correctly at their correct position. Here are some examples:

This example shows the game flow with 4-digits to guess (the default argument)

Generated number: 8576
-	User input: 1234, Output: 0:0
-	User input: 5678, Output: 4:1
-	User input: 5555, Output: 1:1
-	User input: 3586, Output: 3:2
-	User input: 8576, Output: 4:4 -> user wins

Take a look into the provided code structure in `src/main/kotlin/App.kt`. Implement the following methods (lambda expressions):
- _playNumberGame(digitsToGuess: Int = 4)_ (1 point): The main game loop that handles user input and game state. Make use of _generateRandomNonRepeatingNumber_ and _checkUserInputAgainstGeneratedNumber_ here. This function also utilizes a default argument 
- _generateRandomNonRepeatingNumber_ (1 point): A lambda expression that generates a random number with non-repeating digits of a specified length.
- _checkUserInputAgainstGeneratedNumber_ (1 point): A lambda expression that compares the user's input against the generated number and provides feedback.

``CompareResult.kt`` This class is a data structure which helps with bundling the result of the comparison of the user input and the generated number. Look at the toSting() and use it in your output.

Run the project with `./gradlew run` and test your implementation with the provided tests in `src/test/kotlin/AppTest.kt` with `./gradlew test`.

# Project Structure
The project is structured into two main Kotlin files:

**App.kt**: Contains the main game logic and functions.

**AppTest.kt**: Contains unit tests for the various functions in App.kt.

