
# JavaScript Basics für React.js – Dein Einstieg ins Programmieren

## 1. Was ist JavaScript?

JavaScript (JS) ist eine Programmiersprache, die hauptsächlich für die Entwicklung von interaktiven Webseiten genutzt wird. In Kombination mit HTML (Struktur) und CSS (Design) sorgt JavaScript für dynamische Inhalte.

**Brücke zu React**: React.js ist eine JavaScript-Bibliothek, die das Entwickeln von Benutzeroberflächen (UI) vereinfacht. Bevor du React lernst, musst du verstehen, wie JavaScript funktioniert!

## 2. Dein erstes JavaScript-Programm

Bevor wir loslegen, kannst du JavaScript direkt in deinem Browser ausprobieren.

**JavaScript in der Konsole ausführen**

1. Öffne den Browser (z. B. Chrome oder Firefox).
2. Klicke mit Rechtsklick auf eine beliebige Webseite und wähle "Untersuchen".
3. Öffne den "Konsole"-Tab.
4. Gib folgenden Code ein und drücke Enter:

```js
console.log("Hallo Welt!");
```

Du solltest jetzt den Text "Hallo Welt!" in der Konsole sehen!

**Echtwelt-Beispiel**: Bei einer Website für Online-Shopping könntest du eine Bedingung verwenden, um zu prüfen, ob ein Benutzer das Mindestalter für den Kauf eines Produkts erreicht hat.
**Brücke zu React**: In React wirst du oft die Konsole nutzen, um Fehler zu finden oder zu verstehen, was im Code passiert.

## 3. Variablen – Werte speichern

Variablen sind Speicherplätze für Daten. In JavaScript gibt es drei Möglichkeiten, Variablen zu erstellen:

```js
let name = "Lisa";  // kann später geändert werden
const alter = 25;   // bleibt konstant
var stadt = "Berlin"; // veraltet, besser nicht nutzen
```

**Erklärung:**

- `let`: Kann geändert werden.
- `const`: Bleibt immer gleich (wichtig in React!).
- `var`: Altmodisch, nicht mehr empfohlen.

**Brücke zu React**: In React nutzen wir oft `const` für Dinge, die sich nicht ändern sollen, z. B. UI-Elemente.

## 4. Datentypen – Welche Werte gibt es?

JavaScript hat verschiedene Arten von Daten:

| Typ        | Beispiel                  |
|------------|---------------------------|
| String     | "Hallo Welt"              |
| Number     | 42, 3.14                  |
| Boolean    | true, false               |
| Array      | ["Apfel", "Banane"]       |
| Object     | {name: "Lisa", alter: 25} |
| Null       | null                      |
| Undefined  | undefined                 |

**Brücke zu React**: In React arbeiten wir viel mit Objekten und Arrays, z. B. um Daten in Komponenten zu speichern.

## 5. Bedingungen – Code basierend auf einer Bedingung ausführen

```js
let alter = 18;

if (alter >= 18) {
    console.log("Du darfst fahren!");
} else {
    console.log("Du bist zu jung.");
}
```

**Erklärung:**

- `if`: Prüft eine Bedingung.
- `else`: Führt den Code aus, wenn die Bedingung nicht erfüllt ist.

**Brücke zu React**: In React nutzen wir Bedingungen, um Inhalte auf der Webseite zu zeigen oder zu verstecken.

## 6. Schleifen – Wiederholende Aufgaben automatisieren

### for-Schleife

```js
for (let i = 0; i < 5; i++) {
    console.log("Nummer: " + i);
}
```

### while-Schleife

```js
let count = 0;
while (count < 5) {
    console.log("Zähler: " + count);
    count++;
}
```

### forEach für Arrays

```js
const namen = ["Lisa", "Tom", "Anna"];
namen.forEach(name => console.log("Hallo " + name));
```

**Echtwelt-Beispiel**:
- *for*: Eine Schleife, die alle Artikel in einem Warenkorb ausgibt.
- *while*: Eine Schleife, die eine Anzahl von Seiten lädt, bis alle angezeigt wurden.
- *forEach*: Eine Schleife, die alle Teilnehmer eines Events begrüßt.
**Brücke zu React**: In React nutzen wir oft Schleifen, um Listen von Elementen anzuzeigen.

## 7. Funktionen – Wiederverwendbarer Code

### Klassische Funktionen

```js
function begruessen(name) {
    return "Hallo " + name + "!";
}
console.log(begruessen("Lisa"));
```

### Arrow Functions – Die moderne Alternative

```js
const begruessen = (name) => `Hallo ${name}!`;
console.log(begruessen("Lisa"));
```

**Warum Arrow Functions?**

- Kürzer und lesbarer.
- Behalten den `this`-Kontext, was besonders in React nützlich ist.
- Ideal für Callbacks und funktionale Programmierung.

