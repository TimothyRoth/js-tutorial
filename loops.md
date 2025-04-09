# JavaScript - Loops

Im folgenden Kapitel soll es zwar um Schleifen (Loops) spezifisch in JavaScript gehen, allerdings ist das Konzept von Schleifen in der Welt der Software-Entwicklung so allgemein verankert,
dass die Ausführungen im weiteren Verlauf sprachübergreifend angewendet werden können.

## Was ist überhaupt eine Schleife ??

Ein Schleife ist eine sich wiederholende Programmsequenz.
So damit hätten wir es dann auch schon abgehandlet oder? Okay natürlich nicht. Was ist überhaupt eine Programmsequenz?

``` js
let number = 0;
console.log(number) // output: 0 
```

Genau. Das wäre eine Beispielhafte Programmsequenz. Wir definieren eine Zahl, setzen den Wert dieser Zahl auf 0 und geben uns zur Bestätigung diesen Wert einmal auf der Konsole aus. Eine Programmsequenz kann dabei beliebig lang sein. Sie zeichnet sich dadurch aus, dass diese prozedural von oben nach unten ausgeführt wird, mit der ersten Zeile beginnt und mit der letzten Zeile aufhört. In diesem Fall fängt die Sequenz also in Zeile 1 mit der Deklaration der Variable `number` an und hört in Zeile 2 mit dem `console.log` Befehl auf.

Was hat das ganze jetzt mit Schleifen zu tun? Naja wie bereits eingangs erwähnt, sind Schleifen dafür da um Programmsequenzen beliebig oft, eventuell sogar unendlich oft zu wiederholen. Um Schleifen im Detail zu verstehen, müssen wir erst einmal verstehen was eine Schleife im Kern tut. Machen wir uns das ganze mal anhand der `while Schleife` verständlich. Sie besteht im Kern auf 3 Teilen.

``` js
/*
 * 1. Dem while keyword
 */
while(true) /* 2. Der Abbruchsbedingung */ 
{
    /* 3. Dem Body */
}
```

In diesem konkreten Fall ist die Abbruchsbedingung aber keine wirklich abbrechende richtig? Wie wir ja bereits im Kapitel der `If-Statements` gelernt haben, muss in einer Bedingung immer ein sogenannter `boolscher Ausdruck` stehen. Sprich eine Gegenüberstellung die unser Compiler, im Fall von JavaScript der Browser, mit `true` oder `false` beantworten kann. Da while(true) eben immer true ist, haben wir damit eine unendliche Schleife erschaffen. Das heißt der Code welcher sich im `Body` befindet, wird unendlich oft ausgeführt. Eine echte Abbruchsbedingung wäre zum Beispiel:

``` js

let userIsLoggedIn = getUserLoginStatus();

while(userIsLoggedIn === true)
{
    renderProgram();
}

console.log("Program has ended");
```
Wo der Wert von `isUserLoggedIn` kommt ist in diesem Beispiel nicht so wichtig, er könnte z.B. das Ergebnis einer Datenbankabfrage sein oder aus der Session kommen. Wichtig ist nur, solange der Wert für isUserLoggedIn = true ist, wird das Programm ausgeführt. Gäbe es jetzt innerhalb der ausgeführten Sequenz `renderProgram()` die Möglichkeit userIsLoggedIn = false zu setzen, würde der boolsche Audruck welcher in den runden Klammern nach dem while steht false sein. Damit würde die Schleife durchbrochen werden und erst dann würde der console.log nach dem Body ausgeführt werden. Das heißt also, da unser Code von oben nach unten ausgeführt wird, geht es unter unserer Schleife nicht weiter, bis wir aus der Schleife "ausbrechen".

Ein konkreteres Beispiel einer Abbruchbedingung wäre beispielsweise:

``` js

let number = 0;

while(number < 10)
{
    console.log(number);
}

console.log("Loop has ended.");
```

