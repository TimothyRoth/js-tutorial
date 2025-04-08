# JavaScript Arrays

## Einführung

Arrays sind ein wichtiger Datentyp den wir Software-Entwickler für unsere tägliche Arbeit benötigen. In den meisten Anwendungen bekommen wir von APIs oder Datenbanken `responses ` welche verschiedene Objekte verschachtelt in einem Array speichern. Aber auch innerhalb von Objekten sind die Werte (values) einzelner Schlüssel (keys) häufig arrays.

Ein Array in JavaScript orientiert sich an der syntax (Schreibweise) der meisten **C-Orientierten** Programmiersprachen. **C** ist eine der älteren und wichtigsten Programmiersprachen unserer Zeit.

```js
let numbers = [1, 2, 3];
```

Was du hier siehst ist ein veränderbares `array` numbers. Veränderbar, weil wir es mit dem `let` und nicht dem `const` keyword deklariert haben. Den Unterschied zu verstehen ist wichtig. Es gibt einige Dinge (Operationen oder auch Methoden) in JavaScript die wir mit unserem numbers array tun können. Manche verändern das array nachhaltig, andere widerrum erzeugen nur einen neuen Rückgabewert. Das vertiefen wir später weiter.

Um eine Methode in JavaScript auf ein Array anwenden zu können, wird in der der Regel folgendes Schema angewendet:

```js
numbers.Methode();
```

Ein wenig weiter unten stelle ich dir eine Liste mit den wichtigsten Methoden welche du in JavaScript zur Verfügung hast, aber `Achtung Spoiler!!!` ... Niemand kennt alle Methoden auswendig und niemand verlangt das. Generell ist es ein allgemeiner Irrglaube, dass es entscheidend wäre den größten Teil einer Programmiersprache auswendig zu können. Viel wichtiger ist, dass du ein Gefühl für die Sprache entwickelst und eine relativ genaue Idee davon hast, was du tun willst und was möglich ist. Du kannst dann beispielsweise deine Idee erst ausformulieren und dann später bei Unsicherheiten mit Hilfe von Google, LLM`s und Co. zu funktionalem Code umwandeln. Zudem kann ein LLM wie beispielsweise ChatGPT einen prompt viel besser verarbeiten, wenn du den logischen Ablauf deines Programms bereits ausgearbeitet hast.

Beispiel:

```js
/*
 * neue Variable: result
 * für jedes Element im Array
 *      neue Variable: number
 *      addiere number zum result hinzu
 * ende Schleife
 *
 * Ausgabe auf der Konsole von result
 */
```

So könnte beispielsweise dein Pseudo-Code aussehen um jede Zahl im Array numbers zu einem Ergebnis aufzuaddieren.

```js
let result = 0;

numbers.forEach((number) => {
  result += number;
});