**Echtwelt-Beispiel**: Eine Funktion, die das Alter eines Benutzers überprüft und eine Nachricht zurückgibt, ob er alt genug ist.
**Brücke zu React**: In React werden Arrow Functions oft für Event-Handler und Callbacks verwendet, z. B. wenn ein Button geklickt wird.

## 8. Wichtige Array-Methoden

### map – Elemente transformieren

```js
const zahlen = [1, 2, 3];
const quadrate = zahlen.map(num => num * num);
console.log(quadrate); // [1, 4, 9]
```

### filter – Elemente herausfiltern

```js
const zahlen = [10, 15, 20, 25];
const groesserAls15 = zahlen.filter(num => num > 15);
console.log(groesserAls15); // [20, 25]
```

### reduce – Werte zusammenfassen

```js
const zahlen = [1, 2, 3, 4];
const summe = zahlen.reduce((acc, num) => acc + num, 0);
console.log(summe); // 10
```
**Echtwelt-Beispiel**:
- *map*: Wenn du eine Liste von Preisen hast und diese mit einem Rabatt berechnen möchtest.
- *filter*: Wenn du nur Produkte anzeigen möchtest, die einen Preis über einem bestimmten Wert haben.
- *reduce*: Um die Gesamtsumme der Produkte im Warenkorb zu berechnen.
**Brücke zu React**: Diese Methoden sind extrem wichtig für das Arbeiten mit Listen und Daten in React.

## 9. String-Typen und Template Literals

In JavaScript gibt es mehrere Möglichkeiten, Strings zu definieren:

1. **Einfaches Anführungszeichen (`''`)**:
   - Wird häufig verwendet, wenn keine Variablen oder Ausdrücke eingebaut werden müssen.
   - Beispiel: 
     ```js
     let name = 'Lisa';
     console.log('Hallo ' + name);
     ```

2. **Doppelte Anführungszeichen (`""`)**:
   - Diese werden oft in HTML-Attributen verwendet und sind für Strings, die keine besonderen Anforderungen haben, geeignet.
   - Beispiel:
     ```js
     let stadt = "Berlin";
     console.log("Willkommen in " + stadt);
     ```

3. **Template Literals (Backticks `` ` ``)**:
   - Ermöglichen die einfache Einbettung von Variablen und Ausdrücken in den String.
   - Vorteil: Bessere Lesbarkeit und einfacher für komplexe Strings mit Variablen.
   - Beispiel:
     ```js
     let alter = 25;
     console.log(`Ich bin ${alter} Jahre alt.`);
     ```

**Wann sollte man was verwenden?**

- **`''` und `""`** sind für einfache Strings gut geeignet.
- **Template Literals** sind besonders nützlich, wenn du Variablen oder Ausdrücke in den String einfügen möchtest. Sie sind in React von großem Nutzen, z. B. bei der Arbeit mit JSX.

**Brücke zu React**: In React werden häufig Template Literals verwendet, besonders wenn wir mit dynamischen Werten in JSX arbeiten.

## 10. Übergabeparameter und komplexe Objekte

### Übergabeparameter

In JavaScript können Funktionen auch Parameter entgegennehmen, um Daten zu verarbeiten.

```js
function begruessen(name) {
    return `Hallo ${name}!`;
}
console.log(begruessen("Lisa"));
```

### Arrays als Parameter

Du kannst auch Arrays an Funktionen übergeben:

```js
function summeZahlen(zahlen) {
    return zahlen.reduce((acc, num) => acc + num, 0);
}
console.log(summeZahlen([1, 2, 3])); // 6
```

### Objekte als Parameter

Funktionen können auch Objekte empfangen, um komplexe Daten zu verarbeiten:

```js
function beschreibung(person) {
    return `${person.name} ist ${person.alter} Jahre alt und kommt aus ${person.stadt}.`;
}

let person = {name: "Lisa", alter: 25, stadt: "Berlin"};
console.log(beschreibung(person));
```

### Verschachtelte Parameter

Du kannst auch verschachtelte Objekte und Arrays an Funktionen übergeben:

```js
function personInfo(person) {
    return `Name: ${person.name}, Alter: ${person.alter}, Adresse: ${person.adresse.stadt}`;
}

let person = {name: "Lisa", alter: 25, adresse: {stadt: "Berlin", strasse: "Musterstr. 1"}};
console.log(personInfo(person)); // Name: Lisa, Alter: 25, Adresse: Berlin
```
**Echtwelt-Beispiel**:
- Übergabe eines Arrays: Wenn du eine Liste von Bestellungen an eine Funktion übergibst, um sie zu sortieren oder zu filtern.
- Übergabe eines Objekts: Ein Benutzerobjekt wird an eine Funktion übergeben, die dann die Profilinformationen anzeigt.
- Verschachtelte Parameter: Wenn du eine vollständige Adresse an eine Funktion übergibst, die diese für ein Versandetikett verwendet.
**Brücke zu React**: In React werden oft komplexe Objekte und Arrays an Komponenten übergeben, besonders bei der Arbeit mit Formularen oder API-Daten.