In Zeile 1 definieren wir eine Zahl und setzen deren Wert auf 0. Dann initieren wir eine Schleife welche prüft ob number kleiner als 10 ist. Die Bedingung ist wahr, da number = 0 ist und 0 kleiner als 10. Also betreten wir den Body der Schleife. Im diesem Beispiel würde unsere Konsole nun endlos 0 ausgeben. Denn wir würden die im Body definierte Sequenz immer und immer wieder wiederholen. Mit nur einer Zeile können wir diese unendliche Schleife endlich machen. 

``` js
let number = 0;

while(number < 10)
{
    console.log(number);
    number++;
}

console.log("Loop has ended.");
```

Jetzt würde number sich nach jedem Durchlauf erhöhen. Konkret würde das folgenden Programmablauf bedeuten.

``` js
/*
 * Zeile 1: Number = 0;
 * Zeile 2: Schleife wenn Number (0) kleiner als 10 ist wahr
 * Zeile 3: Konsolenausgabe: 0
 * Zeile 4: Number um eins erhöhen, sprung zurück zu Zeile 2
 * Zeile 2: Schleife wenn Number (1) kleiner als 10 ist wahr
 * Zeile 3: Konsolenausgabe: 1
 * Zeile 4: Number um eins erhöhen, srung zurück zu Zeile 2
 * Zeile 2: Schleife wenn Number (2) kleiner als 10 ist wahr
 * Zeile 3: Konsolenausgabe: 2
 * ......
 * ......
 */
```

Bis wir dann irgendwann an den Punkt kommmen, wo number = 10 ist. Da 10 kleiner als 10 falsch ist, würde die Schleife abbrechen und die Konsole würde zur Konsolenausgabe "Loop has ended" kommen.

Heutzutage machen Schleifen für uns ganz automatisch das, was wir gerade so mühsam als Kommentar aufgeschrieben haben. Nämlich in verschiedene Zeilen hin und her springen ganz ohne das wir dies in unserem Quellcode genauer beschreiben müssen. In der Zeit "vor den Schleifen", musste man dies noch mühseelig mit sogenannten ´goTos´, also "spring zu" Befehlen machen. Wollte man also früher das Sequenzen sich eine bestimmte Anzahl wiederholen,sah der Quellcode deutlich mehr wie im Beispiel des Programmablaufs als Kommentar aus, als wie unsere bequeme While-Schreibweise.

Damit ist erstmal zu Schleifen im allgemeinen schon einiges gesagt. Jetzt also die Frage: 

## Welche Arten von Schleifen gibt es in JavaScript?

- while()
- for()
- forEach()
- for...of
- for...in
    
    **Hinweis**: for...in wird normalerweise für Objekte verwendet. Man kann ihn aber auch mit Arrays verwenden – dabei wird über die Indizes iteriert, nicht direkt über die Werte.

sind die wohl gängigsten. Wir nehmen uns einmal ein Beispiel für eine Schleife und passen die Schreibweise je nach Schleifentyp an. Die erwartete Ausgabe auf der Konsole entspricht dabei immer:

``` js
/*
 * 1
 * 2
 * 3
 * 4
 * 5
 * 6
 * 7
 * 8
 * 9
 * 10
 * loop has ended
 */ 
```

### while

``` js
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const length = numbers.length;
let counter = 0;

while(counter < length) {
    console.log(numbers[counter])
    counter++;
}

console.log("loop has ended");
```

### for

``` js
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

for (let i = 0; i < numbers.length; i++) {
    console.log(numbers[i]);
}

console.log("loop has ended");
```

### forEach

``` js
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

numbers.forEach(function(number) {
    console.log(number);
});

console.log("loop has ended");
```

### for...of

``` js
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

for (let number of numbers) {
    console.log(number);
}

console.log("loop has ended");
```

### for...in

``` js
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

for (let index in numbers) {
    console.log(numbers[index]);
}

console.log("loop has ended");
```

## Unterschiede, Vor- und Nachteile der verschiedenen Schleifenarten

Jetzt wo wir gesehen haben, wie verschiedene SChleife in JavaSCript syntaktisch funktionieren, stellt sich die berechtigte Frage:
**Wann nutze ich welche Schleife - und warum?**

### while

