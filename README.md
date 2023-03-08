# Mobile Application Developement

Kotlin

2022-23

© G. Malnati, A. Rabino, 2021-23

## Introduzione e storia

- Linguaggio di programmazione a tipizzazione statica per applicazioni multipiattaforma moderne [https://kotlinlang.org/](https://kotlinlang.org/)
- Largamente ispirato alle tecniche di programmazione funzionale: funzioni di ordine superiore, chiusure, immutabilità, tipi algebrici, funtori, monadi, ecc.
- Ha preso idee sensate da varie fonti: C#, Javascript, Scala, Groovy, Java, Haskell, ecc.
- Si rivolge a diverse piattaforme

## La timeline di Kotlin

- Luglio '11: Inizio del progetto
- Febbraio '16: Kotlin 1.0
- Marzo '17 - Kotlin 1.1: Javascript e coroutine
- Novembre '17: Kotlin 1.2: Interoperabilità Java/JS
- Ottobre '18: Kotlin 1.3: Supporto nativo
- Agosto '20: Kotlin 1.4.0
- Maggio '21: Kotlin 1.5.0
- Dicembre '21: Kotlin 1.6.10
- Settembre '22: Kotlin 1.7.20
- Febbraio '23: Kotlin 1.8.10

## Giocare con Kotlin

- Un'interfaccia REPL online è disponibile come playground [https://play.kotlinlang.org/](https://play.kotlinlang.org/)
- Consente di sperimentare facilmente con i costrutti del linguaggio e vedere le differenze tra le varie versioni del linguaggio e della piattaforma di destinazione: JVM, JVM + JUnit, Javascript, Javascript Intermediate Representation (IR), JS Canvas, ecc.
- È possibile condividere il codice creato con il playground con altre persone e ospitarlo in siti di terze parti

## Il sistema di tipi di Kotlin

- Kotlin è un linguaggio a tipizzazione statica
- Le variabili, i temporanei, i parametri delle funzioni e i tipi di ritorno sono etichettati con il tipo del valore a cui possono essere assegnati
- Il compilatore utilizza un potente sistema di inferenza dei tipi per effettuare deduzioni e rilevare possibili errori il prima possibile
- Le variabili e le funzioni possono essere annotate con un tipo esplicito in caso di ambiguità
- Kotlin non ha un insieme di tipi primitivi come Java, ma si basa solo sul corrispondente tipo boxed (Int, Short, Long, Byte, Float, Double, Char, Boolean), avendo quindi una semantica di riferimento per ogni tipo
- Tuttavia, il compilatore ottimizza internamente il tipo effettivo dei dati, quando possibile, riducendo l'overhead effettivo dovuto al boxing e all'allocazione basata su heap e garantendo lo stesso livello di efficienza fornito dal linguaggio Java

## Ecco alcuni esempi di codice che mostrano come funziona la Null Safety in Kotlin:

1. Variabile non nulla:

```kotlin
val a: String = "Hello"
val b: String? = null

```

In questo esempio, la variabile `a` è non nulla perché è stata inizializzata con una stringa. Invece, la variabile `b` è nulla perché è stata definita come una variabile nullable.

1. Operatore di chiamata sicura:

```kotlin
val a: String? = null
val b: Int? = a?.length

```

In questo esempio, la variabile `a` è nulla, ma grazie all'operatore di chiamata sicura `?.`, l'accesso alla proprietà `length` non genera un'eccezione, ma restituisce un valore null.

1. Operatore elvis:

```kotlin
val a: String? = null
val b: Int = a?.length ?: -1

```

In questo esempio, la variabile `a` è nulla, ma grazie all'operatore elvis `?:`, se la proprietà `length` è nulla, viene restituito il valore `-1`.

1. Operatore di finta non nullità:

```kotlin
val a: String? = null
val b: Int = a!!.length

```

In questo esempio, la variabile `a` è nulla, ma grazie all'operatore di finta non nullità `!!`, viene forzata la non nullabilità della variabile. Se la variabile è nulla, viene generata un'eccezione di tipo `NullPointerException`.

## Tipi di funzione

- Il sistema di tipi di Kotlin supporta anche i tipi di funzione
- I tipi di funzione possono essere istanziati con funzioni regolari, letterali di funzione ed espressioni lambda
- Sono comunemente usati nella programmazione funzionale e possono essere utilizzati per creare codice più modulare, flessibile ed espressivo

## Funzioni con nome

- Le funzioni con nome sono funzioni che hanno un nome che può essere utilizzato per chiamarle
- Sono definite utilizzando la parola chiave fun seguita dal nome della funzione e dal corpo della funzione
- Il corpo della funzione può contenere istruzioni arbitrarie e può restituire un valore
- Le funzioni con nome sono il tipo più comune di funzione in Kotlin e vengono utilizzate per definire blocchi di codice riutilizzabili che possono essere chiamati da diverse parti di un programma

## Parametri della funzione

- Specificano i tipi e il numero di argomenti che una funzione accetta
- I parametri della funzione possono avere valori predefiniti
- I parametri della funzione possono essere nominati durante la chiamata delle funzioni

## Corpo della funzione

- Le funzioni Kotlin possono contenere una vasta gamma di istruzioni, che consentono di definire la logica e il comportamento del proprio programma
- La maggior parte di esse si comporta in modo simile alle corrispondenti istruzioni in Java, ma ci sono alcune eccezioni notevoli

## Istruzioni di controllo

- La clausola if è un'espressione: ogni branch restituisce un valore
- Se un branch contiene un blocco, l'ultimo valore del blocco viene restituito
- La clausola when sostituisce il costrutto switch di Java
- Lo statement for opera solo con iteratori, intervalli o iterable
- La sintassi tradizionale, tipo C, è stata rimossa

## Le espressioni lambda sono spesso usate in combinazione con altre funzionalità del linguaggio come ad esempio la funzione `map`.

Ecco un esempio di come utilizzare le espressioni lambda per trasformare una lista di numeri:

```kotlin
val numbers = listOf(1, 2, 3, 4, 5)
val squaredNumbers = numbers.map { it * it }
println(squaredNumbers) // Output: [1, 4, 9, 16, 25]

```

In questo esempio, `map` è una funzione di ordine superiore che accetta una funzione come parametro. La funzione passata a `map` è un'espressione lambda che viene utilizzata per trasformare ogni numero nella lista in un quadrato.

Ecco un altro esempio di come utilizzare le espressioni lambda per filtrare una lista di numeri:

```kotlin
val numbers = listOf(1, 2, 3, 4, 5)
val filteredNumbers = numbers.filter { it % 2 == 0 }
println(filteredNumbers) // Output: [2, 4]

```

In questo esempio, `filter` è una funzione di ordine superiore che accetta una funzione come parametro. La funzione passata a `filter` è un'espressione lambda che viene utilizzata per filtrare i numeri pari dalla lista.

## Tipi definiti dall'utente

- Kotlin supporta completamente il paradigma orientato agli oggetti e fornisce un insieme di classi incorporate con una singola gerarchia di ereditarietà
- Possono essere definite ulteriori classi come estensioni di quelle esistenti
- Le interfacce possono essere organizzate in più gerarchie di ereditarietà (zero o più)

## Classi

- La parola chiave class introduce una nuova classe
- Le classi hanno un costruttore primario e zero o più costruttori secondari

## Proprietà

- Ogni classe può dichiarare zero o più proprietà che vengono utilizzate per memorizzare e rappresentare i dati all'interno delle istanze di quella classe

## Metodi

- Ogni classe può definire zero o più metodi che rappresentano il comportamento che le istanze della classe possono eseguire
- I metodi possono accedere alle proprietà della classe e possono essere chiamati da altre parti del programma

Esempio di definizione di un metodo:

```kotlin
class Person(var name: String, var age: Int) {
    fun sayHello() {
        println("Hello, my name is $name and I am $age years old.")
    }
}

```

Esempio di chiamata di un metodo:

```kotlin
val person = Person("John", 30)
person.sayHello() // Hello, my name is John and I am 30 years old.

```

## Companion Objects

- Kotlin supporta gli oggetti compagni, che sono oggetti associati a una classe e che possono avere proprietà e metodi statici
- Gli oggetti compagni sono utili per fornire funzionalità che non dipendono da un'istanza della classe

Esempio di definizione di un oggetto compagno:

```kotlin
class MyClass {
    companion object {
        const val CONSTANT = "My constant value"

        fun myStaticMethod() {
            println("This is a static method")
        }
    }
}

```

Esempio di utilizzo di una costante dell'oggetto compagno:

```kotlin
println(MyClass.CONSTANT) // My constant value

```

Esempio di chiamata di un metodo statico dell'oggetto compagno:

```
MyClass.myStaticMethod() // This is a static method

```

## Estensioni

- Kotlin supporta l'estensione delle classi esistenti con nuovi metodi e proprietà
- Le estensioni sono utili per aggiungere funzionalità a classi esistenti senza dover sottoporre la classe originale a modifiche

Esempio di definizione di un metodo estensione per una classe esistente:

```kotlin
fun String.removeSpaces(): String {
    return this.replace(" ", "")
}

```

Esempio di chiamata del metodo estensione:

```kotlin
val myString = "Hello world"
val newString = myString.removeSpaces()
println(newString) // Helloworld

```

## Generics

- Kotlin supporta i tipi generici, che consentono di scrivere codice che funziona con un'ampia varietà di tipi
- I tipi generici sono usati per creare classi, metodi e funzioni che possono lavorare con tipi arbitrari

Esempio di definizione di una classe generica:

```kotlin
class Box<T>(var item: T)

```

Esempio di creazione di un'istanza di una classe generica:

```kotlin
val box = Box("Hello")
val box2 = Box(42)

```

Esempio di definizione di una funzione generica:

```kotlin
fun <T> myFunction(item: T) {
    // do something with item
}

```

Esempio di chiamata di una funzione generica:

```kotlin
myFunction("Hello")
myFunction(42)

```

## Errori comuni Kotlin

Ecco alcuni degli errori più comuni che si possono incontrare durante la scrittura di codice Kotlin:

- **NullPointerException**: questo errore si verifica quando si cerca di accedere a una variabile nullabile senza prima controllare se è null o meno. Per evitare questo errore, è possibile utilizzare l'operatore di chiamata sicura `?.` o l'operatore elvis `?:`.
- **Type mismatch**: questo errore si verifica quando si assegna un valore di tipo diverso a una variabile. Per risolvere questo errore, è necessario assicurarsi che il tipo della variabile corrisponda al tipo del valore assegnato.
- **Unresolved reference**: questo errore si verifica quando si cerca di utilizzare una variabile o una funzione che non è stata definita. Per risolvere questo errore, è necessario definire la variabile o la funzione prima di utilizzarla.
- **Unreachable code**: questo errore si verifica quando il compilatore rileva del codice che non verrà mai eseguito. Per risolvere questo errore, è necessario rimuovere il codice inutile.
- **Ambiguous reference**: questo errore si verifica quando il compilatore non è in grado di determinare quale variabile o funzione si sta cercando di utilizzare. Per risolvere questo errore, è necessario specificare il nome della variabile o della funzione corretta.
- **Duplicate class**: questo errore si verifica quando si definisce una classe con lo stesso nome di un'altra classe. Per risolvere questo errore, è necessario rinominare una delle classi.
- **Unresolved import**: questo errore si verifica quando si cerca di importare una classe che non esiste. Per risolvere questo errore, è necessario verificare che il nome della classe sia corretto e che la libreria contenente la classe sia stata importata correttamente.

*Ricorda sempre di controllare attentamente il tuo codice e di eseguire i test per assicurarti che funzioni correttamente.*
