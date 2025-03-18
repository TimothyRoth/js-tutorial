# JavaScript Basics für React.js – Dein Einstieg ins Programmieren

## 1. Was ist JavaScript?
JavaScript (JS) ist eine Programmiersprache, die hauptsächlich für die Entwicklung von interaktiven Webseiten genutzt wird. In Kombination mit **HTML** (Struktur) und **CSS** (Design) sorgt JavaScript für dynamische Inhalte.

> **Brücke zu React:** React.js ist eine JavaScript-Bibliothek, die das Entwickeln von Benutzeroberflächen (UI) vereinfacht. Bevor du React lernst, musst du verstehen, wie JavaScript funktioniert!

---

## 2. Dein erstes JavaScript-Programm
Bevor wir loslegen, kannst du JavaScript direkt in deinem Browser ausprobieren.

### JavaScript in der Konsole ausführen
1. Öffne den Browser (z. B. Chrome oder Firefox)
2. Klicke mit **Rechtsklick** auf eine beliebige Webseite und wähle **Untersuchen**
3. Öffne den **Konsole-Tab**
4. Gib folgenden Code ein und drücke **Enter**:
   ```js
   console.log("Hallo Welt!");
   ```
5. Du solltest jetzt den Text "Hallo Welt!" in der Konsole sehen!

> **Brücke zu React:** In React wirst du oft die Konsole nutzen, um Fehler zu finden oder zu verstehen, was im Code passiert.

---

## 3. Variablen – Werte speichern
```js
let name = "Lisa";  // kann später geändert werden
const alter = 25;   // bleibt konstant
var stadt = "Berlin"; // veraltet, besser nicht nutzen
```

> **Brücke zu React:** In React nutzen wir oft `const` für Dinge, die sich nicht ändern sollen, z. B. UI-Elemente.

---

## 4. Arrays & Objekte dekonstruieren
### Arrays dekonstruieren
```js
const farben = ["Rot", "Grün", "Blau"];
const [ersteFarbe, zweiteFarbe] = farben;
console.log(ersteFarbe); // "Rot"
```

### Objekte dekonstruieren
```js
const person = { name: "Lisa", alter: 25 };
const { name, alter } = person;
console.log(name); // "Lisa"
```

> **Brücke zu React:** In React dekonstruieren wir oft Props, um sie in Komponenten einfacher zu nutzen.

---

## 5. Imports und Exports
### Export
```js
export const hallo = "Hallo Welt";
export function sagHallo() {
    return "Hallo aus der Funktion";
}
```

### Import
```js
import { hallo, sagHallo } from "./meineDatei.js";
console.log(hallo);
console.log(sagHallo());
```

> **Brücke zu React:** In React nutzen wir `import` und `export`, um Komponenten und Funktionen zu organisieren.

---

## Fazit & Ausblick auf React.js
Herzlichen Glückwunsch! 🎉 Du hast die JavaScript-Grundlagen gelernt. Diese Konzepte helfen dir enorm, wenn du mit React anfängst. 

### Nächste Schritte:
- Installiere **Node.js**
- Erstelle dein erstes **React-Projekt** mit `npx create-react-app mein-projekt`
- Lerne **JSX** (eine Mischung aus HTML & JavaScript)

Viel Erfolg beim Coden! 🚀