**Vorteile**
- Ideal, wenn die Anzahl der Schleifendurchläufe nicht im Voraus bekannt ist.
- Flexible Steuerung, besonders nützlich bei asynchronen Prozessen oder benutzerabhängigen Abbruchbedingungen.

**Nachteile**
- Höheres Fehlerpotenzial bei der Abbruchbedingung. Wird der Zähler z. B. nicht erhöht, kann es zu einer Endlosschleife kommen.
- Nicht immer auf den ersten Blick so klar lesbar wie for oder forEach.

**Typischer Einsatz**
- Warten auf ein bestimmtes Ereignis oder Bedingung.
- Polling-Mechanismen, Login-Überprüfung, dynamisches Nachladen.

### for

**Vorteile**
- Sehr gut geeignet, wenn man eine feste Anzahl an Durchläufen hat.
- Alle drei Schleifenkomponenten (Initialisierung, Bedingung, Inkrementierung) stehen direkt sichtbar in der Kopfzeile.
- Kompakt und leicht zu kontrollieren

**Nachteile**
- Kann bei komplexen Schleifenbedingungen unübersichtlich werden.
- Weniger "funktional", keine eingebauten Methoden wie forEach.

**Typischer Einsatz**
- Iteration über Arrays mit Indexzugriff.
- Wenn man Zugriff auf den Index selbst braucht (z. B. i % 2 === 0 für gerade Elemente).

### forEach

**Vorteile**
- Moderne, funktionale Schreibweise.
- Leserlich und sehr kurz, perfekt wenn man über jeden Eintrag in einem Array gehen möchte.
- Kein Risiko, die Schleife "versehentlich" endlos laufen zu lassen – sie läuft immer exakt einmal pro Element.

**Nachteile**
- Kann nicht mit break oder continue unterbrochen werden.
- Nur für Arrays bzw. Array-ähnliche Strukturen geeignet.

**Typischer Einsatz**
- Weniger performant als andere Schleifenarten, besonders bei großen Objekten.

**Typischer Einsatz**
- Iteration über die Schlüssel eines Objekts.
- Wenn du mit Objekten arbeitest und deren Eigenschaften dynamisch verarbeiten möchtest.- Weniger performant als andere Schleifenarten, besonders bei großen Objekten.

**Typischer Einsatz**
- Iteration über die Schlüssel eines Objekts.
- Wenn du mit Objekten arbeitest und deren Eigenschaften dynamisch verarbeiten möchtest.- Transformation oder Ausgabe von Array-Daten.
- Wenn du pro Element etwas tun möchtest – z. B. Werte ausgeben, formatieren, speichern.

### for...of

**Vorteile**
- Sehr leserlich, ähnlich wie forEach, aber mit break/continue-Unterstützung.
- Ideal für alle iterierbaren Datenstrukturen, also nicht nur Arrays, sondern auch Strings, Maps, Sets etc.

**Nachteile**
- Kein Zugriff auf den Index beim Durchlauf (außer man zählt manuell mit).

**Typischer Einsatz**
- Wenn du über Werte iterieren willst, ohne dich um Indizes kümmern zu müssen.
- Bei Datenstrukturen wie Arrays, Strings, Sets oder Maps, wenn du direkten Zugriff auf die Inhalte brauchst.
- Auch praktisch, wenn du continue oder break verwenden willst – was bei forEach nicht geht.

### for...in

**Vorteile**
- Speziell für das Iterieren über Objekte gedacht.ist.
- Gibt dir direkt Zugriff auf alle Property-Namen (Schlüssel) eines Objekts.

**Nachteile**
- Nicht ideal für Arrays – es wird über die Indizes als Strings iteriert, nicht direkt über die Werte.
- Die Iterationsreihenfolge ist bei Objekten nicht garantiert.
- Kann auch vererbte Eigenschaften aus der Prototyp-Kette mitnehmen, wenn man nicht mit hasOwnProperty filtert.

**Typischer Einsatz**
- Durchlaufen von Objekten mit dynamischen Keys.
- Wenn du die Namen der Eigenschaften brauchst, z. B. um sie auszugeben oder dynamisch zu verarbeiten.
