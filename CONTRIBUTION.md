# Setup

Im folgenden Abschnitt wird beschrieben, welche Bereiche des Projekts
wie erstellt bzw. bearbeitet werden können.

## User Stories

User Stories werden auf Github als Issues erstellt. In einem Comment
sollen die Tasks, die zur Erfüllung notwendig sind, aufgelistet sein.
Zusätzlich soll dem Issue ein Tag mit der Priorität zugewiesen werden.
Für eine Übersicht aller User Stories gibt es in der STORIES.md Datei
eine Tablle mit den folgenden Feldern:

-   **Issue** mit der Id des Githubissue als Link

-   **Name** mit dem Titel der Story

-   **Prio** mit der Priorität der Story (MH/SH/N2H)

-   **Points** mit dem zu erwartenden Aufwand

-   **Head** mit dem Verantwortlichen

-   **Status** mit dem aktuellen Zustand der Story

## Download the Code

Der Sourcecode für unser Projekt ist auf Github unter
<https://github.com/TGM-HIT/syt5-gek1051-mobile-application-dieliste> zu
finden. Das Repository kann mit folgendem Befehl heruntergeladen werden:

``` bash
git clone https://github.com/TGM-HIT/syt5-gek1051-mobile-application-dieliste
```

## Edit the Code

### IDE

Bei der Entwicklungsumgebung besteht freie Wahl. VS Code wäre eine
einfache Möglichkeit. Es ist lightweight und einfach zu bedienen.
Starten lässt sich VS Code über die Kommandozeile im root-Verzeichnis
des Projektes mit folgendem Befehl:

```
code . \# startet VS Code und öffnet das aktuelle Verzeichnis
```

### Dateistruktur {#setup:dateistruktur}

Die Wichtigsten Dateien für das Projekt sind folgende:

- **index.html** Hier wird die Struktur der Einkaufsliste festgelegt.

- **shoppinglist.js** Hier werden Funktionen definiert, die bei der Interaktion mit der Liste ausgeführt werden sollen.

- **shoppinglist.css** Hier wird das Aussehen der Einkaufsliste festgelegt.

Möchte man die Struktur der Weboberfläche ändern, muss man in der *index.html* Datei neue Bereiche erstellen bzw. vorhandene bearbeiten.

-   Ein Button könnte so aussehen:

    ```html
    <!-- back button -->
    <md-button class="md-icon-button" v-if="mode != 'itemedit'" v-on:click="onBack">
        <md-icon>arrow_back</md-icon>
    </md-button>
    ```

-   Ein Eingabefeld könnte so aussehen:

    ```html
    <!-- shopping item title -->
    <md-input-container>
        <md-input v-model="newItemTitle" placeholder="New item e.g. eggs" @keyup.enter.native="onAddListItem"></md-input>
    </md-input-container>
    ```

Die beiden besonderen Eigenschaften in den Tags werden von Vue
bereitgestellt.

-   **v-on:click** Hier kann angegeben werden, welche Methode beim
    Klicken eines Buttons ausgeführt werden soll. Alternativ zu *click*
    gibt es auch andere Events wie *change*.

-   **v-if** Hier kann eine Bedingung angegeben werden. Trifft diese zu,
    wird das Element angezeigt, anderenfalls nicht.

Möchte man die Struktur der Einkaufsartikel ändern, muss man in der
*shoppinglist.js* Datei die Konstante **sampleListItem** bearbeiten. Die
Struktur könnte wie folgt aussehen:

```js
// template shopping list item object
const sampleListItem = {
  "_id": "",
  "type": "item",
  "version": 1,
  "title": "",
  "amount": "",
  "checked": false,
  "createdAt": "",
  "updatedAt": ""
};
```

Möchte man ein Funktion hinzufügen, muss man in der *shoppinglist.js*
Datei im Bereich **methods** der Veriable **app** die Funktion einfügen.
Hier ist der Beginn des methods-Bereich als Beispiel:

```js
methods: {
    /**
     * Called when the settings button is pressed. Sets the mode
     * to 'settings' so the Vue displays the settings panel.
     */
    onClickSettings: function() {
      this.mode = 'settings';
    },
    /**
     * Called when the about button is pressed. Sets the mode
     * to 'about' so the Vue displays the about panel.
     */
    onClickAbout: function() {
      this.mode = 'about';
    },
    //...
}
```

Kommentare wären leiwand.

## Run the Code

Um das Programm für die Einkaufsliste zu starten, werden im
root-Verzeichnis des Projekts über die Kommandozeile folgende Befehle
ausgeführt:

```bash
npm install # um notwendige npm-Pakete zu installieren
npm start # um das Programm zu starten
```

Anschließend ist die Einkaufsliste unter *localhost:8081* erreichbar.

## Testing

Für End 2 End Tests wird Cypress verwendet. [1]

Installation:
```bash
cd /project-root
npm install cypress --save-dev
# --save-dev damit cpyress als dev-dependency installiert wird -> bei productions builds nicht mehr inkludiert
```

Ausführen:
```bash
npx run cypress open
```

Für einheitliches Starten der Bereiche des Projekts wurde ein npm Script erstellt
```js
{
    "scripts": {
        "capress:open": "cypress open"
    }
}
```

Cypress kann nun auch so gestartet werden:
```bash
npm run cypress:open
```

*Nimmt sich nicht viel zum anderen Command*

Für jede User Story sollte mindestens 1 Test erstell werden.
Die wesentlichen Punkt, die hierbei zu beachten sind, sind hier zu finden: [1, 2]

### Quellen
- [1]: Writing Your First E2E Test; visited 31.03.2023; [online](https://docs.cypress.io/guides/end-to-end-testing/writing-your-first-end-to-end-test)
- [2]: Cypress Kitchen Sink; visited 31.03.2023; [online](https://example.cypress.io/)