console.log(result);
```

Wäre eine von vielen Möglichkeiten diese Aufgabe umzusetzen. Ja genau `viele` ist ein gutes Stichwort. Sei dir über eines bewusst: Es gibt immer mindestens 10 Arten das selbe Problem zu lösen und nicht immer (aber manchmal) ist nur eine davon die richtige. Unser eben aufgezeigtes Beispiel hätte man auch wunderbar mit der `reduce()` Methode lösen können, aber nicht müssen. Generell gilt es als Software-Entwickler aber immer folgene Reihenfolge einzuhalten:

1. Funktionales Ergebnis erzielen
2. Das am besten optimierteste, idealste Ergebnis erzielen

Und dabei muss `2.` noch nicht einmal zwangläufig stattfinden. Es kommt immmer darauf an was dein Ziel ist. Möchtest du etwas lernen, solltest du immer so viel wie möglich mit einem Code herumspielen und experimentieren. Hast du einen Job zu erledigen, eventuell auch unter Zeitdruck, dann fällt dieser Punkt meistens weg. Allerdings ist es eine gängige Praxis unter uns Entwicklern, bereits geschriebenen und **funktionierenden** Code nachträglich zu verbesseren. Diesen Vorgang nennt man `Refactoring`. Die Gründe dafür sind vor allem eine bessere _Wartbarkeit_ und _Skalierbarkeit_. Umso wartbarer und skalierbarer eine Anwendung ist, desto länger ist diese auch im Einsatz.

Schauen wir uns trotzdem einmal an wie eine Lösung mit der reduce Methode ausgesehen hätte:

```js
let result = numbers.reduce((acc, number) => acc + number, 0);
console.log(result);
```

Okay halt stop :D. Ist das jetzt besser? Also für einen Anfänger bestimmt nicht, denn hier passiert ne ganze Menge. Erstmal werden hier ein haufen `shorthands` (verkürzte schreibweisen) verwendet, die einen verwirren können, wenn man diese nicht kennt. Ich weiß in diesem Kapitel soll es vor allem um die Array-Methoden in JavaScript gehen, allerdings kommen wir in diesem Zusammenhang nicht umher, uns auch mit einigen dieser "Kurzschreibweisen" auseinanderzusetzen, vor allem da diese uns immer wieder begegnen werden.

Nehmen wir also das Beispiel einmal Stück für Stück auseinander.

1. Rückgabewert

   Da die reduce() Methode einen Wert als finales Ergebnis zurückgibt, können wir dieses Ergebnis einer Variable zuordnen.

   ```js
   let result = numbers.reduce(); // numbers.reduce hat einen Rückgabewert
   ```

2. Funktionen (callback) als Eingabeparameter für eine Funktion.

   Was auf den ersten Blick vielleicht nicht direkt ersichtlich wird ist, dass wir in die reduce Methode zwei Parameter hinzugeben.

   ```js
   numbers.reduce(parameter1, parameter2);
   ```

   Bei diesen Parametern handelt es sich um eine Funktion, sowie den Initialwert des Rückgabewerts, bevor dieser Initialwert um den Wert dann erweitert wird.

   ```js
   numbers.reduce(Funktion(), Initialwert);
   ```

   Das ganze wird deutlicher wenn wir einmal mit einem echten Beispiel arbeiten:

   ```js
   let numbers = [1, 2, 3]; // Deklaration eines Arrays bestehend aus 3 Zahlen.

   let result = numbers.reduce(() => {
     // result = Initialwert (in diesem Fall 0) + das was in jeder Schleife der reduce Funktion hinzukommt.
     // Code ...
     return 0;
   }, 0);
   ```

   Also in diesem Fall haben wir den Initialwert auf 0 gesetzt. So wie viele Array-Methoden, wird auch reduce iterativ, sprich also wie ein Loop, auf jedes Element welches sich im Array befindet ausgeführt. Der Rückgabewert unserer `anonymen Funktion`, auch Lamba-Ausdruck genannt, wird dann einfach zu dem Initialwert hinzugefügt. In dieser Implementierung würden wir nun konkret für jedes Element im Array, also 3 mal 0 zum Initialwert 0 hinzufügen. Sprich `result` wäre am Ende 0. Was wir in diesem Beispiel erreichen wollen ist, für jedes Element im Array den Wert mal 2 zu nehmen und diesen dann zum Initialwert aufzuaddieren. Da die Werte im Array 1, 2 und 3 sind, sollte die Rechnung also 2 \* 1 + 2 \* 2 + 2 \* 3 sein, was dem Ergebnis 11 entsprechen würde. Innerhalb der reduce Methode haben wir Zugriff auf 2 Parameter. Den Akkumulator und den aktuellen Wert im Array durch den wir gerate durchiterieren.
   Akkumulator beschreibt dabei so etwas wie einen Aggregatszustand, also den aktuellen Wert des **Initialzustands**, in unserem Fall also anfänglich die Zahl 0. Dieser ändert sich dann aber für jede Iteration / Durchgang um den Rückgabewert der von uns implementierten Funktion.

   Gehen wir im folgenden eimal davon aus, wir befinden uns im ersten Durchgang, sprich also numbers[0], was gleich der Zahl 1 entspricht. Dann würde aus

   ```js
   let result = numbers.reduce((Akkumulator, WertImArray) => {
     return Akkumulator + WertImArray * 2;
   }, 0);
   ```

   wenn wir die Variablen mit den echten Werten ersetzen:

   ```js
   let result = numbers.reduce((Akkumulator, WertImArray) => {
     return 0 + 1 * 2; // 1
   }, 0);
   ```

   Im zweiten Durchgang befände sich dann der Akkumulator auf den Wert 1 da er das **Zwischenergebnis** für jeden Durchgang repräsentiert bzw. speichert. Er **verändert** sich also pro Durchgang:

   ```js
   let result = numbers.reduce((Akkumulator, WertImArray) => {
     return 1 + 2 * 2; // 5
   }, 0);
   ```

   und letzlich:

   ```js
   let result = numbers.reduce((Akkumulator, WertImArray) => {
     return 5 + 3 * 2; // 11
   }, 0);

   console.log("Ergebnis ist = " + result); //  Ergebnis ist = 11
   ```

   Um das mit dem Initialwert noch einmal deutlich zu machen. Hätten wir diesen am Anfang auf beispielsweise 11 gesetzt und nicht auf 0, dann wäre das Ergebnis jetzt 22, da wir mit der Zahl 11 angefangen hätten und die Rechnung dann 11 + 1 \* 2 + 2 \* 2 + 3 \* 2 gewesen wäre.

3. Eine Funktion in der Schreibweise verkürzen

   Wie kommen wir jetzt zu der Kurzschreibweise wie im ersten Beispiel der "optimierten" Variante. Wenn wir nur eine Zeile in unserem Funktionsbody (das ist alles das was zwischen den geschweiften Klammern `{}` steht) haben, können wir die geschweiften Klammern weglassen und alles in eine Zeile schreiben.

   Aus:

   ```js
   let result = numbers.reduce((Akkumulator, WertImArray) => {
     return Akkumulator + WertimArray;
   }, 0);
   ```

   wird dann:

   ```js
   let result = numbers.reduce((Akkumulator, WertImArray) => return Akkumulator + WertImArray, 0);
   ```

   Wenn ich dann jetzt noch Abkürzungen für die Worte Akkumulator und WertImArray benutze welche Standardmäßig acc für Akkumulator und ein Name passend zu einem einzelnen Wert in unserem Array, also in diesem Fall number, verwenden:

   ```js
   let numbers = [1, 2, 3];
   let result = numbers.reduce((acc, number) => return acc + number, 0);
   ```

   Kurz gesagt: Wenn man nur eine Zeile im Funktionsbody hat, kann man geschweifte Klammern weglassen.

**Fazit**
Letzlich lassen sich alle Array-Methoden ähnlich verwenden. Es ist ein wenig gewöhnungsbedürftig auf _magische_ Art Zugriff auf Parameter in von uns definierten callbacks zu haben die wir nicht selbst definiert haben, wie im obigen Beispiel _acc_ und _number_. Die Antwort dazu liegt in den teilweise komplexen Implementierungen der Methoden welche wir verwenden. Momentan würde eine detaillierte Erklärung jedoch deutlich den Rahmen sprengen. Mit der Zeit werden diese noch neuen Konzepte immer klarer und verständlicher. Für jetzt ist aber erstmal wichtig das du verstehst wie man diese Methoden benutzt, nicht wie sie im Detail funktionieren. Betrachte sie als Werkzeug. Nicht jedes Werkzeug welches du in der echten Welt benutzt hast du zu 100% im Detail verstanden und das ist auch vollkommen in Ordnung. Genau so ist es in der Software-Entwicklung auch.

Zu guter letzt hier einmal die versprochene Liste der wichtigsten Array-Methoden in JavaScript:

### Iteration / Transformation

- foreach() – führt eine Funktion für jedes Element aus
- map() – erstellt ein neues Array mit den Rückgabewerten
- filter() – erstellt ein neues Array mit gefilterten Elementen
- reduce() – reduziert das Array auf einen einzelnen Wert
- join() – verbindet alle Elemente zu einem String

### Suchen und Prüfen

- find() – gibt das erste passende Element zurück
- findIndex() – gibt den Index des ersten passenden Elements zurück
- some() – prüft, ob mindestens ein Element eine Bedingung erfüllt
- every() – prüft, ob alle Elemente eine Bedingung erfüllen
- includes() – prüft, ob ein bestimmter Wert vorhanden ist
- indexOf() – gibt den Index eines Werts zurück (oder -1)
- lastIndexOf() – wie indexOf(), aber rückwärts

### Hinzufügen und Entfernen

- push() – fügt am Ende hinzu
- pop() – entfernt das letzte Element
- unshift() – fügt am Anfang hinzu
- shift() – entfernt das erste Element
- splice() – fügt an beliebiger Stelle ein, entfernt oder ersetzt
- slice() – erstellt eine Kopie eines Ausschnitts (nicht destruktiv)
- concat() – verbindet Arrays

### Sortieren und Umkehren

- sort() – sortiert Elemente (Achtung: verändert Original)
- reverse() – kehrt die Reihenfolge um
