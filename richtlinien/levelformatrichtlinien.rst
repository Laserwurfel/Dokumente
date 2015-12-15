Grober Überblick
----------------

Das Level wird in der Definition in drei Teile geteilt. Im ersten Teil werden
alle Metainformationen, im zweiten Teil wird das Aussehen und im dritten die
Logik festgelegt.

Metainformationen
-----------------

Diese werden als Key-Value Paare angegeben. Der Key wird von der Value durch
einen Doppelpunkt (``:``) getrennt. Die Value kann einer der folgenden
Datentypen sein:

``string``
    Beginnt und endet mit einem Anführungszeichen (``"``)

``path``
    Beginnt mit Punkt-Slash (``./``) um den aktuellen Ordner zu denotieren.
    Order werden im Unix-Style mit einem Forwardslash (``/``) getrennt.

Folgende Keys sind verpflichtend:

``title``
    Der Name des Levels als ``string``

``track``
    Der Dateiname für die Musik als ``path``

Aussehen
--------

Beschrieben werden in diesem Teil die Dekorationen. Die Art der Dekoration wird
durch ein Zeichenpaar festgelegt, und die Position direkt auf einem
aufgeklappten ASCII-Würfel. Folgende Dekorationen sind definiert:

``[]``
    Haus

``@@``
    Baum

``%%``
    Tierherde

``##``
    Getreidefeld

Der Würfel wird so aufgeklappt, dass die hintere Seite am Ende ganz rechts
außen liegt. Jede Fläche hat 9x9 Positionen für Dekorationen, wobei jede Spalte
2 Zellen breit ist, weil eine Zelle circa doppelt so hoch wie breit ist. Um die
Fläche herum werden die Kanten mit Pipe (``|``) und zwei Bindestrichen (``--``)
gezeichnet.  Verdbindungspunkte werden mit einem großen ``O`` oder, bei Punkten
in der Mitte einer Spalte, mit Klammern ``()`` dargestellt.

Aufbau
------

Jeder Verbindungspunkt ist eindeutig durch seine anliegenden Flächen
ansprechbar. Die Flächen werden in der Reihenfolge Front/Back, Left/Right,
Up/Down angegeben und mit Unterstrich (``_``) getrennt.

Um Operationen auf Punkten vorzunehmen wird zuerst das Symbol der Operation und
danach die benötigte Anzahl der Punkten geschrieben. Folgende Operatoren sind
definiert:

``* source goal``
    Macht eine Laserquelle aus dem ersten Punkt und das dazugehörige Ziel aus
    dem zweiten.

``! point``
    Deaktiviert diesen Punkt.

``-- from to``
    Erstellt eine fixe Verbindung zwischen den Punkten.

``[] block_from block_to [switch_from switch_to]...``
    Blockiert Verbindungen zwischen den ersten Punktepaar, außer mindestens
    einer der Schalter zwischen allen weiteren Punktepaaren hat eine Verbindung
    auf sich.  Wenn eine Blockade öfters, aber mit verschiedenen Schaltern,
    platziert wird, muss jeder Schalter betätigt werden um die Blockade zu
    öffnen.

``% from to``
    Erstellt einen "Teleporter", eine fixe Verbindung zwischen den Punkten, die
    auch durch den Würfel gehen kann.

Alle leere Zeilen und Zeilen die mit einer Raute (``#``) beginnen, werden
ignoriert.

Beispiel
--------

Der genaue Aufbau des Würfels wo die Flächen benannt sind.::

                     O--------()--------O
                     |                  |
                     |                  |
                     |                  |
                     |                  |
                     O        up        O
                     |                  |
                     |                  |
                     |                  |
                     |                  |
  O--------()--------O--------()--------O--------()--------O--------()--------O
  |                  |                  |                  |                  |
  |                  |                  |                  |                  |
  |                  |                  |                  |                  |
  |                  |                  |                  |                  |
  O       left       O      front       O      right       O       back       O
  |                  |                  |                  |                  |
  |                  |                  |                  |                  |
  |                  |                  |                  |                  |
  |                  |                  |                  |                  |
  O--------()--------O--------()--------O--------()--------O--------()--------O
                     |                  |
                     |                  |
                     |                  |
                     |                  |
                     O       down       O
                     |                  |
                     |                  |
                     |                  |
                     |                  |
                     O--------()--------O

Alle Punkte auf der "Front" Fläche::

  front_left_up
  front_up
  front_right_up
  front_left
  front_right
  front_left_down
  front_down
  front_right_down

  -- front_right right_down
  -- right_down front_down
  -- front_down front_right

  ! front_right_down
