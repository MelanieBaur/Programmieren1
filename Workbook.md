<!--
author: Melanie Baur, Sebastian Speiser and further professors and students of HFT Stuttgart, contact: melanie.baur@hft-stuttgart.de, sebastian.speiser@hft-stuttgart.de
language: de
version: 1.0
narrator: Deutsch Female
mode: Textbook

comment: Vorlesung Programmieren 1 und 2 an der HFT Stuttgart der Bachelor-Studiengänge Informatik und Wirtschaftsinformatik

import: https://raw.githubusercontent.com/liascript/CodeRunner/master/README.md

-->
# Programmieren 1 und 2 in Java
<article>
Dieses Online-Buch wird entwickelt an der Hochschule für Technik Stuttgart und dient der Einführung in die Programmierung mit Java zunächst in den Studiengängen Informatik und Wirtschaftsinformatik im 1. und 2. Semester. Es werden somit keine Vorkenntnisse im Programmieren vorausgesetzt. Das Buch befindet sich gerade im Aufbau und wird laufend ergänzt und verbessert. Die Inhalte des 1. Semesters sind Stand Juli 2024 im Buch inkludiert in einer 1. Version. Die Inhalte des 2. Semesters werden zum Wintersemester 24/25 ergänzt.

Als Arbeitsweise wird für die Teilnehmenden der oben genannten Vorlesungen vorgeschlagen, jede Woche ein Kapitel durchzuarbeiten inkl. der zur Verfügung stehenden Programmieraufgaben. Der geschätze Zeitaufwand beträgt ohne Vorkenntnisse pro Woche 16 Stunden. Hiervon werden 6 Stunden an der Hochschule erbracht, ein:e Professor:in und/oder ein:e Assistent:in stehen hierbei für Fragen zur Verfügung. 10 Stunden sollen selbständig absolviert werden.

Lesen Sie gerne ein "echtes" Buch? So empfehlen wir die Lektüre von Philipp Ackermann: Schrödinger programmiert Java, Rheinwerk. Sie finden dieses Buch als eBook in der HFT Bibliothek.

Die wichtigsten Informationen finden Sie aber in diesem Online-Buch. Dieses besteht nicht nur aus Text, sondern auch aus Links zu externen Webseiten. Für diese übernehmen wir keinerlei Haftung. Weiterhin gibt es natürlich viele Code-Beispiele. Diese können Sie direkt im Online-Buch ausführen. 

Zum Beispiel ist das folgende ein Programm-Code, bei dem etwas auf der Konsole ausgegeben wird.

```java
class HalloWelt{
    public static void main(String args[]){
        System.out.println("Hallo Welt");
    }
}
```
@LIA.java(HalloWelt)

Klicken Sie nun auf </> im kleinen Kreis unter der Code-Zeile, so wird der Code ausgeführt und Sie sehen im schwarzen Kästchen, das dann erscheint, das Ergebnis.

</article>

Natürlich sollen Sie nicht nur lesen, sondern insbesondere auch viel selbst machen. Hier kommt die erste Aufgabe.

>**Aufgabe**

Geben Sie nun statt "Hallo Welt" einen anderen Text zwischen den Anführungszeichen ein. Führen Sie den Code erneut aus. Was fällt Ihnen auf?

Auf der rechten Seiten unterhalb des Codes, können Sie nun mit den Pfeilen zwischen den verschiedenen Codes hin- und herwechseln. Gehen Sie mit dem Pfeil nach links zurück auf den ursprünglichen Code und dann mit dem Pfeil nach rechts wieder zu Ihrem neuen Code.


>**Übungen**

Um viel zu üben, denn das ist das wichtigste beim Programmieren, werden [hier](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) zu jedem Kapitel Übungen bereit gestellt. Sie werden im Laufe des Buchs immer wieder zu diesen Übungen aufgefordert. Führen Sie die Aufgaben gewissenhaft aus. Bei Problemen fragen Sie einfach in der nächsten Mentoringstunde. 



## Einführung 
Eine Programmiersprache zu lernen, ist unabdingbare Voraussetzung für eine Tätigkeit in der Informatik, z.B. als Entwickler, Projektleiter, Softwarearchitekt, denn die Computer führen exakt den Code aus, den sie vorgesetzt bekommen und die Compiler übersetzen genau das was im Programmtext steht in Maschinencode. 

Sie als Programmierer:

* Analysieren Probleme
* Überlegen sich Lösungen
* Übersetzen Lösungen in Programmtext
Der Computer ist nicht kreativ und findet keine Lösungen. Dafür gibt es die glorreiche Tätigkeit des Programmierens.

Um dies zu können, müssen Sie viel üben:

* Kennen Sie einen Trainer der Bundesliga, der nicht Profi-Fußballer war? 
* Haben Sie Schwimmen oder Radfahren aus Büchern erlernt? 
* Sind Sie zur praktischen Fahrprüfung erstmals Auto gefahren?
* Wie viele Jahre hat ein Musiker vor dem ersten Klavierkonzert geübt?

Was könnte Beispiele für kleine Programme sein?

* Zwei Zahlen addieren
* Eine Zahl abspeichern
* Eine Zahl laden
* Zwei Zahlen miteinander vergleichen

Das können Sie sicherlich auch, aber Computer können das:

* Sehr schnell: Milliarden von Operationen pro Sekunde
* Sehr genau: Milliarden von Zahlen speichern und exakt so wieder abrufen

Sie lernen zunächst, was Code und was ein Programm ist. Am Ende des Kapitels werden Sie Ihr erstes eigenes Programm in der Programmiersprache Java schreiben und ausführen.



### Was ist Code?
* Code ist eine Reihe von Anweisungen,
* Jede Anweisung beschreibt, welche Operation (z.B. Addition) der Computer mit welchen Operanden (z.B. 5 und 3) ausführen soll
* Der Computer führt eine Anweisung nach der anderen aus

Programme bestehen nun aus Millionen von Anweisungen. Die Anweisungen sind wiederum Zahlen - hier als Hexadezimal-codierter x86-Code (erstellt mit [godbolt.org](https://godbolt.org/z/WYorj7EG5)):

```
55 48 89 e5
89 7d fc 8b
45 fc 0f c0
5d c3
```
    
So zu entwickeln ist sehr kompliziert und fehleranfällig, also gibt es ein Abstraktionsniveau höher Assembler - menschenmerkbare Abkürzungen für die Befehle und Hilfe bei der Berechnung von Speicheradressen, wo Daten abgespeichert sind, z.B.:

```
push   rbp
 mov    rbp,rsp
 mov    DWORD PTR [rbp-0x4],edi
 mov    eax,DWORD PTR [rbp-0x4]
 imul   eax,eax
 pop    rbp
 ret    
main:
 push   rbp
 mov    rbp,rsp
 mov    eax,0x0
 pop    rbp
 ret  
```

Auch dies ist noch recht aufwändig - und zudem noch an eine konkrete Prozessorarchitektur gebunden. Als nächstes Abstraktionsniveau kann man dann eine höhere Programmiersprache nehmen, z.B.:

```
int square(int num) {
    return num * num;
}
```

Wir nutzen in unserer Vorlesung Java als Programmiersprache. Im Hintergrund gibt es einen Compiler, der Java in Maschinensprache übersetzt. Die Maschinensprache wird auf unseren Wunsch hin vom Betriebssystem geladen und dann zur Ausführung gebracht. 
Bei Java gibt es noch die Besonderheit, dass es eine Art virtuelle Maschinensprache nutzt, die unabhängig von der genutzten Prozessorarchitektur ist und erst zur Laufzeit von einer weiteren Programmkomponente in die konkrete Maschinensprache übersetzt wird. 
Aber hierzu später mehr


>**Welcher Code wird ausgeführt?**

Das Betriebssystem startet den binären Code bei der ersten Anweisung - aber wo ist das in unserem Code der höheren Programmiersprache?

Im allgemeinen Java-Programm: die Main-Methode der Hauptklasse: 

```
public static void main(String[] args) {
}
```


### Was ist Programmieren?
Unter Programmieren versteht man das Erstellen von Anweisungen für eine Maschine. Dies hat historisch eine viel längere Geschichte, als Sie wahrscheinlich vermuten. Besuchen Sie diese [Seite](https://www.cs101.com/) und überzeugen Sie sich selbst. 

Im Rahmen der nächsten zwei Semester werden Sie nun folgendes Lernen: 

* Programmieren 1: Erwerb der Fähigkeit, ein (mittelgroßes) Java-Programm zu schreiben
* Programmieren 2: Erweiterung um die „Kommunikation mit der Außenwelt“ und Einführung in die Web-Programmierung

Ein Programm ist vergleichbar mit einem Kochrezept:
Ziel ist es einen bzw. mehrere fertige Pfannkuchen aus verschiedenen einzelnen Zutaten zu kochen.
Kochrezepte sind wie „imperative“ Programmierung: (von lat. imperare: anordnen, befehlen)

```
\\ Variablen
gramm mehl        = 300;
liter milch       = 0,6;
stueck eier       = 3;
prise salz        = 1; 
liter wasser      = 0,05;
essloeffel butter = 1;

\\ Methoden
void rühren();
void braten();

\\Hauptprogramm
pfannkuchen_machen {
    teig = mehl + milch + eier + salz;
    rühren(teig);
    teig = teig + wasser;
    rühren(teig);
    pfannkuchen = braten(reig);
}
```

### Aufbau eines Programms

Der Grundbaustein für ein Programm sind Anweisungen mit verschiedenen Untertypen:

1. Variablen deklarieren: Speicher für Daten reservieren
2. Variablen zuweisen: Werte oder Berechnungen im reservierten Speicher ablegen
3. Methodendeklarationen: eine bestimmte Sammlung von Anweisungen definieren, die unter einem Namen abgerufen werden kann, ggfs. mit Parametern
4. If-Anweisungen: Je nach Wert einer Bedingung, eine von mehreren Anweisungsblöcken ausführen
5. Schleifen: einen Anweisungsblock wiederholt ausführen

Aber nun erst einmal langsam, wir machen das Schritt für Schritt. 


* Ein Java-Programm ist in (Klassen), Methoden und Blöcke aufgeteilt, die ineinander verschachtelt sind.
* Blöcke werden durch die {}-Klammern geschachtelt.
* Der äußere Block umfasst die Klasse `Uebung`, der innere Block bildet den Methodenrumpf von `main` mit dem Aufruf der Methode `tueWas`.


```
public class Uebung{
    public static void main(String args[]){
        tueWas(0815);
    }
}
```

Genauer: 

* Hauptklasse oder Startklasse: Oberste Struktureinheit in Java
* Hauptmethode oder main-Methode genannt: Hier läuft das eigentliche Programm ab, ohne die main-Methode läuft das Programm nicht.
* Weitere Methoden: Es können für Teilberechnungen weitere Methoden definiert werden, die dann von der main-Methode aufgerufen werden. D.h. Methoden sind gespeicherte Anweisungen innerhalb eines Programms. Sie werden für einen bestimmten Zweck geschrieben und aufgerufen. Weiterhin kann man Methoden auch als Werkzeug betrachten. Man kann ein Werkzeug besitzen, aber es gar nicht einsetzen. 



### Übersetzen und Ausführen eines Programms

* Java-Programme können mit einem beliebigen Editor geschrieben werden. Die Dateiendung der Quell-Dateien lautet .java. Hier steht der Quellcode (engl. source)
* Der Java-Compiler `javac` übersetzt die Quelldatei in sogenannten Bytecode, dieser wird in der mit der Endung .class gespeichert.
* Die Java-Laufzeitumgebung (engl. Runtime Environment) `java` führt den Bytecode aus.
* Das Java-Programm von der Einführung gibt den Text „Hallo Welt“ am Bildschirm aus.

```java
class HalloWelt{
    public static void main(String args[]){
        System.out.println("Hallo Welt");
    }
}
```
@LIA.java(HalloWelt)

Das bedeutet

* Übersetzen: In Java wird Programmcode über einen Compiler in den Bytecode übersetzt (kompiliert). Dieser kann dann von einem Interpreter ausgeführt werden.

<p align="center">
<img src="programmausfuehren2.png" alt="ProgrammAusfuehren" width="60%">
</p>

* Eine Besonderheit von Java ist, dass ein Bytecode von verschiedenen Systemen verwendet werden kann: „Write once, run anywhere“

<p align="center">
<img src="bytecode2.png" alt="Bytecode" width="60%">
</p>

Wir wollen nun das Programm selbst schreiben. Hierzu benötigen Sie wie das Bild zeigt:

* Einen Java-Compiler
* Einen Java-Interpreter

Auf den Rechner in der Hochschule ist alles bereits installiert. Auf Ihrem eigenen Rechner können Sie auf die Schnelle einen externen Web-Editor nutzen, wie z.B. https://www.online-ide.com/online_java_editor, wenn Sie gleich los programmieren wollen. Im nächsten Kapitel erklären wir Ihnen zunächst wie man auf der Kommandozeile arbeitet und dann, wie Eclipse mit allem drum und dran installiert wird. 

---

>**Quiz** 

Führen Sie nun folgendes Quiz durch und testen Sie Ihr Wissen: 

**Frage 1**

Was macht der Compiler?

[(x)] Er erstellt .class-Dateien
[( )] Er verarbeitet .class-Dateien
[( )] Er führt das Programm aus

---

**Frage 2**

Was macht der Befehl `java`?

[( )] Er macht aus Qullcode Bytecode
[(x)] Er führt das Programm aus
[( )] Er verarbeitet .java-Dateien

---


###  Kommandozeile

>**Arbeiten mit der Kommandozeile unter Windows**

Zunächst machen wir ein paar Übungen auf der Kommandozeile:

- Öffnen der Kommandozeile

Um die Kommandozeile zu öffnen, drücken Sie `Windows + R` und geben Sie `cmd` in das Ausführen-Dialogfeld ein. Drücken Sie dann die Eingabetaste.

- Überprüfen des Benutzernamens

Um den Benutzernamen anzuzeigen, verwenden Sie den Befehl:

```
whoami
```

- Navigieren durch Verzeichnisse

Verwenden Sie `cd`, um zwischen Verzeichnissen zu wechseln. Beispiele:

```
cd            # Aktuelles Verzeichnis anzeigen
cd Desktop    # Zum Desktop wechseln
```

- Anzeigen des Verzeichnisinhalts

Verwenden Sie `dir`, um den Inhalt des aktuellen Verzeichnisses anzuzeigen:

```
dir
```

- Erstellen und Löschen von Ordnern

Verwenden Sie `mkdir` und `rmdir`, um Ordner zu erstellen und zu löschen:

```
mkdir practice    # Erstellt einen Ordner namens "practice"
rmdir Test        # Löscht den Ordner "Test"
```

- Anzeigen der Java-Version

Um die installierte Java-Version anzuzeigen, verwenden Sie:

```
java -version
```

- Überprüfen von Umgebungsvariablen

Um Umgebungsvariablen wie `JAVA_HOME` oder `PATH` zu überprüfen, verwenden Sie:

```
echo %JAVA_HOME%
echo %PATH%
```

- Beenden der Eingabeaufforderung

Um die Eingabeaufforderung zu schließen, geben Sie einfach ein:

```
exit
```

>**Kommandozeile und Java-Code**

Um einen Java-Code im Texteditor zu erstellen und dann auf der Kommandozeile zu kompilieren und auszuführen, können Sie die folgenden Schritte befolgen:

1. **Öffnen Sie Ihren Texteditor:** Verwenden Sie ein beliebiges Textbearbeitungsprogramm wie Notepad, Editor, TextPad, UltraEdit, Kate, gedit, Emacs, vi oder ein anderes, das "plain text" (unformatierten Text) speichern kann.

2. **Schreiben Sie Ihren Java-Code:** Erstellen Sie eine neue Datei und geben Sie Ihren Java-Code ein. Zum Beispiel:

```java
public class HalloWelt {
    public static void main(String[] args) {
        System.out.println("Hallo Welt!");
    }
}
```

3. **Speichern Sie die Datei:** Speichern Sie die Datei mit der Erweiterung ".java". Zum Beispiel: "HalloWelt.java". Wichtig: Die Datei muss so heißen, wie Ihre Klasse heißt. In diesem Fall: HalloWelt

4. **Öffnen Sie die Eingabeaufforderung oder das Terminal:** Navigieren Sie zu dem Verzeichnis, in dem sich Ihre Java-Datei befindet.

5. **Kompilieren Sie den Java-Code:** Verwenden Sie den Befehl `javac`, um den Java-Code zu kompilieren. Wenn Sie möchten, können Sie die kompilierten Dateien in einem separaten Ordner speichern. Beispiel:

```bash
javac HalloWelt.java
```

oder

```
javac -d . HalloWelt.java
```

Der `-d`-Schalter gibt an, in welchem Verzeichnis die kompilierten `.class`-Dateien gespeichert werden sollen. Hier wird der Punkt verwendet, um die Dateien im aktuellen Verzeichnis zu speichern.

6. **Führen Sie das Programm aus:** Verwenden Sie den Befehl `java`, um das Programm auszuführen. Verwenden Sie den Klassennamen ohne die Erweiterung ".class". Beispiel:

```
java HalloWelt
```

7. **Überprüfen Sie die Ausgabe:** Das Programm sollte ausgeführt werden und die Ausgabe auf der Konsole anzeigen. In diesem Fall würde es "Hallo Welt!" ausgeben.

Durch das Befolgen dieser Schritte können Sie einen Java-Code im Texteditor erstellen, kompilieren und ausführen, ohne eine integrierte Entwicklungsumgebung (IDE) zu verwenden. Dies ist auf Dauer aber sehr mühsam, wie Sie vielleicht an diesem kleinen Beispiel schon bemerkt haben. 

### Installation von Eclipse

Wir werden im 1. Semester mit der IDE (dies ist die Abkürzung für integrierte Entwicklungsumgebung von engl. integrated development environment) arbeiten. Eine IDE macht Ihne das Leben sehr viel leichter. Sie sollten, wenn möglich, Eclipse auch auf Ihrem privaten Rechner installieren, um auch zu Hause üben zu können. 

Führen Sie also diese Schritte auf Ihrem Laptop oder Rechner zu Hause durch, so dass Sie für das Semester ausgerüstet sind. Auf den Rechnern der Hochschule ist alles bereits installiert. 

1. Öffnen Sie Ihren Webbrowser und besuchen Sie die offizielle Eclipse-Website unter https://www.eclipse.org/downloads/.

2. Herunterladen des Installationsprogramms („Download x86_64“)
![](installation_1.JPG) <br>

3. Bestätigung des Downloads vom ausgewählten Server
![](installation_2.JPG)

4. Wechsel in den „Downloads“-Ordner und Start des heruntergeladenen Programms
`eclipse-inst-jre-win64.exe`

5. Auswahl des Eintrags `Eclipse IDE for Java Developers`

<p align="center">
<img src="installation_3.JPG" alt="Auswahl Eintrag" width="60%">
</p>



6. Bestätigen der Standardeinträge für die JVM und den Installationsordner
<p align="center">
<img src="installation_4.JPG" alt="Bestätigung Installationsordner" width="60%">
</p>

7. Auswahl/Anlegen des Eclipse Workspace und "Launch"
<p align="center">
<img src="installation_5.JPG" alt="Auswahl des Eclipse Workspace" width="60%">
</p>


>**Führung durch Eclipse**

Absolvieren Sie dann die Anleitung zum Erstellen eine Hello World-Projekts:

<p align="center">
<img src="installation_5b.JPG" alt="Hello World" width="75%">
</p>

>**Start des ersten Projekts**

Ein Eclipse-Projekt starten Sie unter:
<p align="center">
<img src="installation_5d.JPG" alt="Java Projekt starten" width="75%">
</p>


Oder, wenn Sie den Start-Bildschirm nicht sehen, klicken Sie links oben auf File -> New -> Java Project -> Project name eingeben
<p align="center">
<img src="installation_6a.JPG" alt="Java Projekt starten" width="50%">
</p>


Geben Sie oben einen Projektnamen ein und deslektieren Sie das Häckchen der module-info.java!
Danach klicken Sie auf `Finish`.
<p align="center">
<img src="installation_6b.JPG" alt="Projektname" width="60%">
</p>

Wir arbeiten zunächst ohne Module und auch ohne Packages. 

Um nun eine Klasse zu erstellen, rechtsklicken Sie auf das Projekt `ErstesProjekt`, wählen Sie `New`, dann `Class`.
<p align="center">
<img src="installation_8b.JPG" alt="Klasse anlegen" width="60%">
</p>

 Geben Sie einen Namen für die Klasse ein, wählen Sie aus, dass die Main-  und klicken Sie auf `Finish`.
<p align="center">
<img src="installation_9b.JPG" alt="Klassenname" width="60%">
</p>


Erstellen Sie nun Ihr gewünschtes Programm. Zum Ausführen des Programms dann einfach den grünen `Run As` Button drücken:
![](installation_10.jpg)

### Übungen

**Aufgabe 1:** 
Recherchieren Sie ein Pfannkuchenrezept und versuchen Sie die einzelnen Schritte nachzuvollziehen. Natürlich dürfen Sie dieses Rezept auch nachkochen. Was sind die Variablen und Methoden in dem Rezept?

**Aufgabe 2:** 
Erstellen Sie mit Hilfe eines einfachen Texteditors ein Programm `HalloStudent.java`, welches Ihren Namen auf Konsole ausgibt. 

* Übersetzen Sie das Programm mit `javac HalloStudent.java`
* Führen Sie es mit `java HalloStudent` aus
* Suchen Sie den erzeugten Binärcode

**Aufgabe 3:** 
Programmieren mit Eclipse: Machen Sie Aufgabe 2 mit Eclipse.

Wenn Sie ein kleines Programm auf der Kommandozeile ausführen können, dieses auch in der IDE läuft und Sie dazu verstanden haben, welche Schritte im Hintergrund ausgeführt wurden, dann sind Sie bereit für das nächste Kapitel. 



## Variablen und Datentypen 

Schauen Sie sich folgendes Beispiel an und überlegen Sie sich für jede Zeile, was das Programm tun könnte und welche Ausgabe der Code Ihrer Meinung nach erzeugt.

```java
class Variablen {
    public static void main(String[] args) {

        byte b = 1;
        System.out.println(b);

        short s = 250;
        System.out.println(s);

        int i = 5;
        System.out.println(i);

        long l = 105464560L;
        System.out.println(l);

        float f = 1.5f;
        System.out.println(f);

        double d = 1.8;
        System.out.println(d);

        char c = 'a';
        System.out.println(c);

        char c2 = 65;
        System.out.println(c2);

        boolean bl = true;
        System.out.println(bl);
    }
}
```
@LIA.java(Variablen)


* Führen Sie nun den Code aus und überprüfen Sie Ihre Vermutung. 

* Ändern Sie den Code ab und probieren Sie aus, ob das Programm noch läuft und was die Ausgabe ist. 

Achtung: Wenn Sie eine rote Ausgabe erhalten, haben Sie einen fehlerhaften Code erzeugt. Können Sie den Code wieder berichtigen?

* Gehen Sie nun auf die nächste Seite und arbeiten Sie die Erklärungen durch.


### Variablen deklarieren
Der Speicher im Computer besteht nur aus einer langen Folge von 0en und 1en. Jeweils 8 werden zu einem Byte zusammengefasst. Die Bytes werden durchnummeriert (beginnend bei 0). Die Nummer eines Bytes ist dessen Adresse.

Variablen geben einer bestimmten Speicherstelle einen Namen und einen Typen:

* Einfacher zu merken als eine Speicheradresse
* Kann gleich bleiben, auch wenn sich die Speicheradresse ändert
* Der Typ kann bestimmte Arten von Programmfehlern verhindern und bestimmt wie viele Bytes die Variable umfasst

Eine Variable ist also eine Art Gefäß im Speicher. Werte können überprüft, verändert und vor allem gespeichert werden.
Variablen haben einen bestimmten TYP, eine ADRESSE im Speicher, einem NAMEN und natürlich einem WERT. Java ist eine statisch typisierte Programmiersprache. Das bedeutet, dass jede Variable einen festen Typ hat, der bereits zur Übersetzungszeit bekannt ist (hierzu später mehr).

Wie funktioniert nun die Deklaration von Variablen in Java:

```
int schuhgroesse;  // Das hier ist übrigens ein Kommentar
char buchstabe1, buchstabe2, buchstabe3; // Hiervon braucht man oft mehrere
double temperatur; // Kommazahl
boolean sonnigerTag; // wahr/falsch, ja/nein -> boolean
```

In Java können wir Variablen direkt bei der Deklaration mit einem Wert initialisieren, hier *Literals* also Konstanten im Programmtext:

```
int schuhgroesse = 42;
double temperatur = 20.2; // Ohne Einheit - müssen wir uns separat merken
double wunschEinkommen = 50_000; // Euro? Brutto/Netto? Im Jahr oder Monat?
boolean sonnigerTag = true;
```

Allgemein also: 

```
Datentyp Variablenname = Wert;
```
In einem kleinen Programm könnte das so aussehen: 

```java
class Schuhgroesse {
    public static void main(String[] args) {
        int schuhgroesse = 42;
        System.out.println("Meine Schuhgröße ist: " + schuhgroesse);
   }
}
```
@LIA.java(Schuhgroesse)

Hinweis: Man muss einer Variable nicht sofot einen Wert geben. Dies kann auch später geschehen. Die Variable erhält dann zunächst einen Standardwert - je nach Datentyp. 


Hier finden Sie eine Übersicht über verschiedene primitive Datentypen, das sind die elementaren Datentypen. 

<!-- data-type="None" -->
| Datentyp   | Bit   | Minimum   | Maximum   |
| :--------- | :--------- | :--------- | :--------- |
| byte    | 8-Bit     | -128    | 127    |
| short    | 16-Bit     | -32768    | 32767    |
| int    | 32-Bit     | -2147483648    | 2147483647   |
| long    | 64-Bit     | -9223372036854775808    | 9223372036854775807    |
| float    | 32-Bit     | -3.4 * (10<sup>38</sup>)    | 3.4 * (10<sup>38</sup>)      |
| double    | 64-Bit     | -1.7 * (10<sup>308</sup>)    | 1.7 * (10<sup>308</sup>)    |

Weiterhin gibt es noch die beiden Datentypen `boolean` und `char`: 

<!-- data-type="None" -->
| Datentyp   | Bit   |Werte   |
| :--------- | :--------- | :--------- | 
| boolean    | 1 Byte     | true / false   | 
| char    | 2 Byte     | Ein Unicode-Zeichen  | 

Primitive Typen werden immer klein geschrieben. 

Hinweis: Ein char ist intern als Zahlen codiert (z.B. A → 65) – deshalb kann mit char gerechnet werden.

Weiterhin gibt es Referenztypen, welche auf Klassen basieren (z.B. String). Diese werden groß geschrieben. 

Java ist eine streng typisierte Sprache, d.h. Java erlaubt es nicht, Variablen die für einen Typ deklariert sind mit Werten aus einem anderen Typ zu belegen. Beim Übersetzen des Quellcodes wird geprüft, ob alle Werte zu den geforderten Typen passen – also auch Variablenwerte und Variablentypen.
Eclipse prüft dies bereits beim Schreiben und meldet ggf. einen Fehler


Bei der Benennung von Variablen ist es wichtig, einige Regeln zu beachten:

* Am Anfang muss ein Buchstabe (oder `_`) stehen.
* Danach können Buchstaben oder Ziffern folgen.
* Erlaubt (aber nicht empfohlen) sind: `$, _, ä, ö, ü, ß, €, …` (wobei `$` oft für generierte Namen verwendet wird.)
* Nicht erlaubt sind Sonderzeichen wie `!, ?, *, /, … `
* Groß- und Kleinschreibung ist relevant. Das bedeutet, dass Variablennamen wie `glueckszahl` und `gluecksZahl` unterschiedlich sind.
* Variablennamen sollten zusammengeschrieben werden, also ohne Leerzeichen.
* Schlüsselwörrter dürfen nicht als Variablennamen verwendet werden, da sie zum Sprachumfang von Java gehören

* Eine häufige Konvention ist die Verwendung von „CamelCase“:

  * Variablen, Methoden und Pakete beginnen klein und jedes neue Wort beginnt groß, z.B. kleinAnfangenUndJedesWortGrossBeginnen.
  * Klassennamen beginnen groß und jedes neue Wort beginnt groß, z.B. GrossAnfangenUndJedesWortGrossBeginnen.

>**Merke**
Gute Variablennamen sind nicht zu kurz und nicht zu lang. Sie sind immer aussagekräftig (z.B. int alterInTagen), nur temporäre Variablen dürfen auch mal kürzer sein (z.B. in Schleifen, vgl. folgendes Kapitel). Der Typ der Variable sollte nicht im Namen aufgeführt werden. Der Compiler meldet zurück, ob der Name gültig ist, nicht ob dieser sinnvoll gewählt ist.

### Variablen zuweisen
Die Initialisierung hat den Variablen direkt bei der Speicherreservierung einen Wert zugewiesen. Nachdem eine Variable angelegt wurde können wir ihr einen (neuen) Wert zuweisen:

```java
class Temperatur {
    public static void main(String[] args) {
        double temperatur = 18.1;
        System.out.println("Die Temperatur ist: " + temperatur + " Grad.");
        System.out.println("Die Sonne scheint...");
        temperatur = 24.5;
        System.out.println("Nun ist die Temperatur: " + temperatur + " Grad.");
   }
}
```
@LIA.java(Temperatur)

Sie sehen im Programmcode die Zuweisungen. Links vom Gleichheitszeichen steht der Name einer bereits deklarierten Variable. Rechts vom Gleichheitszeichen steht ein Ausdruck.

Für Ausdrücke gibt es verschiedene Aufbauten:

* Literale - das sind konstante Werte, die direkt im Programmtext geschrieben werden, z.B. `8`, `17.4`, `'a'`, `"Hallo Welt"`
* Variablen - der Name einer bestehenden Variable, dieser wird bei der Auswertung des Ausdrucks mit dem aktuellen Wert der Variable ersetzt, z.B. `schuhgroesse`
* Methodenaufrufe - es wird Code, der unter dem Methodennamen abgespeichert ist, ausgeführt und das Ergebnis zurück geliefert, z.B. `readInt()`, manche Methoden nehmen Parameter (wiederum Ausdrücke), z.B. `System.out.println("Hallo Welt")`
* Operationen: hier werden eine oder mehrere (meistens zwei) Ausdrücke mit einem Operator verknüpft, z.B. `schuhgroesse + wunschEinkommen`

In Java müssen wir den Wert eines Ausdrucks einer Variable zuweisen:

```
double komischeZahl = schuhgroesse + wunschEinkommen;
```

oder uns per Methodenaufruf ausgeben:

```
System.out.println("Hallo " + "Programmieren " + 1)
```
Mit Operationen und Methodenaufrufen können komplexe Ausdrücke geschafften werden, z.B.:

```
System.out.println("In Fahrenheit: " + ((readDouble() * 9.0/5.0) + 32))
```
Auch dazu später mehr.

Ausdrücke werden von innen nach außen ausgewertet, d.h. bei verschachtelten Ausdrücken erst die Sachen in Klammern, bzw. nach Prioritäten ("Punkt vor Strich).

Bei Zuweisungen wird erst die rechte Seite berechnet und dann erst die links genannte Variable aktualisiert. Überlegen Sie, was folgender Programmcode somit ausgibt. Probieren Sie dies dann aus.

```java
class Wert {
    public static void main(String[] args) {
       int wert = 10;
       System.out.println("Der Wert ist: " + wert);
       wert = wert + 1;
       System.out.println("Der Wert ist nun: " + wert);
   }
}
```
@LIA.java(Wert)


### Operatoren
Übersicht über wichtige Java-Operatoren:

| Operator | Beschreibung                                    |
|----------|-------------------------------------------------|
| +        | Addition von Zahlen oder Verkettung von Strings |
| -        | Subtraktion von Zahlen                          |
| *        | Multiplikation von Zahlen                       |
| /        | Division von Zahlen                             |
| %        | Modulo (Rest bei der Division)                  |
| +=       | Addition und Zuweisung                          |
| -=       | Subtraktion und Zuweisung                       |
| ++       | Inkrement (Erhöhung um eins)                    |
| --       | Dekrement (Verminderung um eins)                |


Von den Standardoperatoren `+`, `-`, `*` (Mal), `/` (geteilt durch) für Zahlen gibt es auch jeweils eine Version, die gleich die Zuweisung integriert. 

Überlegen Sie, welchen Wert `x` im folgenden Programm hat. Fügen Sie eine Zeile im Programmcode für die Ausgabe hinzu und überprüfen Sie Ihre Überlegung.


```java
class Operatoren1 {
    public static void main(String[] args) {
        int x = 5;
        x += 5; // Gleichbedeutend mit x = x + 5
   }
}
```
@LIA.java(Operatoren1)


Was ist `y` am Ende des folgenden Programmcodes? Fügen Sie auch hier eine Zeile für die Ausgabe hinzu, um Ihre Überlegung zu überprüfen.

```java
class Operatoren2 {
    public static void main(String[] args) {
        int y = 2;
        y *= y; // Gleichbedeutend mit y = y * y;
   }
}
```
@LIA.java(Operatoren2)


Häufig zählen wir Variablen um eins nach oben oder eins nach unten, hier gibt die Kurzformen `i++` und `i--`. Sie liefern den Wert von `i` zurück und danach wird `i` inkrementiert bzw. dekrementiert. Versuchen Sie folgenden Code nachzuvollziehen:


```java
class Operatoren3 {
    public static void main(String[] args) {
        int i = 0;
        System.out.println(i++); // Gibt 0 aus und erhöht dann i auf 1
        System.out.println(i); // Gibt den neuen Wert von i (1) aus
        System.out.println(i--); // Gibt 1 aus und verringert dann i auf 0
        System.out.println(i); // Gibt den neuen Wert von i (0) aus
   }
}
```
@LIA.java(Operatoren3)


Weniger verbreitet sind die Formen `++i` und `--i`, die zuerst `i` inkrementieren bzw. dekrementieren und dann den Wert zurückliefern. Dies liefert folgendes, doch etwas überraschende Eregebnis:

```java
class Operatoren4 {
    public static void main(String[] args) {
        int i = 0;
        System.out.println(++i); // Erhöht i zuerst auf 1 und gibt dann 1 aus
        System.out.println(i); // Gibt den aktuellen Wert von i (1) aus
        System.out.println(--i); // Verringert i zuerst auf 0 und gibt dann 0 aus
        System.out.println(i); // Gibt den aktuellen Wert von i (0) aus
   }
}
```
@LIA.java(Operatoren4)

Nützlich ist der Modulo-Operator `%` - er liefert den Rest bei einer Ganzzahlendivision, z.B.:

```java
class Operatoren5 {
    public static void main(String[] args) {
        int zahl = 22;
        int divisor = 4;
        int rest = zahl % divisor;
        System.out.println(rest); // Der Wert ist 2, da 22/4 = 5 Rest 2 ist
   }
}
```
@LIA.java(Operatoren5)

Weitere Operatoren sind Vergleichsoperatoren (`==`, `!=`, `<=`, `>=`, `<`, `>`), Bit-Operatoren (`&`, `|`, `<<`, `>>`) und logische Operatoren (`&&`, `||`)


### Sichtbarkeit von Variablen
„Sichtbar“ bedeutet: Die Variable kann vom folgendem Code verwendet werden. Variablen sind erst sichtbar, nachdem sie deklariert wurden.

Neben den Variablen, die wir innerhalb einer Methode deklarieren (bisher in der main-Methode), gibt es auch noch statische Klassenvariablen. Diese sind in der gesamten Klasse sichtbar und das Programm kann hierauf zugreifen, sobald es gestartet wurde. Eine statische Klassenvariable kann von mehreren Methoden einer Klasse verwendet werden. Sie wird im Rumpf einer Klassendeklaration geschrieben (nicht im Rumpf einer Methodendeklaration). 

Hier ein Beispiel:

```java
class Klassenvariable {
    public static int zahl = 10; //statische Klassenvariable

    public static void main(String[] args) {
        int neueZahl = zahl + 10; //lokale Variable, nur innerhalb der Methode sichtbar
        System.out.println(neueZahl);
   }
}
```
@LIA.java(Klassenvariable)

* `static` bedeutet für uns zunächst etwa "von Anfang an vorhanden", "der Klasse zugeordnet"
* Variablen ohne den Modifier `static` sind den Objekten zugeordnet (ab Kapitel Klassen und Objekte)
* Lokale Variablen sind nur innerhalb des Blocks sichtbar

Weiterhin gibt es noch statische Klassenkonstanten. Diese werden mit dem Schlüsselwort `final` deklariert. Hier sind Änderungen nur an einer Stelle möglich. Dies erleichter die Lesbarkeit. 

```
\\ statt den Wert als Literal fest im Code anzugeben
double umfang = 2.0 * radius * 3.14159;
double flaeche = radius * radius* 3.14159;

\\ wird der Wert als Klassenkonstante deklariert
public static final double PI = 3.14159;
double umfang = 2.0 * radius * PI;
double flaeche = radius * radius * PI;

```
Konstanten werden groß geschrieben. 

>**Lebensdauer von Variablen**

Klassenvariable: beginnt mit dem Laden der Klasse und endet mit dem Ende des Programms
Lokale Variable: beginnt mit der Deklaration im Block und endet mit dem Blockende (schließende })


### Konvertierung
In Java können verschiedene primitive Datentypen durch Umwandlung konvertiert werden. Dabei unterscheidet man zwei Fälle: 

* Widening = Erweitern: eine Variable von einem Typ mit einem kleinen Wertebereich wird in eine Variable von einem Typ mit einem größeren Wertebereich umgewandelt. Dies stellt in der Regel kein Problem dar.


```java
class Widening {
    public static void main(String[] args) {
		byte kleinsterTyp = 5;
		short kleinerTyp = kleinsterTyp;
		int grosserTyp = kleinerTyp;
		
		System.out.println(grosserTyp);
   }
}
```
@LIA.java(Widening)

* Narrowing = Eingrenzen: Gegenteil zu Widening -> hier ist Casting erforderlich

```java
class Narrowing {
    public static void main(String[] args) {
		byte kleinsterTyp = 5;
		short kleinerTyp = kleinsterTyp;
		int grosserTyp = kleinerTyp;
		
		// Type Mismatch
		// kleinerTyp = grosserTyp;
		
		// so geht's mit Narrowing
		kleinerTyp = (short) grosserTyp;
   }
}
```
@LIA.java(Narrowing)

Was ergibt dann folgendes Beispiel?

```java
class Konvertierung {
    public static void main(String[] args) {
		short zahl = 128;
		byte kleinesByte = (byte) zahl;
		// Was kommt hier heraus?
		System.out.println(kleinesByte);
   }
}
```
@LIA.java(Konvertierung)


### Übungen

**Aufgabe 1:** 

Führen Sie folgendes Quiz durch und testen Sie Ihr Wissen: 


**Frage 1**

Welcher Variablentyp würde am besten verwendet werden, um die Temperatur `42,2` Grad zu speichern?

[( )] Integer
[(x)] Float
[( )] String
[( )] Boolean

---

**Frage 2**

Welcher Variablentyp wird verwendet, um einzelne Buchstaben zu speichern?

[(x)] Char
[( )] Integer
[( )] Float
[( )] String

---

**Frage 3**

Welcher Variablentyp könnte verwendet werden, um alle Menschen auf der Welt zu nummerieren?

[( )] Char
[( )] Float
[(x)] Long
[( )] Integer

---

**Frage 4**

Welcher Variablentyp wird verwendet, um einen Satz zu speichern?

[( )] Char
[( )] Integer
[( )] Float
[(x)] String

**Weitere Aufgaben:**   

Machen Sie die Aufgaben aus der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus Kapitel 01.

### Ablage 

* Variablen: Werden in Lower Camel Case benannt, wie z.B. alterInTagen
* Klassen: Werden in Upper Camel­Case benannt, wie z.B. TageDesJahres
* Konstanten (ändern sich nicht): komplett in Großbuchstaben (als Trennzeichen typischerweise Unterstrich), wie z.B. ANZAHL_JAHRESZEITEN

Und noch ein paar Tipps für die Arbeit in Eclipse:

* Vervollständigung: Strg + Leertaste
* Formatieren: Source -> Format oder Strg+Shift+F
* Umbenennen: rechte Maustaste -> Refactor -> Rename


## Kontrollfluss

Der Kontrollfluss in Java ermöglicht es uns, den Ablauf unseres Codes zu steuern, indem wir Entscheidungen treffen und Schleifen verwenden. Kontrollflussstrukturen wie bedingte Anweisungen und Schleifen ermöglichen es uns, unseren Code dynamisch zu gestalten und verschiedene Pfade je nach Bedingungen oder Anforderungen auszuführen.

Schauen Sie sich folgendes Beispiel an und überlegen Sie sich für jede Zeile, was das Programm tun könnte und welche Ausgabe der Code Ihrer Meinung nach erzeugt.

```java
class DemoKontrollfluss{
    public static void main(String args[]){
        int zahl = 10;

        if (zahl % 2 == 0) {
            System.out.println(zahl + " ist eine gerade Zahl.");
        } else {
            System.out.println(zahl + " ist eine ungerade Zahl.");
        }
        
        System.out.println("Zahlen von 1 bis 5:");
        for (int i = 1; i <= 5; i++) {
            System.out.println(i);
        }
    }
}
```
@LIA.java(DemoKontrollfluss)

Führen Sie nun den Code aus und überprüfen Sie Ihre Vermutung.



### If-Verzweigung
Die if-Anweisung ist die einfachste Kontrollstruktur. Man kann sich diese wie folgt vorstellen:

<p align="center">
<img src="if.png" alt="if-Anweisung" width="25%">
</p>

Sie wird wie folgt dargestellt:

```
if (Bedingung) {
    //Wenn die Bedingung `true` ist
    Anweisung;
}
```

Ist die Bedingung wahr, werden die Anweisungen der nächsten Zeile, bzw. des Blockes ausgeführt, ansonsten passiert nichts! Beim Auswerten der Bedingung muss immer ein Boolescher Wert entstehen.



>**Wie können diese Bedingungen aussehen?**

In Programmiersprachen werden häufig Vergleiche zwischen Werten mittels Operatoren durchgeführt, um Bedingungen zu überprüfen. Hier sind einige gängige Vergleiche:

- `a > 0`: Überprüft, ob der Wert von "a" größer als 0 ist.
  
- `c == d`: Überprüft, ob der Wert von "c" gleich dem Wert von "d" ist, zum Beispiel, ob zwei Ganzzahlen gleich sind.
  
- `e != 1`: Überprüft, ob der Wert von "e" ungleich 1 ist.
  
- `"Müller".equals("Meier")`: Überprüft die Gleichheit von zwei Strings, in diesem Fall, ob der String "Müller" gleich dem String "Meier" ist.

Diese Bedingungen können in `if`-Verzweigungen verwendet werden, um Entscheidungen im Code zu treffen. Ändern und ergänzen Sie folgendes Programm so, dass in der if-Verzweigung `"Der if-Block wurde ausgeführt"` ausgegeben wird. 


```java
class IfAnweisung{
    public static void main(String args[]){
    int f = 3;
    if (f > 5) {
        // Führe diesen Codeblock aus, wenn "f" größer als 5 ist
        }
    }
}
```
@LIA.java(IfAnweisung)



>**Logische Operatoren**

Logische Operatoren können wie folgt aussehen:

| Operator | Beschreibung                                                                                        |
|----------|-----------------------------------------------------------------------------------------------------|
| !        | Negation: Dreht den Wahrheitswert um (aus `true` wird `false` und aus `false` wird `true`)      |
| &        | Und mit vollständiger Auswertung: Liefert `true`, wenn beide Ausdrücke `true` sind               |
| \|       | Oder mit vollständiger Auswertung: Liefert `true`, wenn einer oder beide Ausdrücke `true` sind   |
| &&       | Und mit verkürzter Auswertung: Wie &, jedoch wird sofort `false` zurückgegeben, wenn der erste Ausdruck `false` ist |
| \|\|     | Oder mit verkürzter Auswertung: Wie \|, jedoch wird sofort `true` zurückgegeben, wenn der erste Ausdruck `true` ist  |
| \^       | Exklusives Oder: Liefert nur `true`, wenn genau einer der beiden Ausdrücke `true` ist             |



Welche Anweisungen eignen sich für Bedingungen?

1. 4<10
[(x)] wahr
[( )] falsch

2. int a = 0;
[( )] wahr
[(x)] falsch

3. String name = "Schulze"; name.equals("Meier") 
[(x)] wahr
[( )] falsch

4. 4 == 4 && 5 == 5 
[(x)] wahr
[( )] falsch

5. true || 4>10
[(x)] wahr
[( )] falsch


Ändern und ergänzen Sie folgendes Programm nun so, dass der if-Block dann ausgeführt wird, wenn f < 5 und gleichzeitig t = 7 ist. 

```java
class If{
    public static void main(String args[]){
    int f = 3;
    if (f > 5) {
        System.out.println("Der if-Block wird gerade ausgeführt.");
        }
    }
}
```
@LIA.java(If)



### if/else-Anweisungen

Die `else`-Anweisung erweitert die Kontrollstruktur von `if`, um einen Zweig hinzuzufügen, der ausgeführt wird, wenn die Bedingung der `if`-Anweisung nicht erfüllt ist. 

<p align="center">
<img src="ifelse.png" alt="if/else-Anweisung" width="35%">
</p>


Die `if/else`-Anweisung hat die folgende Syntax:

```java
if (Bedingung) {
    // Wenn die Bedingung `true` ist
    Anweisung;
} else {
    // Wenn die Bedingung `false` ist
    Alternative_Anweisung;
}
```

Wenn die Bedingung der `if`-Anweisung wahr ist, werden die Anweisungen innerhalb des `if`-Blocks ausgeführt. Andernfalls werden die Anweisungen innerhalb des `else`-Blocks ausgeführt.

Die `else`-Anweisung ist optional und kann allein oder in Kombination mit einer `if`-Anweisung verwendet werden, um alternative Aktionen basierend auf Bedingungen auszuführen.

Beispiel:

```java
class Semester{
    public static void main(String args[]){
        int semester = 2;
        if ( semester == 1 ) {
        System.out.println("Ihr Fach ist PRO1");
        } else {
        System.out.println("Ihr Fach ist PRO2");
        }       
    }
}
```
@LIA.java(Semester)

Was müssen Sie abändern, wenn Ihr Fach dieses Semester PRO1 ist?

Die `else`-Anweisung kann auch mit verschachtelten `if`-Anweisungen verwendet werden, um komplexere Entscheidungsstrukturen zu erstellen.

```
if ( Bedingung 1 ){   
    Anweisung1;
} else {    
    if ( Bedingung 2 ){        
        Anweisung2;    
    } else {        
        Anweisung3;    
    }
}      
```

Enthält der `else`-Zweig lediglich ein weiteres if (ggf. mit else), können die Anweisungen auch fortgesetzt werden:

```
if ( Bedingung 1 ) {
        Anweisung1;
    } else if ( Bedingung 2 ){ 
        Anweisung2;
    } else if ( Bedingung 3 ){   		
        Anweisung3;
    } else {    
        Anweisung4;
    }   
```


Schreiben Sie eine if/else-Verzweigung für den folgenden Fall:

* Wenn die Temperatur unter 20°C liegt, geben Sie „Jacke!“ aus, 
* Wenn sie zwischen 20°C und 28°C liegt, geben Sie „T-Shirt!“ aus, 
* wenn sie über 28°C liegt, „Badeanzug!“


```java
class Temperatur2{
    public static void main(String args[]){
      
    }
}
```
@LIA.java(Temperatur2)


>**Der bedingte Ausdruck**

- Der bedingte Ausdruck ist keine Anweisung sondern ein Operatorausdruck, also etwas, das in einem Ausdruck (z.B. einer Formel) eingesetzt werden kann. Vergleichbar mit der WENN( ; ; ) Formel in Excel: (Bedingung) ? Ausdruck1 : Ausdruck2
 
- Wenn die Bedingung wahr ist, so ist der Wert des Ausdrucks identisch mit Ausdruck1, sonst mit Ausdruck2
Beide Ausdrücke müssen vom selben Werttyp (int, char, String, etc.) sein

```
int urlaubstage = (alter > 28 ? 30 : 25);
```

Erstellen Sie ein Programm, dass Ihnen Ihre an Urlaubstage ausgibt. Wenn Sie älter als 30 Jahre sind, haben Sie 32 Urlaubstage, wenn Sie jünger sind, nur 28 Tage. 


```java
class Urlaubstage{
    public static void main(String args[]){
      
    }
}
```
@LIA.java(Urlaubstage)



### switch/case-Statement

Die switch-Anweisung bietet eine alternative Methode zur Kontrollstruktur if, insbesondere wenn eine Variable auf verschiedene Werte geprüft werden soll und abhängig vom Wert unterschiedliche Aktionen ausgeführt werden sollen.

Die Syntax einer `switch`-Anweisung sieht folgendermaßen aus:
![](switchcase.JPG)

- Der switch-Ausdruck muss Ergebnisse vom Typ byte, short, int, char, String oder Enumeration zurückliefern
- Im case-Teil müssen Konstanten stehen (keine Variablen, Funktionsaufrufe o.ä.)
- Die Konstanten im case-Teil müssen vom gleichen Typ wie der switch-Ausdruck sein (also auch byte, short, int, char oder String)
- Kein Wert der Konstanten dieser case-Zweige darf doppelt auftreten. Die Reihenfolge ist egal.
- Nach dem case kommt eine Folge von Anweisungen; üblicherweise abgeschlossen durch ein return oder break
- break ist optional – wenn es fehlt, wird die Bearbeitung mit dem nächsten case (ohne Prüfung!) fortgesetzt – aber Vorsicht: Fehler durch vergessene break sind schwierig zu finden.
- der default-Zweig ist optional; es ist höchstens einer zulässig

Testen Sie Ihr Wissen nun, indem Sie ein Programm schreiben das den heutigen Wochentag als Variable initalisiert und dann Ihre Vorlesungen für den jeweiligen Wochentag auf der Konsole ausgibt. Nutzen Sie hierfür am Besten Eclipse. Wenn Sie wollen, können Sie es aber auch direkt im Workbook erstellen.

```java
class Stundenplan{
    public static void main(String args[]){
      
    }
}
```
@LIA.java(Stundenplan)


### Zählschleife ("normale for-Schleife")
Die Schleife wird von einer Anfangszahl bis zu einer Endzahl mit einer vorgegebenen Schrittweite wiederholt.

<p align="center">
<img src="forSchleife.png" alt="For-Schleife" width="70%">
</p>


Im Code sieht dies dann so aus:

```java
class Zaehlschleife{
    public static void main(String args[]){
        for (int i = 0; i < 10; i++){
          System.out.println(i);
        }
    }
}
```
@LIA.java(Zaehlschleife)

Wie müssen Sie das Programm abändern, um die ungeraden Zahlen von 1 bis 20 aufzusummieren?


>**Anmerkungen**

- Eine im Schleifenkopf deklarierte Variable ist nur innerhalb der Schleife sichtbar.
- `break` verlässt die Schleife
- `continue` springt zum Ende der Schleife
- Teile des Kopfes können leer bleiben (z.B. stellt for(;;) eine Endlosschleife dar).

**Weiteres Beispiel**

Was wird im folgenden Programm berechnet?

```java
class Zaehlschleife2{
    public static void main(String args[]){
        int n = 4;
        int fakultaet = 1;
        for(int i = 1; i<=n; i++) {
            fakultaet *= i;
        }
        System.out.println(n + "! = " + fakultaet);
    }
}
```
@LIA.java(Zaehlschleife2)


### For-Each-Schleife (Mengenschleife)

Die `for-each`-Schleife benötigt eine Sammlung gleichartiger Objekte. Ein Array, das im Kapitel `Arrays` besprochen wird, ist ein Beispiel hierfür. Im Vorgriff wird die Kontrollstruktur trotzdem bereits an dieser Stelle erklärt. Gehen Sie zu diesem Kapitel nochmals zurück, sobald Sie das Kapitel `Arrays` durchgearbeitet haben. 

Die `for-each`-Schleife führt den Rumpf für jedes Element der angegebenen Menge aus. Es ist somit nicht erforderlich einen Index oder die Größe des Arrays zu berücksichtigen. Dies hilft, Fehler zu vermeiden. 



```java
class ForEach{
    public static void main(String args[]){
        String[] array = {"eins", "zwei", "drei"}; //Dies ist ein Array und wird im nächsten Kapitel erklärt
        for(String wort : array) {
            System.out.println(wort);
        }
    }
}
```
@LIA.java(ForEach)

Die `for-each`-Schleife schauen wir uns später noch genauer an, wenn wir verschiedene Mengen betrachten, z.B. im Zusammenhang mit Collections.

Erklärung für Fortgeschrittene: Intern wird bei der `for-each`-Schleife ein Iterator benutzt, welcher automatisch durch die Sammlung der gleichartigen Objekte zählt und die Schleife beendet, wenn alle Elemente durchlaufen sind. Iteratoren schauen wir uns auch später an. 


### While-Schleife
Die while-Schleife wird verwendet, um einen Codeblock wiederholt auszuführen, solange eine bestimmte Bedingung erfüllt ist. Die Bedingung wird vor jeder Ausführung des Codeblocks überprüft und muss ein boolescher Ausdruck sein.

<p align="center">
<img src="while.png" alt="While-Schleife" width="25%">
</p>


Schauen Sie sich folgendes Programm an. Was passiert hier?

```java
class While{
    public static void main(String args[]){
        int zaehler = 15;
        while (zaehler < 20) {
            System.out.println(zaehler);
            zaehler++;
        }
    }
}
```
@LIA.java(While)

Können Sie es so modifizieren, dass alle geraden Zahlen ausgegeben werden?

<p align="center">
<img src="while2.png" alt="While-Schleife-Beispiel" width="25%">
</p>

Können Sie obiges Bild als Code darstellen?

```java
class WhileBeispiel{
    public static void main(String args[]){

       
    }
}
```
@LIA.java(WhileBeispiel)

>**Die "ewige" while-Schleife**

Bei der ewigen while-Schleife wird die while-Anweisung  solange wiederholt, bis die Bedingung ´false´ liefert. Dieser Fall tritt hier jedoch nie ein, so dass das Programm immer weiter läuft.

<p align="center">
<img src="ewigeWhile.png" alt="ewige While-Schleife" width="20%">
</p>


>**Anmerkungen**

- Die Bedingung der `while`-Schleife wird vor der Ausführung des Codeblocks überprüft. Wenn die Bedingung falsch ist, wird der Codeblock nicht ausgeführt und die Schleife wird beendet.
- Es ist wichtig, sicherzustellen, dass sich die Bedingung im Verlauf der Schleife ändert, um eine Endlosschleife zu vermeiden.
- `break` kann verwendet werden, um die Schleife vorzeitig zu beenden, und `continue` springt zum nächsten Schleifendurchlauf.

Die `while`-Schleife ist besonders nützlich, wenn die Anzahl der Iterationen im Voraus nicht bekannt ist, sondern von einer Bedingung abhängt.


### Do-While-Schleife
Die Do-While-Schleife ist eine Schleife mit Test der Bedingung am Ende des Schleifenkörpers. Das bedeutet, die Schleife wird mindestens einmal durchlaufen. 

Sie hat folgende Syntax:

```
do {
  Anweisung;
} while (Bedingung);
```

Die Schleife wird solange durchlaufen, solange die Bedingung wahr ist. Wie immer muss die Bedingung muss ein boolescher Ausdruck sein. Weiterhin muss die Anweisung die Bedingung ändern, sonst hat man eine Endlosschleife.

<p align="center">
<img src="dowhile.png" alt="Do-While-Schleife" width="20%">
</p>


Welche Ausgabe erzeugt folgendes Beispiel?

```java
class DoWhileBeispiel{
    public static void main(String args[]){
        int z = 0;
        do {
            System.out.println("Ausgabe ist: " + z);
            z = z+1;
        } while (z<5);

        System.out.println("-------------------");
        System.out.println("Zu Ende ist bei: " + z);     
    }
}
```
@LIA.java(DoWhileBeispiel)

### Beispiele

Machen Sie sich mit folgendem Coding vertraut und überlegen Sie, was die Ausgabe ist. 

```java
public class Anwendung2_For {
	public static void main(String[] args) {
		for (int i = 1 ; i < 4 ; i = i + 1) {
			System.out.println("i = " + i);
		}	
	}
}
```
@LIA.java(Anwendung2_For)

Überlegen Sie danach, wie Sie obigen Code in eine äquivalente `while`-Schleife und anschließend in eine äquivalente `do-while`-Schleife umbauen können.

```java
public class Ueberlegung{
	public static void main(String[] args) {
    // hier können Sie die Schleifen ausprobieren

    }	
}
```
@LIA.java(Ueberlegung)

Die Lösungen finden Sie untenstehend. Zunächst die `while`-Schleife:

```java
public class Anwendung1_While{
	public static void main(String[] args) {
		int i = 1;	
		while (i < 4) {
			System.out.println("i = " + i);
			i = i + 1;
        }
    }	
}
```
@LIA.java(Anwendung1_While)

Und nun die `do-while`-Schleife:  

```java
public class Anwendung3_DoWhile{
	public static void main(String[] args) {
        int i = 1;
		boolean mindestensEinmal = true;

		do {
			if (mindestensEinmal == true) {
				System.out.println("i = " + i);
			}
			i = i + 1;
		} while (i < 4);
    }	
}
```
@LIA.java(Anwendung3_DoWhile)

Nun schauen wir den Ersatz einer `if`-Bedingung durch eine `while`-Schleife:

```java
public class Anwendung1_If {
	public static void main(String[] args) {
		int i = 3;

		if (i < 18) {
			System.out.println("noch nicht volljährig");
		}
	}
}
```
@LIA.java(Anwendung1_If)

Verwenden Sie nun ausschließlich eine `while`-Schleife. Das Ergebnis soll das gleiche sein:

```java
public class Ueberlegung2{
	public static void main(String[] args) {
    // hier können Sie die while-Schleife ausprobieren

    }	
}
```
@LIA.java(Ueberlegung2)

Hier finden Sie die Lösung:

```java
public class Anwendung2_While{
	public static void main(String[] args) {
		int i = 3;
		boolean nurEinmal = true;

		while (i < 18 && nurEinmal == true) {
			System.out.println("noch nicht volljährig");
			nurEinmal = false;
		}
	}
}
```
@LIA.java(Anwendung2_While)

Wenn Sie diese Beispiele verstanden haben, können Sie zu den Übungen weiter gehen.

### Übungen

**Aufgabe 1  
Berechnen Sie die Summe aller Zahlen von 0 bis zu einer vorgegebenen größten Zahl. Für das Beispiel 5 wäre das also 0+1+2+3+4+5 = 15.

Lösen Sie das Problem auf mindestens drei verschiedene Arten. 

**Weitere Aufgaben:**   Machen Sie die Aufgaben aus der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus Kapitel 02.



### Ablage 

Wann wird welche Schleife verwendet?

* while -> Anzahl Durchläufe ist zu Beginn unbekannt
* for -> Anzahl Durchläufe ist zu Beginn bekannt	
* for each -> Zugriff auf die Elemente einer Menge
* do-while -> Anzahl Durchläufe ist zu Beginn unbekannt, aber ein Durchlauf ist mindestens notwendig


## Arrays

Schauen Sie sich folgenden Code an und überlegen Sie sich folgende Fragen, bevor Sie weiterlesen:

- Was passiert hier? Gehen Sie den Code durch und versuchen Sie diesen nachzuvollziehen!
- Welches Anwendungsszenario könnte hier wiedergegeben sein?
- Worin bestehen die Vor- und Nachteile in diesem Code?


```java
class Arrays{
    public static void main(String args[]){
        int wpmMo = 55;
        int wpmDi = 57;
        int wpmMi = 49;
        int wpmDo = 63;
        int wpmFr = 0;
        int wpmSa = 56;
        int wpmSo = 70;

        int sum = 0;
        sum += wpmMo;
        sum += wpmDi;
        sum += wpmMi;
        sum += wpmDo;
        sum += wpmFr;
        sum += wpmSa;
        sum += wpmSo;

        int avg = sum / 7;
        System.out.println(avg);
    }
}
```
@LIA.java(Arrays)

Ein mögliches Anwendungsszenario könnte sein:

Sie haben gemessen, wie schnell Sie Java-Code tippen können und sind dabei wie folgt vorgegangen:

- Täglich üben und `wpm` messen
- Wert in einer Variable für diesen Tag eintragen
- Summe über alle Tages-Variablen bilden
- Durchschnitt berechnen

Sie können dies selbst ausprobieren. Gehen Sie auf [Speedtyper](https://www.speedtyper.dev/) und testen Sie Ihre Tippgeschwindigkeit. Absoliveren Sie diese Übung immer wieder, um sich zu verbessern.

Doch nun zurück zum Code: Das ist ziemlich repetetiv, denn neben der vielen Tipparbeit ist das auch noch:

- Fehleranfällig: einen Tag vergessen, einen Tag doppelt nehmen
- Unflexibel: was ist, wenn wir länger als exakt eine Woche üben?

Für sich wiederholende Berechnungen haben wir bereits die Schleife kennengelernt. Dabei konnten wir z.B. einen Zähler hochzählen. Wiederholen Sie: Was passiert hier?

```java
class SchleifeWiederholung{
    public static void main(String args[]){
        int zaehler = 0;
        while(zaehler < 7) {
            System.out.println(zaehler);
            zaehler++;
        }
    }
}
```
@LIA.java(SchleifeWiederholung)

Mit Arrays gibt es eine Datenstruktur, bei der wir mit Hilfe eines solchen Zählers auf verschiedene Variablen zugreifen können. Statt einzelne Variablen für jeden Tag anzulegen, speichern wie die `wpm` nun besser in einem Array:

```
int[] wpm = {55, 57, 49, 63, 0, 56, 70};
```

Im Speicher wird Platz für 7 direkt hintereinanderliegende `int`-Werte reserviert und befüllt:

<!-- data-type="None" -->
| Index  | 0 | 1 | 2 | 3 | 4 | 5 | 6 |
|:-------|---|---|---|---|---|---|---|
| Wert   | 55| 57| 49| 63| 0 | 56| 70|


Ein Array mit 7 Elementen, kann man sich in etwa so vorstellen: 

<p align="center">
<img src="array-1.png" alt="Array" width="55%">
</p>

Unser konkretes Array sieht dann so aus:

<p align="center">
<img src="array-2.png" alt="Array befüllt" width="45%">
</p>

Mit Hilfe des Index können wir auf die Werte zugreifen:

```
// Der Wert für Montag ist der erste Wert - wir fangen immer bei 0 an zu zählen
wpm[0];
```

Variablen vom Array-Typ haben eine  `.length`-Eigenschaft, die angibt wie viele Werte vorhanden sind:

```
wpm.length
```

Nun können wir eine Schleife verwenden, um den Mittelwert zu bilden:

```java
class Mittelwert{
    public static void main(String args[]){
        int i = 0;
        int sum = 0;
        int[] wpm = {55, 57, 49, 63, 0, 56, 70};
            while(i < wpm.length) { // < statt <= weil wir bei 0 anfangen zu zählen
                sum += wpm[i];
                i++;
            }
        int avg = sum / wpm.length; // Durch Verwendung von .length statt 7 sind wir flexibel
        System.out.println("Der Durchschnitt ist: " + avg);
    }
}
```
@LIA.java(Mittelwert)

* Versuchen Sie diesen Code nachzuvollziehen. 

* Erstellen Sie nun ein eigenes Programm, in welchem Sie ein Array der Länge 10 mit beliebigen Werten befüllen und die Werte des Array dann aufsummieren. Nutzen Sie hierfür eine geeignete Schleife. Geben Sie die Summe anschließend auf der Konsole aus.

### Arrays: Basics

>**Datentyp von Arrays**

Der Datentyp eines Arrays ergibt sich aus dem Basisdatentyp (der Datentyp jedes einzelnen Elements) mit angehängten eckigen Klammern `[]`, also z.B.
`int[], double[], boolean[], char[]`.

>**Initialisierung von Arrays**

Arrays müssen immer initialisiert werden, sonst passiert sowas:

```java
class ArrayKaputt{
    public static void main(String args[]){
        int[] meinArray;
        System.out.println(meinArray);
    }
}
```
@LIA.java(ArrayKaputt)


Initialisieren können wir entweder mit Werten/Literalen, wie oben bei `wpm` oder z.B.:

```
char message[] = {'H', 'a', 'l', 'l', 'o'};
```

Oder per Schlüsselwort `new` - hier wird Speicher reserviert aber keine Werte hinterlegt:

```
double[] tagesTemperaturen2022 = new double[365];
```

Die Größe lässt sich nicht nachträglich nicht mehr ändern (hier 365).

<br>

Auf einzelne Werte wird per Zahl zugegriffen:

```
message[1] //wäre in dem Fall der Buchstabe a
```

Eine einzelne Position im Array verhält sich wie eine Variable - letztendlich lässt sich über die Adresse des Arrays, den Index und die Größe jedes Elements ja auch die Speicheradresse ermitteln. Somit kann ein Arrayzugriff auch links vom Zuweisungsoperator `=` stehen:

```
tagesTemperaturen2022[30] = 8.5;
```

Die Anzahl der Element im Array `a` ergibt sich mit `a.length`. Niemals nehmen wir ein Literal mit der aktuellen Länge! Das erste Element befindet sicht immer an Position 0. Somit ist das letzte Element an Position `length - 1`:

```
message[message.length - 1]
```

>**Ausgabe von Arrays**

Es gibt verschiedene Möglichkeiten, Arrays auszugeben. Eine davon, die Ihnen bereits bekannt ist, ist diese:

```
int [] liste = {0, 1, 2};		
System.out.println(liste[0]);	
System.out.println(liste[1]);	
System.out.println(liste[2]);
```
Diese Methode ist jedoch nicht besonders effizient. Daher verwenden wir Schleifen, um die Effizienz zu verbessern:

```
int zaehler = 0;
while (zaehler < 3) {
    zaehler++;
}
```

Durch die Kombination des Arrays mit einer Schleife erhalten wir dann folgende Ausgabe:

```
int [] liste = {0, 1, 2};
int zaehler = 0;
while (zaehler < 3) {
    System.out.println(liste[zaehler]);
    zaehler++;
}
```

>**Übung**

Versuchen Sie nun die obigen Erkenntnisse in ein lauffähiges Programm zu packen. Probieren Sie an dieser Stelle auch explizit die Verwendung einer for-each-Schleife aus. Wiederholen Sie bei Bedarf das entsprechende Kapitel. 

```java
class MeinArray{
    public static void main(String args[]){
        
        
    }
}
```
@LIA.java(MeinArray)

### Wachsende Arrays

Arrays werden bei der Erzeugung mit fester, nicht mehr änderbarer Größe erzeugt. Möchte man die Größe eines Array-Objektes nachträglich ändern, so muss neues Array-Objekt erzeugt werden und das
bisherige Array in das neue Array umkopiert werden. Diese Aktionen werden von der Standardfunktion `copyOf` effizient erledigt. Die Klasse `java.util.Arrays` enthält zahlreiche Funktionen zur Manipulation von Arrays wie z.B. das eben erwähnte `copyOf`. 

>**Hintergrund** 
In Java gibt es bereits sehr, sehr viele vorgefertigte Methoden, die wir nutzen können. Erklärungen hierzu finden Sie unter: [Java API](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/module-summary.html). Mit diesem Link werden wir das kommende Jahr sehr viel arbeiten. 
Unter java.util finden Sie die Klasse `Arrays`, die Methoden zum Manipulieren von Arrays enthält. So auch das oben genannte `java.util.Arrays. 

* Welche Länge hat in folgendem Code welches Array?
* Was ist die Ausgabe der Schleife?

```java
import java.util.Arrays; // durch die Importanweisung wird die genutzte Methode gefunden
class ArrayKopie{
    public static void main(String args[]){
        int[] meinArray = {0,1,2,3,4,5};
        int[] neuesArray = Arrays.copyOf(meinArray,meinArray.length*2);
        
        System.out.println("Länge Array: " + meinArray.length);
        System.out.println("Länge neues Array: " + neuesArray.length);

        for(int i:neuesArray) {
        	System.out.println(i);
        }       
    }
}
```
@LIA.java(ArrayKopie)

Mit der Methode `arraycopy` der Klasse `System` können Sie die Kopie noch genauer steuern:

```java
class ArrayKopie2{
    public static void main(String args[]){
        int[] meinArray = {0,1,2,3,4,5};
        int[] neuesArray = new int[meinArray.length*2];
        System.arraycopy(meinArray, 0,neuesArray, 0,meinArray.length);
        for(int i : neuesArray) {
        	System.out.println(i);
        }   
    }
}
```
@LIA.java(ArrayKopie2)

* Suchen Sie die Methode `arraycopy` in der Java API und finden Sie heraus, was die Argumente in der Methode bedeuten. 
* Ändern Sie die Argumente ab und schauen Sie sich das ergebnis an. 

Hinweis: die Argumente einer Methode sind die Parameter, die in den Klammern der Methode stehen. Methoden lernen wir bald genauer kennen. 

Lösungshinweis: Sie finden die Methode im Module `java.base`, im Paket `java.lang` und im Klassensystem in der Klasse `System`, welche sich unterhalb von `java.lang.Object` befindet.


### Mehrdimensionale Arrays

Arrays können auch mit mehrdimensionalen Indizes gebaut werden - in Java sind das technisch gesehen Arrays mit einem weiteren Array als Basisdatentyp. Beispiele für Anwendungen:

- Tabellen, z.B. Stundenplan mit Tagen als Spalten und Vorlesungsblöcken als Zeilen und Vorlesungsbezeichnung
- Bilder - 2 dimensionale Anordnungen von Pixel (Farbwerten)
- Welten in Computerspielen: zwei- oder dreidimensionale Anordnungen von Feldern

Durchwandern können wir diese Arrays mit geschachtelten Schleifen.

Ein zweidimensionales Array kann auch wieder per Literale oder per `new` konstruiert werden. 

Machen Sie sich mit folgendem Coding vertraut:

```java
class Tabelle{
    public static void main(String args[]){
		int[][] tabelle = 	{{11, 12, 13},
							{21, 22, 23},
							{31, 32, 33}};

		System.out.println(tabelle[1][2]);
    }
}
```
@LIA.java(Tabelle)

* Welches Element wird hier ausgegeben? 
* Schreiben Sie eine doppelte Schleife, so dass alle Elemente ausgegeben werden.

Hier finden Sie zwei weitere Beispiele: 

```
// 5x5 Array mit true (Schwarz) / false (Weiss) Werten
boolean[][] schwarzweissBild = {{false, false, true, false, false}, 
                                {false, true, false, true, false},
                                {true, true, true, true, true},
                                {true, false, false, false, true},
                                {true, true, true, true, true}};

// Array für Klausurpunkte
int nStudierende = 30;
int nAufgaben = 10;
int[][] punkte = new int[nStudierende][nAufgaben];
```

### Übungen

**Weitere Aufgaben: **  Machen Sie die Aufgaben aus der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus Kapitel 03.


## Strings

Bisher haben wir uns mit primitiven Datentypen befasst, wie z.B. int, double und char, um einfache Werte zu speichern. Mit dem primitiven Datentyp char können wir einzelne Zeichen speichern, während ein char-Array Zeichenfolgen einer festen Länge speichern kann.

Für die Arbeit mit Zeichenketten bietet Java die Klasse `String` an. Im Gegensatz zu primitiven Datentypen stellt die Klasse `String` einen Referenztyp dar. Das bedeutet, dass eine Variable vom Typ `String` nicht den tatsächlichen String selbst speichert, sondern eine Referenz auf das `String`-Objekt in der Speicherstruktur.

Objekte eines Referenztyps, wie z.B. String-Objekte, können Methoden bereitstellen, die auf sie angewendet werden können. Die `String`-Klasse stellt eine Vielzahl von Methoden zur Verfügung, um Zeichenketten zu manipulieren, vergleichen, suchen und mehr.

Was passiert in folgendem Programm? 

* Versuchen Sie das Programm nachzuvollziehen.
* Welche Ausgaben erscheinen auf der Konsole?
* Wie wurden die einzelnen Strings gebaut?

```java
class StringBeispiel{
    public static void main(String args[]){
        String name_1 = new String("Speicherfresser"); 
        String name_2 = "String-Pool"; 
        char[] buchstaben = { 'E', 'i', 'n', 'z', 'e', 'l', 'n'};
        String name_3 = new String(buchstaben); 
        String name_4 = "Bau" + "meister"; 

        System.out.println(name_1);  
        System.out.println(name_2); 
        System.out.println(name_3); 
        System.out.println(name_4); 
    }
}
```
@LIA.java(StringBeispiel)


### Nutzung von Zeichenketten

Wir schauen uns in diesem Kapitel etwas genauer an, wie Strings erzeugt werden und wo diese gespeichert werden.

- Mit dem Konstruktoraufruf `new String(…)` werden immer neue Stringobjekte angelegt.

- `String`-Literale (Zeichenketten in doppelten Anführungszeichen) werden im String-Pool verwaltet.

- Alle Java-Objekte werden auf dem Speicherbereich namens Heap angelegt

Merke: Die Objekterzeugung mit `new()` umgeht den String-Pool

Beachten Sie dabei folgende Abbildung. Versuchen Sie diese nachzuvollziehen. Wo wird welcher String gespeichert?

![](zeichenketten_1.JPG)

Schauen Sie das einführende Programm erneut an. Können Sie nun die Kommentare nachvollziehen?

```java
class StringBeispiel{
    public static void main(String args[]){
        String name_1 = new String("Speicherfresser"); // new belegt neuen Speicherplatz
        String name_2 = "String-Pool"; // Zeichenkettenkonstanten werden wiederverwendet

        char[] buchstaben = { 'E', 'i', 'n', 'z', 'e', 'l', 'n'};
        String name_3 = new String(buchstaben); // new belegt neuen Speicherplatz

        String name_4 = "Bau" + "meister"; // Einzelteile werden wiederverwendet,
                                        // aber + Operator erzeugt neues Objekt
        System.out.println(name_1); //Ausgabe: Speicherfresser 
        System.out.println(name_2); //Ausgabe: String-Pool
        System.out.println(name_3); //Ausgabe: Einzeln
        System.out.println(name_4); //Ausgabe: Baumeister
    }
}
```
@LIA.java(StringBeispiel)

>**Unveränderbare Zeichenketten**

Objekte der Klasse `String` sind unveränderlich.

- Methoden, die einen String ändern, liefern ein neues Objekt zurück.
- Beispiel: Methode replace()
- Versuchen Sie nun auch folgenden Code nachzuvollziehen, welche Ausgaben werden generiert?

```java
class Mutter{
    public static void main(String args[]){
        String mama = "Mutter";
        String schraubenteil = "Mutter";
        System.out.println(mama == schraubenteil); 
        mama.replace("Mutter", "Mother"); // Das Objekt, auf das mama zeigt, bleibt unverändert

        System.out.println(mama); 
        System.out.println(schraubenteil); 
        System.out.println(mama == schraubenteil); 
        mama = mama.replace("Mutter", "Mother"); // Die Variable mama zeigt auf ein anderes Objekt
        System.out.println(mama); 
        System.out.println(mama == schraubenteil); 
    }
}
```
@LIA.java(Mutter)



### Veränderbare Zeichenketten

- Objekte der Klassen `StringBuffer` und `StringBuilder` sind veränderbar. Analysieren Sie folgendes Beispiel (vgl. Schröder programmiert Java, S. 163):

```java
class StringBilder{
    public static void main(String args[]){
        StringBuilder stringBuilder = new StringBuilder();
        stringBuilder.append("String"); //append() und insert() verändern dynamisch das darunterliegende Objekt
        stringBuilder.append("-");
        stringBuilder.append("Bilder");
        stringBuilder.insert(8, "u");
        System.out.println(stringBuilder.toString());
    }
}
```
@LIA.java(StringBilder)


- Die Objekte können dynamisch ihre Größe ändern.
- Optional kann man im Konstruktor der Klassen `StringBuffer` und `StringBuilder` bereits eine Größe mitgeben. Konstruktoren lernen wir im Kapitel Konstruktoren bei den Objekten.

- Die Klassen `StringBuffer` und `StringBuilder` bieten die gleichen Methoden an.
- Die beiden Klassen unterscheiden sich in der Arbeitsweise:

  - `StringBuffer` ist synchronisiert (= Thread-sicher bei zeitgleichem Zugriff mehrerer Programmteile)

  - `StringBuilder` ist nicht synchronisiert (und etwas schneller)
- Weitere Methoden sind zum Beispiel:

  - delete(), deleteCharAt()

  - replace()

  - usw.



### Zeichenkettenoperationen

Beispiel:

```
String satz = „Dies ist ein Satz.“;
```

Was für Methoden können auf diesem String aufrufen werden? 

Methoden: `charAt(int index)`, `length()`, `substring(int beginIndex)` etc.

- Zugriff auf ein Zeichen: `charAt()`
- Länge eines Strings: `length()`
- Zerlegen eines Strings: `substring()`, `split()`

Suchen Sie in der Java Documentation nach weiteren Methoden, die Sie auf Strings aufrufen können. Überlegen Sie sich, was jeweils mit dem String passiert. Betrachten Sie auch hierzu folgendes Beispiel und versuchen Sie die einzelnen Schritte nachzuvollziehen.


```java
public class Zeichenkettenoperationen {
    public static void main(String[] args) {
        String satz = "Das ist ein Satz";
        String[] woerter = satz.split(" "); //Teilt den String bei allen Leerzeichen
        for(int i = 0; i < woerter.length; i++) {
            System.out.println(woerter[i]);
        } 

        String teil = satz.substring(6, 10); //Beginn des Substrings an Position 6 und Ende an Position 10
        System.out.println(teil);
   }
}
```
@LIA.java(Zeichenkettenoperationen)

- Vergleichsoperationen in Java funktionieren nur für primitive Datentypen und nicht für Referenztypen wie z.B. String. Dies bedeutet, Zeichenketten vergleicht man immer mit `equals()`, nicht mit ==. Der Vergleich mit == vergleicht die Gleichheit der zugrunde liegenden Objekte, während die Methode `equals()` die Gleichheit der Strings überprüft.
- Wenn Teile von Strings verglichen werden sollen, kann man z.B. `endsWith()`, `startsWith()` oder `regionMatches()` verwenden.
- Mit Hilfe der Methoden `indexOf()`, `lastIndexOf()`, `contains()` kann man in Strings suchen.
- Veränderungen können mit `replace()`, `replaceFirst()`, `replaceAll()` erfolgen.

>**Aufgabe**

Suchen Sie sich geeignete Methoden in der Java API der Klasse [String](https://docs.oracle.com/en/java/javase/21/docs//api/java.base/java/lang/String.html)
um den String "Iss" jeweils geeignet weiter zu verarbeiten. Dabei sollte jeweils das Wort im Kommentar erscheinen.

```java
public class Iss {
    public static void main(String[] args) {
        String satz = "Iss";
        // Eis

        // Heiss

        // Heisser

        //Hosenschei**er
   }
}
```
@LIA.java(Iss)

Die Übung entstammt dem Buch Schrödinger programmiert Java von Philipp Ackermann (S. 152). Dort finden Sie auch eine Lösung.

Hinweis: Benutzen Sie u.a. die Methoden substring(), toLowerCase(), replaceAll() und konkatenieren Sie geeignet die Strings.


**Weitere Beispiele**

Versuchen Sie nun auch folgenden Code nachzuvollziehen. Die Idee hiervon entstammt ebenfalls aus dem Buch Schrödinger programmiert Java (S. 145). Welche Ausgaben werden generiert und warum?

```java
class StringWeiteresBeispiel{
    public static void main(String args[]){
        String wort = "Urinstinkt";
        boolean sindGleich = wort.equals("Ur" + "instinkt");
        System.out.println(sindGleich); 

        System.out.println(wort.startsWith("Urin")); 
        System.out.println(wort.endsWith("stinkt")); 

        System.out.println("Autoschlüssel".regionMatches(5, "Schlüsselbund", 1,3)); 
        System.out.println(wort.indexOf('i')); 
        System.out.println(wort.lastIndexOf('i')); 
    }
}
```
@LIA.java(StringWeiteresBeispiel)

### Übungen

Machen Sie die Aufgaben aus der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus Kapitel 04.


## Exkurs: Debugging in Eclipse

Debugging ist ein unverzichtbarer Schritt in der Softwareentwicklung, bei dem Fehler oder Bugs in einem Programm gefunden und behoben werden. Es ist von entscheidender Bedeutung, um sicherzustellen, dass die Software reibungslos funktioniert und die gewünschten Ergebnisse liefert. Durch Debugging können Entwickler Probleme erkennen, verstehen und lösen, was letztendlich zu einer verbesserten Qualität und Benutzererfahrung der Software führt.

>**Breakpoints**

- Ein Breakpoint ist wie eine Art Halt-Zeichen, das man in einen Code einfügt, um ihn an einer bestimmten Stelle anzuhalten. Wenn das Programm während der Ausführung auf diesen Breakpoint trifft, hält es an und man kann den Zustand des Codes genauer untersuchen.
- Um Breakpoints zu setzen, klicken Sie mit der rechten Maustaste in die vertikale Leiste neben dem Code und drücken `Toggle Breakpoint`, wie im Bild gezeigt.
- Alternativ können Sie auch doppelt auf die Leiste klicken, um einen Breakpoint zu setzen oder mit der Maus über die Zeile gehen und die Tastenkombination `Strg + Umschalt + B` verwenden.

![](Debugger-1.png)

- Der blaue Punkt kennzeichnet einen Breakpoint:

![](Debugger-2.JPG)



>**Debuggen**

- Starten Sie Ihr Programm im Debug-Modus, indem Sie auf den Käfer (Bug) neben dem Run-Button klicken und darauf die Debug-Perspective öffnen (Switch klicken).

![](Debugger-3.png)

- Step Over: Mit dieser Funktion kann man den nächsten Befehl ausführen, ohne in die Details einer Methode oder Funktion einzutauchen. Wenn man Step Over verwendet und die nächste Anweisung eine Methodeaufruf ist, wird die Methode komplett ausgeführt, und die Ausführung springt zur nächsten Zeile im aktuellen Kontext.

- Step Into: Im Gegensatz zu Step Over taucht man mit Step Into in die Details einer Methode oder Funktion ein. Wenn die nächste Anweisung eine Methode oder Funktion ist, springt man in diese Methode und kann die Ausführung schrittweise innerhalb dieser Methode fortsetzen.

![](Debugger-4.png)

 - Auf der rechten Seite des Debuggers können zusätzliche Informationen angezeigt werden, wie zum Beispiel aktuelle Werte von Variablen und Ausdrücken. Diese Informationen helfen dabei, den Zustand der Anwendung während des Debugging-Prozesses besser zu verstehen. Durch die Anzeige von Variablenwerten und anderen relevanten Informationen können Sie schnell erkennen, wie sich der Code verhält und potenzielle Probleme identifizieren.

![](Debugger-5.JPG)

>**Übung**

Wir benutzen das Beispiel aus dem vorherigen Kapitel um nachvollziehen, wann ein neues Objekt angelegt wird. Kopieren Sie hierzu folgendes Coding in Eclipse: 

```java
class Mutter{
    public static void main(String args[]){
        String mama = "Mutter";
        String schraubenteil = "Mutter";
        System.out.println(mama == schraubenteil); 
        mama.replace("Mutter", "Mother"); // Das Objekt, auf das mama zeigt, bleibt unverändert

        System.out.println(mama); 
        System.out.println(schraubenteil); 
        System.out.println(mama == schraubenteil); 
        mama = mama.replace("Mutter", "Mother"); // Die Variable mama zeigt auf ein anderes Objekt
        System.out.println(mama); 
        System.out.println(mama == schraubenteil); 
    }
}
```

Versuchen Sie nun mit Hilfe des Debuggers nachzuvollziehen, wann welche Objekte neu angelegt werden. 

Lösung: Eine detaillierte Erklärung finden Sie im Buch Schrödinger programmiert Java, ab S. 153.


## Klassen, Objekte, Methoden

Bisher bestand unser Javaprogramm aus folgenden Einzelteilen:

* Hauptklasse oder Startklasse: Oberste Struktureinheit in Java
* Hauptmethode oder main-Methode genannt: Hier läuft das eigentliche Programm ab, ohne die main-Methode läuft das Programm nicht.

In diesem Kapitel wollen wir:

* Weitere Methoden erstellen: Es können für Teilberechnungen weitere Methoden definiert werden, die dann von der main-Methode aufgerufen werden.
* Weitere Klassen erstellen, so dass diese als Ansammlung gleichartiger Objekte genutzt werden können


### Methoden

Wir haben bisher in der main-Methode gearbeitet, bzw. Methoden genutzt, die im Sprachumfang von Java bereits enthalten sind, wie z.B. die Methoden der Klasse `String`. In diesem Kapitel möchten wir nun eigene Methoden schreiben. 

Betrachten Sie hierzu folgendes Beispiel:

```java
public class KreisBerechnungen {

	public static final double PI = 3.14159265;
	
	public static void main(String[] args) {
		double radius = 3.0;
		System.out.println("Der Umfang bei einem Radius von " + radius + " ist: " + berechneUmfang(radius));
		System.out.println("Die Fläche bei einem Radius von " + radius + " ist: " + berechneFlaeche(radius));
	}

	private static double berechneUmfang(double radius) {
		double umfang = 2.0 * radius * PI;
		return umfang;
	}

	private static double berechneFlaeche(double radius) {
		double flaeche = radius * radius * PI;
		return flaeche;
	}
	
}
```
@LIA.java(KreisBerechnungen)

* Erkennen Sie im Beispiel die Methoden?
* Was passiert in diesen Methoden?
* Wo werden diese aufgerufen und mit welchen Parametern?

Der Klassenkörper-Block besteht aus Variablendeklarationen und Methoden. Die in der Klasse deklarierten und gegebenenfalls initialisierten Variablen sind in allen Methoden der Klasse sichtbar, wie im Beispiel PI. Die Methoden der Klasse bestehen aus der Methodendeklaration und dem Methodenkörper/Methodenrumpf ( Block, eingegrenzt mit { } ). Allgemein besteht eine Methodendeklaration aus: 

1. Modifikatoren public oder private, evtl. static
2. Rückgabetyp
3. Methodennamen
4. Parameterliste
5. Methodenrumpf

Wir betrachten erneut folgende Methode:

```java
    //Modifikatoren: private und static
    //Rückgabetyp: double
    //Methodenname: berechneUmfang
    //Parameterliste: double radius
	private static double berechneUmfang(double radius) { 
		double flaeche = radius * radius * PI;
		return flaeche;
	}
```



**1. Modifikatoren**

Es gibt folgende Sichtbarkeitsmodifikatoren, welche angebeben, von wo aus die Methode aufgerufen werden kann:

* public: von überall aufrufbar
* protected: innerhalb des Pakets oder Unterklassen in einem anderen Paket (→ später: Vererbung)
* ohne („package private“): innerhalb des Pakets
* private: innerhalb der Klasse

Weiterhin gibt es auch statische und nicht-statische Methoden:

* static: der Klasse zugeordnet
* ohne Modifier („non-static“): den Objekten zugeordnet (→ später: Objektorientierung)

**2. Rückgabetyp**

Der Rückgabetyp gibt an, welchen Typ das Ergebnis haben wird. Rückgabetypen können sein:

* die primitiven Typen
* Referenztypen
* der spezielle „Nichttyp“ void (= kein Rückgabewert)

Hat eine Methode einen Rückgabetyp (nicht void), so muss der zurückzugebende Wert durch `return ergebnis;` definiert werden, im Beispiel `return flaeche;`

**3. Methodennamen**

Beachten Sie bei der Wahl eines Methodennamen folgende Konventionen:

* Methoden beginnen mit einem kleinen Buchstaben
* Längere Namen werden in CamelCase geschrieben
* Der Name beschreibt, was die Methode tut
* Typischerweise enthalten Namen ein Verb, zum Beispiel: public String getName();

**4. Parameter / Aufruf der Methode**

Methodendefinition:

* „Formale“ Parameter (hier a und b) von Methoden legen fest, welche Angaben die Methode benötigt: 

```java
public static double mittelwert(double a, double b){
    return (a + b)/2;
    }
```

Methodenaufruf:

* „Aktuelle“ Parameter sind die für einen bestimmten Aufruf eingesetzten Werte, wie z.B. (10.5 → a, 5.3 → b): 

```java
double mw = mittelwert(10.5, 5.3);
```

Formale und aktuelle Parameter müssen vom gleichen Typ und der gleichen Reihenfolge sein!

**5. Methodenrumpf**

Der Methodenrumpf enthält die Anweisungen, durch `;` getrennt. Grundsätzlich darf ein Rumpf beliebig lang sein. Sinnvoll ist jedoch max. eine Bildschirmseite. Leerzeichen und -zeilen im Rumpf werden vom Compiler ignoriert, sind aber für die Lesbarkeit wichtig. Die Ausführung einer Methode startet am Anfang und endet bei `return` (oder am Ende).


>**Übungen**

1. Berechnen Sie den Mittelwert zweier Zahlen. Schreiben Sie hierfür in Eclipse ein Programm mit einer Methode `berechneMittelwert`.

2. Machen Sie die ersten Aufgaben aus der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus Kapitel 05.


>**Methoden überladen**

Namensgleiche Methoden mit unterschiedlichen Parametern nennt man überladen. 

Beispiel: 

`double mittelwert(double a, double b)`
und
`double mittelwert(double[] a)`

Der Compiler erkennt an Hand der Anzahl und der Datentypen der Parameter, welche Methode gemeint ist. Methoden mit gleichem Namen und gleichen Parametern (d.h. mit gleicher Signatur) innerhalb einer Klasse sind nicht erlaubt (auch nicht mit unterschiedlichen Rückgabetypen). 



### Objekte

Ab jetzt wollen wir objektorientiert programmieren. D.h. wir wollen Objekte formulieren, die wir wiederverwenden können. Eine Klasse dient uns hierbei als Ansammlung gleichartiger Objekte (auch Instanzen der Klasse genannt). In der Klasse werden dabei Komponenten festgelegt, aus denen jedes Objekt dieser Klasse bestehen soll. 

Jedes Objekt gehört zu einer Klasse. Die Idee dahinter ist, dass die Klasse als Bauplan verstanden werden kann, von dem beliebig viele Objekte abgeleitet werden können. Diese Objekte sind alle gleichartig. Sie besitzen die selben Datendefinitionen und führen die selben Methoden aus. Sie verhalten sich alle gleich, sie unterscheiden sich lediglich in den Werten. Der Vorteil ist: Es muss nur eine Klasse geschrieben werden, die die Daten und Methoden der zukünftigen Objekte definiert.  Von dieser Klasse können dann beliebig viele Objekte erzeugt („instanziiert“) werden.

Beispiel: 

Sie wollen ein Auto bauen. Jedes Auto hat vier Räder und eine Farbe. Die Farbe unterscheidet sich jedoch von Auto zu Auto und kann weiß, rot oder blau sein. Die Klasse Auto enthält somit den Bauplan für das Auto: Jedes Auto wird mit vier Rädern gebaut und beim Bau legen Sie fest, welche Farbe das Auto haben soll. 

Die Anzahl der Räder ist somit eine statische Variable für Ihre Klasse Auto, d.h. sie ist für alle Autos gleich. Die Farbe ist eine Objekteigenschaft des Autos und kann sich von Auto zu Auto unterscheiden. 

Der Bauplan sähe dann wie folgt aus:

```java
public class Auto {
	public static int anzahlRaeder = 4; // Klassenvarialbe, für alle Objekte der Klasse gleich
	public String farbe; // Objektvariable, auch Feld genannt (von englisch "field")

    public void fahren(){ // Objektmethode (non-static)
        System.out.println("Das Auto fährt.");
    }
}
```

Um nun ein Auto zu bauen, können Sie Objekte der Klasse `Auto` erzeugen. Dies passiert in diesem Beispiel in der Klasse `Autobauer`.

```java
public class Autobauer {
	public static void main(String[] args) {
		Auto meinAuto = new Auto(); // Erzeugung eines neuen Auto-Objekts mit dem new-Konstruktor
		meinAuto.farbe = "weiß"; // Der Zugriff auf die Felder des Objekts erfolgt mit einem Punkt "."

		Auto deinAuto = new Auto(); // Erzeugung eines weiteren Auto-Objekts
		deinAuto.farbe = "blau"; // Das zweite Auto hat eine andere Farbe, Achtung: Die Farbe kann nur in Zusammenhang mit einem Objekt abgefragt werden

		System.out.println(meinAuto.anzahlRaeder);  
		System.out.println(meinAuto.farbe);
		meinAuto.fahren(); // Zugriff auf die Methoden erfolgt durch die Qualifikation mit der Objektvariablen - meinAuto ist das Objekt, fahren() der qualifizierte Zugriff
        

		System.out.println(deinAuto.anzahlRaeder);
		System.out.println(deinAuto.farbe);
	}
}
```

Hier werden zwei Auto-Objekte erzeugt:

* meinAuto mit der Farbe weiß
* deinAuto mit der Farbe blau

Jedes Auto hat automatisch vier Räder, denn dies war eine statische Variable, keine Objektvariable.
Jedes Auto hat eine eigene Farbe. Der Zugriff auf die Farbe funktioniert also nur bei Angabe des Objekts (welches Auto? meinAuto oder deinAuto).

Jedes Auto hat ferner die Methode fahren(). 

>**Übung**

Bauen Sie obiges Beispiel in Eclipse nach. Sie benötigen hierfür zwei Klassen. Legen Sie zwei Autos mit unterschiedlichen Farben an. Greifen Sie auf die Felder des Autos zu und geben Sie diese aus. Lassen Sie das Auto fahren. 


### Konstruktoren

Objekte werden oft mit bestimmten Werten erzeugt. Hierbei unterstützt der Konstruktor. 
Der Konstruktor ist eine Art spezielle Methode, die speziell zur Initialisierung eines Objekts verwendet wird. Dieser weist einige Besonderheiten / Eigenschaften auf:

* Wird immer mit einer Objekterzeugung verwendet (new-Operator)
* Kann nicht außerhalb einer Objekterzeugung verwendet werden
* Name ist immer gleich Klassenname
* Hat keinen Rückgabetyp
* Wird nicht vererbt (siehe Kapitel Vererbung)
* Java stellt immer einen Standardkonstruktor (ohne Parameter) bereit
* Wird ein eigener Konstruktor definiert, steht der Standardkonstruktor nicht mehr zur Verfügung

Konstruktoren können direkt mit Parametern initalisiert werden. Am Beispiel des Autos:

```java
public class Auto {
	public static int anzahlRaeder = 4; 
	public String farbe; 

    //Konstruktor
	public Auto(String farbe) {
		this.farbe = farbe; //Zugriff mit this auf das Objekt selbst
	}

    public void fahren(){ 
        System.out.println("Das Auto fährt.");
    }
}
```

Nutzung in der Klasse Autobauer:

```java
public class Autobauer {
	public static void main(String[] args) {
		// Direkt bei der Erzeugung meines Auto-Objekts bekommt dieses die Farbe weiß
		Auto meinAuto = new Auto("weiß");
		
	}
}
```

Achtung: Sobald in der Klasse Auto ein eigener Konstruktor definiert wird, wird der Standardkonstruktor, den wir zuvor genutzt haben (ohne Parameter) nicht mehr automatisch erzeugt. 

Vorteile: 

* Im Konstruktor können wir die Objektvariablen initialisieren. 
* Wir können den Standardkonstruktor mit Standardwerten vorbelegen.
* Konstruktoren mit Parametern sind sinnvoll, wenn die Objektvariablen nicht mit Standardwerten, sondern aus den Parametern initialisiert werden sollen.

Erweitertes Beispiel: 

```java
public class Auto {

	public static int anzahlRaeder = 4;
	public String farbe;
	
    //Wird bei der Objekterzeugung keine Farbe angegeben, so ist das Auto automatisch schwarz
	public Auto() {
		this.farbe = "schwarz";
	}

    // Ein zweiter Konstruktor, der mir erlaubt, die Farbe bei der Objekterzeugung zu definieren
	public Auto(String farbe) {
		this.farbe = farbe;
	}

	public void fahren() {
		System.out.println("Das Auto fährt." + this.farbe);
	}
	
}
```

>**Übung**

* Erstellen Sie eine Klasse Laptop mit den Feldern modell, benutzer und id (welche Variablentypen brauchen Sie?)
* Es gibt auch einen Konstruktor Laptop(String modell, String benutzer).
* Die Klasse hat eine statische Variable gesamtAnzahl, die bei jedem Anlegen eines neuen Laptops hochgezählt wird 
* Das Feld id jeder Laptop-Instanz bekommt beim Anlegen des neuen Laptops den aktuellen Wert von gesamtAnzahl
* Erstellen Sie eine separate Klasse mit einer Main-Methode
* Legen Sie mehrere Laptops an und geben Sie die Laptop-IDs und Gesamtanzahl der Laptops aus


### Kapselung

Wir wollen nun sicherstellen, dass die Datenfelder nicht von außerhalb direkt zugänglich sind um unbefugten Zugriff zu verhindern. Datenfelder können somit `private` gemacht werden, damit niemand von außerhalb zugreifen kann. 
Wenn der Zustand des Objekts nun geändert oder zurück gegeben werden soll, geschieht das mit `Getter`- bzw. `Setter`-Methoden. Hierbei können auch Validierungsregeln eingebaut werden (if-Statement).

>**Getter und Setter**

Getter und Setter sind öffentliche (=public) Methoden, mit denen man den Wert der Datenfelder zurückgeben (get) oder ändern (set) kann. Als Methodennamen wählt man `getWert()` bzw. `setWert()`. 

Getter liefern den Wert einer privaten Variablen. Sie sind folgendermaßen aufgebaut: 

```
public Typ getWert(){
    return wert;
}
```

Setter setzen den Wert einer privaten Variablen. Sie sind folgendermaßen aufgebaut: 

```
public void setWert(Typ wert){
    this.wert = wert;
}
```

Der Parameter `wert` überdeckt die Instanzvariable in der Methode. Die Qualifikation mit `this` (dem Objekt selbst) erlaubt den Zugriff auf die überdeckte Variable. Das bedeutet also: Bei überdeckten Instanzvariablen bezeichnet das Schlüsselwort `this` das Objekt selbst und damit den Zugriff auf die Instanzvariablen des Objekts. 

Mit passenden Modifikatoren wird die Umgehung der öffentlichen Methoden verhindert: 
* public: von überall aufrufbar
* protected: innerhalb des Pakets oder Unterklassen in einem anderen Paket (siehe Kapitel Vererbung)
* ohne („package private“): innerhalb des Pakets
* private: innerhalb der Klasse

Man kann immer nur höchstens einen Sichtbarkeitsmodifikator verwenden. Weiterhin sollte man genau überlegen, welche Methoden von wo aufgerufen werden können sollte und somit welche Methoden private gemacht werden muss und welche öffentlich bleiben kann. Die Grundregel ist so viel wie möglich Daten zu verstecken – Nutzer unserer Klasse/unserer Objekte sehen nur das öffentliche Interface. Alles, was wir versteckt haben, können wir ändern, ohne etwas kaputt zu machen. 

Wenn wir bei Objekten immer nur Getter/Setter haben, dann lagern wir die Logik aus. Besser sind domänenspezifische Methoden, wie zum Beispiel:

* Methode `double berechneLaenge()` für Objekte einer Klasse `Linie` statt per `getStart()` und `getEnd()` den Start und Endpunkt und von diesen dann mit `getX()` und `getY()` die Koordinaten zu bekommen und dann immer wieder von neuen die Länge zu berechnen
* Methode `double bruttoPreis()` für eine Rechnung anstatt `getNettoPreis()` und `getSteuersatz()` abzufragen und dann die Berechnung selbst durchzuführen

>**Regeln zum Information Hiding**

Zusammengehörige Daten / Methoden sollten in einer Klasse zusammengefasst werden. 
Nicht zusammengehörige Daten / Funktionen sollten in verschiedene Klassen aufgeteilt werden.
Insbesondere die `main`-Methode gehört in eine separate Klasse!
Zusammengehörige Klassen werden dann in ein Paket zusammen gefasst. 
Die Daten in einer Klasse sind immer `private` deklariert. Auf diese werden kann kontrolliert über über `public` / `protected` Methoden zugegriffen werden. Unterstützende Methoden sind wiederum `private`.

![Informationhiding](Informationhiding.png)

Die Abbildung zeigt: In der Mitte sind die privaten Daten sind "gekapselt". Der graue Kreis zeigt die Zugriffsmethoden auf die private Daten. Die Klasse A greift dann auf Daten über die Zugriffsmethoden zu.

>**Beispiel**

Mit diesen Erkenntnissen erweitern wir unser Auto:

```java
public class Auto {
	private String farbe; //die Farbe unseres Autos ist nun privat

    // Getter: gibt die Farbe des Autos zurück
    public String getFarbe() {
		return farbe;
	}

    // Setter: Methode, um die Farbe des Autos zu setzen
	public void setFarbe(String farbe) {
		this.farbe = farbe;
	}
}
```

```java
public class Autobauer {
	public static void main(String[] args) {
		Auto meinAuto = new Auto();		
		meinAuto.setFarbe("weiß");
		System.out.println("Mein Auto hat die Farbe: " + meinAuto.getFarbe());
	}
}
```

Versuchen Sie dieses Beispiel nachzuvollziehen! 

* Welcher Konstruktor wird benutzt?
* Funktioniert der Zugriff mit `meinAuto.farbe`? Warum, bzw. warum nicht?
* Welche Rückgabewerte und welche Parameter haben die Methoden `setFarbe()` und `getFarbe()`?


>**Übung**

Fortführung der Übung Laptop:

* Fügen Sie nun Ihrer Laptopklasse Getter und Setter hinzu
* Ihre bereits angelegten Variablen werden nun private
* Greifen Sie nun aus der main-Methode auf die Variablen zu und geben Sie Modell, Benutzer, Laptop-ID aller Laptops aus und die Gesamtanzahl


### Speicherverwaltung

Wir haben schon den Heap als Speicherbereich für Objekte kennengelernt. Im Gegensatz zum Stack, der variablen Speicherplatz für Methoden und primitive Datentypen bereitstellt, kann der Heap dynamisch wachsen und schrumpfen, um Platz für die Erstellung und Freigabe von Objekten zu bieten.

Wenn ein neues Objekt mit dem new-Operator erstellt wird, wird Speicher im Heap allokiert, um das Objekt zu speichern. Der Zugriff auf den Heap erfolgt über eine Referenzvariable auf diese Objekte. Diese Referenzvariablen werden auf dem Stack gespeichert, während die tatsächlichen Objekte im Heap existieren.

`Haustier haustier = new Haustier();`

`haustier` ist eine Referenzvariable vom Typ `Haustier`. Der Operator `new` legt ein neues Objekt vom Typ `Haustier` auf dem Heap an. Der Zuweisungsoperator = verknüpft die Referenzvariable `haustier` mit dem soeben erstellen Objekt auf dem Heap. Diese Verknüpfung stellt eine Referenz (= Verweis) auf das Objekt dar. Es können auch mehrere Variablen auf das gleiche Objekt zeigen.

Java verwendet einen Garbage Collector, der automatisch nicht mehr verwendete Objekte erkennt und Speicher freigibt. Dies hat den Vorteil, dass Sie als Entwickler sich nicht um die Speicherfreigabe kümmern müssen. Wenn der Heap überläuft, stürzt das Programm mit einem `OutOfMemory` Fehler ab. 

Schauen wir uns den Stack nun noch genauer an. Der Stack ist ein Speicherbereich, der für die Ausführung von Methoden und die Speicherung von lokalen Variablen verwendet wird. Jede Methode in Java wird auf einem eigenen Stackframe ausgeführt, der alle für die Ausführung der Methode erforderlichen Informationen enthält, einschließlich der Parameter und lokalen Variablen.

Wenn eine Methode aufgerufen wird, wird ein neuer Stackframe für diese Methode erstellt und auf den Stapel gelegt. Alle Variablen, die innerhalb dieser Methode deklariert werden, sowie die Methodenparameter, werden im Speicher dieses Stackframes gespeichert. Wenn die Methode abgeschlossen ist, wird ihr Stackframe entfernt und der Speicherplatz für lokale Variablen freigegeben.

Da auch der Stack eine begrenzte Größe hat, kann es zu einem `Stack Overflow` kommen, wenn zu viele Methodenaufrufe ineinander verschachtelt sind und der verfügbare Speicherplatz auf dem Stack nicht mehr ausreicht. 

Die oberste Methode auf dem Stack ist immer die aktuelle Methode, die unterste Methode, die main()-Methode, da diese als erstes aufgerufen wurde. Der Stack ist somit ein LIFO-Speicher, das bedeutet last in first out.

>**Zusammengefassung** 

Speicherressourcen werden über den Heap und den Stack verwaltet. Der Heap wird für die Speicherung von Objekten verwendet, während der Stack für die Ausführung von Methoden und die Speicherung von lokalen Variablen dient. 

Hinweis: Bei Programmabsturz sehen Sie den Stacktrace. 

>**Übung**

Gehen Sie zu einem Programm zurück, in welchem Sie die Rekursion geübt haben (z.B. Fakultät). Schauen Sie sich im Debug-Modus den Stack an und beobachten Sie, wie dieser beim rekursiven Aufruf der Methode immer weiter anwächst.

### Übungen

Machen Sie die Aufgaben aus der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus Kapitel 05.


Hinweise zu den Übungsaufgaben: 

* Bibliothek: Fügen Sie das Überschreiben der Methoden `toString()` und `equals(Object o)` erst hinzu, wenn Sie das Kapitel Vererbung durchgearbeitet haben. 



### Ablage

<!-- data-type="None" -->
|    | Klassen   | Objekte   | 
| :--------- | :--------- | :--------- | 
| Erzeugung | automatisch bei Programmstart | explizit mit `new` während der Laufzeit |
| Anzahl | genaue eine | beliebig viele |

<!-- data-type="None" -->
|    | Klassenvariable   | Instanzvariablen   | 
| :--------- | :--------- | :--------- | 
| Erzeugung | mit der Klasse | mit dem Objekt |
| Anzahl | pro Klasse | pro Objekt |
| Modifier | static | keiner |
| Verwendung | von der Klasse und Objekten | nur von den Objekten |

<!-- data-type="None" -->
|    | Klassenmethode  | Instanzmethoden   | 
| :--------- | :--------- | :--------- | 
| Erzeugung | mit der Klasse | mit der Klasse |
| Anzahl | pro Klasse | pro Klasse |
| Modifier | static | keiner |
| Verwendung | von der Klasse und Objekten | nur von den Objekten |

Hinweis: die main-Methode ist eine besondere Klassenmethode



## Exkurs: Rekursion

Eine Rekursion ist ein Vorgang, der sich selbst als Teil enthält oder mithilfe von sich selbst definierbar ist. Eine rekursive Funktion ist somit eine Funktion, die sich selbst aufruft. Rekursion kann zum Beispiel anstelle von Schleifen genutzt werden. 

>**Beispiel: Fakultät**

* Wie wird die Fakultät berechnet? Recherchieren Sie zwei verschiedene Berechnungsmöglichkeiten.
* Sind Ihre gefundenen Berechnungsmöglichkeiten rekursiv oder iterativ?

Bei der Rekursion muss aufgepasst werden, dass keine unendliche Rekursion entsteht. D.h. man braucht immer eine Abbruchbedingung, ansonsten führt dies zu einem Laufzeitfehler. Der rekursive Funktionsaufruf erfolgt nur, wenn die Abbruchbedingung nicht erfüllt ist. 

Hier finden Sie einen Mustercode für die Rekursion: 

```java
public static typ funktion(typ parameter){
  if (bedingung){
    return ergebnis; //Rekursionsabbruch
  } else {
    return wert operation funktion(neuerParameter); //Rekursionsaufruf
  }
}
```

* Rekursion führt für bestimmte Problemstellungen zu prägnanten, knappen und eleganten Algorithmen.
* Rekursionen verbrauchen meist mehr Arbeitsspeicher. Deshalb kann durch zu große Rekursionstiefe auch ein Stack Overflow entstehen.



### Fakultät

Schauen wir uns die Iteration am Beispiel der Fakultät genauer an. Evtl. haben Sie diese beiden Berechnungsmöglichkeiten bereits recherchiert.

Eine iterative Berechnungsmöglichkeit der Fakultät:

<img src="fakultaetIterativ.png" alt="Iterative Berechnung Fakultät" width="40%">

Versus eine rekursive Berechnungsmöglichkeit der Fakultät:

<img src="fakultaetRekursiv.png" alt="Rekursive Berechnung Fakultät" width="30%">

So kann man sich die rekursive Berechnung vorstellen.

![Fakultätsberechnung](fakultaet.png)


>**Aufgabe**

Vervollständigen Sie die beiden Programme mit Hilfe der obigen Definitionen, so dass jeweils die Fakultät berechnet wird:

```java
class FakultaetIterativ{
    public static void main(String args[]){
        int n = 4;
        System.out.println(n + "! = " + fakultaet(n));
    }

    public static int fakultaet(int n ){
        int fakultaet = 1;

        // Fügen Sie hier den passenden Code ein

        return fakultaet;
    }
    
}
```
@LIA.java(FakultaetIterativ)


```java
class FakultaetRekursiv{
    public static void main(String args[]){
        int n = 4;
        System.out.println(n + "! = " + fakultaet(n));
    }

    public static int fakultaet(int n ){
        if ( // Bedingung? ){
            return // was wird zurück gegeben bei Abbruchbedingungen?
        } else {
            // was wird zurück gegeben? rekursiver Aufruf 
    }
}
```
@LIA.java(FakultaetRekursiv)

### Übung

Sie können in der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus der Kategorie sonstige Übungen nun die Aufgabe Binominal und Pascal lösen. 

Betrachten Sie Ihre Lösung auch jeweils in der Debug-Perspektive und achten Sie darauf, welche Methoden auf dem Stack liegen. 


## Exkurs: Arbeiten mit Eclipse

In diesem Kapitel erhalten Sie weitere Tipps zum Arbeiten mit Eclipse:

Über die rechte Maustaste -> Source können Sie:

* Generate Getters and Setters: Getter und Setter erzeugen. Wählen Sie hierfür jeweils die Instanzariablen aus, für die Sie Getter und Setter erzeugen möchten
* Generate Constructor using Fields: Wählen Sie auch hier jeweils die Instanzariablen aus, die Ihr Konstruktor beinhalten soll
* Generate toString(): Erzeugt Ihnen eine toString()-Methode, wählen Sie hier die Instanzariablen aus, die mit ausgegebenw erden sollen



### Kommentare

Hier erhalten Sie ein Überblick, über verschiedene Kommentarmöglichkeiten:

Einzeilige Kommentare 

* Werden zeilenweise verwendet, sie beginnen mit einem Doppelschrägstrich // und enden mit dem Zeilenende
* Für kurze Erklärungen

Blockkommentare 

* Werden für Erklärungen benutzt, die sich über mehrere Zeilen erstrecken
* Sie beginnen mit einem Schrägstrich und Multiplikations-Zeichen /* und enden mit Multiplikations-Zeichen und Schrägstrich */

Dokumentationskommentare 

* Werden zu Dokumentationszwecken eingesetzt
* Mit javadoc kann anschließend automatisch eine umfangreiche HTML-Dokumentation generiert werden.
* Dokumentationskommentare beginnen mit einem Schrägstrich und zwei Multiplikations-Zeichen /** und enden mit Multiplikations-Zeichen und Schrägstrich */
* Stehen immer vor dem Element, welches sie beschreiben sollen

>**Methodenkommntare**
Methodenkommentare beschreiben, was die Methode macht

* Beginnt mit /** und endet mit */
* Schlüsselwörter (Tags) wie 
    * @param: Beschreibung der Parameter der Methode
    * @return: Rückgabewert
    * Und viele mehr

Weitere Schlüsselwörter: author, version, since, see …

Beispiel: 

```java
/**
* Diese Methode berechnet das Maximum für zwei Zahlen.
*
* @param zahl1 Die erste Zahl.
* @param zahl2 Die zweite Zahl.
* @return Die größere der beiden Zahlen.
*/

public static int max(int zahl1, int zahl2) {
    return zahl1 > zahl2 ? zahl1 : zahl2;
    }
```

>**Tipps für Eclipse**

* Source -> Toggle Comment bzw. Ctrl+7

* Source -> Add block Comment 
* Source -> Remove block Comment

* Source -> Generate Element Comment
* Eingabe von /** und return -> generiert Kommentar


### Refactoring

Refactoring bedeutet Strukturverbesserung von Quelltexten mit dem Ziel, Quelltext lesbarer, leichter wiederverwendbar und erwei­terbar zu gestalten. Dazu gehört zum Beispiel kurze, übersichtliche Methoden bauen und Methoden mit vielen Parameter vermeiden, mit dem Ziel
Clean Code zu erzeugen.

>**Refactoring in Eclipse**

Zeilen markieren, die in neue Methode gepackt werden sollen, rechte Maustate Refactor -> Extract Method. Im Dialogfenster: Name für Methode angeben und Modifikatoren wählen. Notwendige Paramter werden von Eclipse erkannt. Danach OK klicken.

Probieren Sie dies an einem eigenen Beispiel aus.




## Vererbung

Schauen Sie sich folgende beiden Codebeispiele an und überlegen Sie sich, was Ihnen hierbei auffällt. 

```java
public class Hund {

	private String name;
	private int alter;
	
	public void schlafen() {
		System.out.println("Ich schlafe...");
	}
	
	public void bellen() {
		System.out.println("wau, wau");
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public int getAlter() {
		return alter;
	}

	public void setAlter(int alter) {
		this.alter = alter;
	}
}
```

```java
public class Katze {

	private String name;
	private int alter;
	
	public void schlafen() {
		System.out.println("Ich schlafe...");
	}
	
	public void miauen() {
		System.out.println("miau, miau");
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public int getAlter() {
		return alter;
	}

	public void setAlter(int alter) {
		this.alter = alter;
	}
}
```

Der Großteil des Codes ist komplett gleich. Nur eine Methode unterscheidet sich vom Hund zur Katze. 

Sie haben bisher gelernt, dass Klassen Objekte beschreiben, die sich gleich verhalten und gleiche Eigenschaften besitzen. Manchmal gibt es jedoch Objekte, die nicht gleich aber doch sehr ähnlich wie andere Objekt sind, wie z.B. ein Hund und eine Katze viele gemeinsame Eigenschaften und Verhaltensweisen haben (sie haben einen Namen, ein Alter, können schlafen etc.), aber doch unterschiedlich sind in anderen Dingen (sie machen andere Laute). 
Weiterhin hat jede Klasse die gleichen Objektvariablen und dazugehörige Setter und Getter, plus evtl. Konstruktoren etc. Wenn wir Katze und Hund als eigenständige Klassen implementieren, haben wir viel doppelten Code. Dies ist arbeitsintensiv und fehleranfällig. 

Die Lösung heißt Vererbung, eine Besonderheit, die es nur in der objektorientierten Programmierung gibt. Damit beschäftigen wir uns in diesem Kapitel.


Vererbung erlaubt, 
* gemeinsame Teile einmal in einer Klasse zusammenzufassen
* spezielle Teile in eigenen Klassen zu beschreiben
* die gemeinsamen Teile in den speziellen Klassen zu erben


Eine Klasse kann also Eigenschaften und Methoden von einer anderen Klasse erben, indem sie von dieser Klasse ableitet. Die Erbschaftsbeziehung wird definiert über Schlüsselwort `extends` (z.B. class B extends A).

Für unser Beispiel bedeutet dies: Alle gemeinsamen Eigenschaften werden in eine Oberklassen (auch Superklasse, Basisklasse oder Elternklasse genannt) gepackt, hier z.B. eine Klasse Haustier.

```java
public class Haustier {

	private String name;
	private int alter;
	
	public void schlafen() {
		System.out.println("Ich schlafe...");
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public int getAlter() {
		return alter;
	}

	public void setAlter(int alter) {
		this.alter = alter;
	}
}
```

Spezielles Verhalten steht in den Unterklassen (auch Subklassen oder Kindklassen genannt). Über das Schlüsselwort `extends` wird angezeigt, dass der Klasse Hund Katze  die Eigenschaften und Methoden der Klasse Haustiere zur Verfügung stehen.


```java
public class Hund extends Haustier {
	public void bellen() {
		System.out.println("wau, wau");
	}
}
```

```java
public class Katze extends Haustier {
	public void miauen() {
		System.out.println("miau, miau");
	}
}
```

Fehlt die Angabe einer Oberklasse wie bisher, so ist die Oberklasse die Klasse `Object`, quasi die Mutter aller Klassen.

>**Einfachvererbung**

Java ist eine Sprache mit Einfachvererbung, das bedeutet, dass Klassen immer nur eine Oberklasse haben:

- Alle Klassen sind direkt oder indirekt Unterklassen der Klasse `Object`
- Wenn keine explizite Oberklasse angegeben wird, wird implizit `Object` angenommen
- `Object` selbst hat (als einzige Klasse) keine Oberklasse

Eine Unterklasse darf man erneut erweitern, so entstehen Hierarchien von Klassen, welche einen Baum bilden, dessen Wurzel die Klasse `Object` ist. 

![](Vererbung-3.png.jpg)


>**Mutterklasse `Object`**

* `Object` ist in Java die Elternklasse jeder weiteren Klasse und somit die allgemeinste Klasse
* Alle anderen Klassen teilen die Eigenschaften der Klasse `Object`
* Beispiel: Die Methode `public boolean equals(Object obj)` vergleicht die Speicheradressen (nicht die semantische Gleichheit!). Die Klassen Integer, String liefern für semantischen Vergleich jeweils eigenen Code, analog müssen eigene Klassen eigenen Code liefern, wenn der Vergleich der Speicheradressen nicht das gewünschte Ergebnis ergibt

Recherchieren Sie in der Java-Dokumentation, welche Methoden die Klasse `Object` liefert. 


Ein häufiges Beispiel ist das Überschreiben der toString()-Methode. Diese sieht standardmäßig folgendermaßen aus:

```java
    public String toString() {
        return getClass().getName() + "@" + Integer.toHexString(hashCode());
    }
```

Sie liefert also eine String Repräsentation des Objekts (genauer den qualifizierten Klassennamen (also den Paketnamen plus den Klassennamen) gefolgt von einem `@` und dem Hashcode). Dies ist jedoch meist nicht, was wir ausgeben wollen. Somit müssen wir die toString()-Methode mit etwas Sinnvollem überschreiben. Was eine sinnvolle Ausgabe ist, hängt von der entsprechenden Klasse ab. 

```java
@Override
public String toString(){
    return "Meine Variable: " + meineVariable;
}
```

>**Übung**

Sie können in der Aufgabe Typen aus der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus Kapitel 06 sich das Codegerüst herunterladen und einen Überblick verschaffen. Legen Sie einen Elefant und eine Ente an und leiten Sie vom richtigen Tier ab. Überschreiben Sie noch keine Methoden. Legen Sie in der Anwendungsklasse einen Elefant und eine Ente an.


### Vererbung von Methoden und Variablen

Schauen wir uns nun an, was mit Instanzmethoden und Variablen bei der Vererbung passiert. 

>**Was passiert mit den Instanzmethoden bei der Vererbung?**

Für `public` und `protected` Methoden gilt:

- Werden geerbt: Verwendbar, als wären sie direkt in der Unterklassen definiert
- Können überschrieben werden: eine Unterklasse kann geerbte Methoden durch Methoden mit gleicher Signatur redefinieren mit der Annotation `@Override` –  - auf die ursprüngliche Methode kann mit dem `super`-Qualifier zugegriffen werden 

Für `private` Methoden gilt:

- Sind in Unterklassen nicht sichtbar
- Können nicht überschrieben werden
- Gleiche Methode in Unterklasse sind möglich (gleicher Rückgabetyp, gleicher Name, gleiche Parameter)

Wenn Überschreiben verboten werden soll: Schlüsselwort `final` benutzen!

 `final`  für Methoden:

- Einzelne Methoden können gezielt mit final als nicht überschreibbar markiert werden
- Beispiel: public final void methode()

 `final`  für Klassen:

- Überschreiben der ganze Klasse verboten
- final markierte Klassen lassen sich nicht ableiten

>**Was passiert mit den Variablen bei der Vererbung?**

- Vererbt werden Variablen, die `public` oder `protected` sind (oder package-private falls Unterklasse und Oberklasse im gleichen Package liegen). Die Verwendung funktioniert dann genau wie bei Variablen, die direkt in der Unterklasse definiert sind.
- Auf `private` Variablen kann nicht zugegriffen werden – es sei denn, es gibt geerbte `public` und `protected` Methoden (z.B. Getter und Setter)
- Eine Unterklassen kann durch neue Variablen erweitert werden, die es in der Oberklasse nicht gibt


Zurück zu unserem Beispiel:

```java
public class AnwendungHaustiere {
	public static void main(String[] args) {
		Katze katze = new Katze();
		katze.setName("Maunzi");
		katze.miauen();
		katze.setAlter(7);
		System.out.println(katze.getName() + " ist " + katze.getAlter() + " Jahre alt.");
		katze.schlafen();
	}
}
```

Welche Ausgabe wird erzeugt? 

Was kann folgender Hund? Wir ändern die Klasse Hund folgendermaßen ab:

```java
public class Hund extends Haustier {
	public void bellen() {
		System.out.println("wau, wau");
    }

    @Override
	public void schlafen() {
		super.schlafen();
		System.out.println("Ich bin ein Langschläfer.");
	}
}
```

Anhand der @Override Annotation erkennt der Compiler, dass die Methode schlafen überschrieben werden soll. Danach erfolgt der Methodenaufruf der Oberklasse mit `super.methode()`, in dem Fall mit super.schlafen(). 

Hinweis: Methodenaufrufe über `super` können an einer beliebigen Stelle in den Methoden der Kindklasse auftauchen. Aufruf des Elternkonstruktors `super()` muss immer als erstes im Kindkonstruktor stehen, siehe nächstes Teilkapitel.

Welche Ausgabe wird erzeugt, wenn Sie ein Objekt des Typs Hund erstellen und auf diesem die Methoden schalfen aufrufen? Überprüfen Sie Ihre Vermutung mit Hilfe von Eclipse.

>**Übung**

Sie können in der Aufgabe Typen aus der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus Kapitel 06 die Methoden geraeuschErzeugen() überschreiben.


### Vererbung Konstruktoren

Java stellt immer einen Standardkonstruktor (ohne Parameter) bereit. Wird ein eigener Konstruktor definiert, steht der Standardkonstruktor nicht mehr zur Verfügung. 
Folgende Hinweise zu, was nicht vererbt wird:

- Hat die Oberklasse hat einen eigenen Konstruktor definiert, muss die Unterklasse ebenfalls einen eigenen definieren
- Der Konstruktor der Oberklasse kann (im Konstruktor der Unterklasse) durch super(Parameterliste) aufgerufen werden 
- Aufruf des gewünschten Konstruktors der Elternklasse muss immer am Anfang des Codings im Konstruktor stehen

>**Konstruktorkette reparieren**
Nehmen wir an, in der Klasse Haustier, sei folgender Konstruktor definiert:

```java
public Haustier(String name, int alter){
    this.name = name;
    this.alter = alter;
}
```

In den Unterklassen Katze und Hund steht nicht mehr der Standardkonstruktor zur Verfügung. Es gibt nun verschiedene Möglichkeiten, die Konstrukorkette zu reparieren.


1) Konstruktor der Oberklasse explizit aufrufen in Standardkonstruktor der Unterklasse.

```java
public Katze(){
    super(null,0);
}
```

Damit hätten wir unserer Katze standardmäßig immer den Namen null und das Alter 0 gegeben.

2) Der Oberklasse explizit wieder Standardkonstruktor hinzufügen. Der Compiler ist zufrieden, aber
Konstruktoren werden nicht vererbt!

```java
public Haustier(){
}
```

3) Der Unterklasse einen neuen Konstruktor hinzufügen, der die gleichen (oder mehr) Parameter hat als der Konstruktor der Oberklasse: 

```java
public Katze(){
    super(name,alter);
    this.kuschelfaktor = kuschelfaktor; //wenn wir annehmen, die Katze hätte noch weitere Instanzvariablen
    }
```

Tipp: In Eclipse hilft Ihnen die rechte Maustaste, um Konstruktoren, die kaputt gegangen sind, hinzuzufügen. 

Merke:
Der erste Aufruf innerhalb eines Konstruktors ist immer der Aufruf eines anderen Konstruktors. Einzige Ausnahme: Der Konstruktor der Mutter aller Klassen Object

>**Quiz**

Welche Konstruktoren sind erlaubt und welche nicht?

```
Person(Person person) {}
```

[(x)] erlaubt
[( )] falsch

```
Person Person() {}
```

[( )] erlaubt
[(x)] falsch

```
private final Person() {}
```

[( )] erlaubt
[(x)] falsch

```
void Person() {}
```

[( )] erlaubt
[(x)] falsch

```
Person() {
    super();
}
```

[(x)] erlaubt
[( )] falsch


>**Übung**
Zurück zu unserer Aufgabe Typen aus der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus Kapitel 06.

* Existieren in den Klassen Konstruktoren?
* Welcher Konstruktor wird durch `Ente ente = new Ente()` aufgerufen?
* Probieren Sie aus: Fügen Sie Vögeln eine Variable Namen hinzu. Erstellen Sie dann einen Konstruktor, der dem Sie den Namen als Startwert mitgeben.
* Was passiert mit der Klasse Ente? Wie können Sie das Problem lösen?



### Typumwandlung
Wir haben Typumwandlungen schon beim Casting von primitiven Datentypen kennengelernt. Unter `Casting` versteht man das Umwandeln von einem Typ in einen anderen Typ.

Zur Erinnerung: Hier wurden verschiedene primitive Datentypen durch Typ­ Umwandlung ineinander konvertiert. Wir haben zwischen zwischen Widening (Erweitern) und Narrowing (Eingrenzen) unterschieden.
Im Fall von primitiven Datentypen bedeutet Widening, dass eine Variable von einem Typ mit einem kleinen Wertebereich in eine Variable von einem Typ mit einem größeren Wertebereich umgewandelt wird
Narrowing bedeutet genau das Gegenteil, der Wertebereich wird also kleiner. Widening ist in der Regel kein Problem, Narrowing kann aber gefährlich sein, da einzelne Werte hierbei verloren gehen können!

Ein ähnliches Vorgehen ist nun auch bei der Typumwandlung von Objekten möglich, denn nicht nur primitive Datentypen können durch Casting umgewandelt werden, sondern auch Objekte. 

* Wenn ein Typ in einen anderen Typ umgewandelt werden kann, heißt dies `kompatibel`. 
* `Downcasting`: Umwandlung eines in der Hierarchie höher liegenden Typs in einen tieferen
* `Upcasting`: Umwandlung eines in der Hierarchie tiefer liegenden Typs in einen höher liegenden

Beim Casting (insbesondere beim Downcasting) muss überprüft werden, ob die Umwandlung funktionieren kann. Dies geschicht mit den instanceof-Operator. Dieser gibt true oder false zurück. 

Merke: Ein Objekt vom Typ der Unterklasse ist auch vom Typ der Oberklasse.
    
Verwendung:

```
Referenzvariable instanceof Klassenname
```

Folgende Grafik verdeutlich dies:

<p align="center">
<img src="Tier.png" alt="HaustierKlassendiagramm" width="50%">
</p>


Beispiel: 

```
Tier katze = new Katze();
```

`katze` ist eine Referenzvariable vom Typ `Tier`, die auf eine konkrete Instanz `Katze` zeigt. 
`katze` kann schlafen, aber nicht miauen, da sie ein Tier ist.

```
Katze gleicheKatze = (Katze) katze;
```

`gleicheKatze` kann miauen, da die Referenzvariable vom Typ Katze ist.

Gebrauch des `instanceof`-Operators in diesem Szenario:

```
if (katze instanceof Katze){
    Tier gleicheKatze = (Katze) katze;
}
```

Merke: Die konkrete Objektinstanz ändert sich hierdurch nicht, d.h. es wird kein neues Objekt auf dem Heap gelegt. 

>**Übung**

Erzeugen Sie den Code zu obigem UML-Diagramm. Probieren Sie folgende Szenarien aus:

* Erzeugen Sie ein Tier vom Typ Hund (Tier tier = new Hund(...)). Was kann dieses Tier?
* Wandeln Sie mit Casting das tier in einen Hund um. Was kann das Tier jetzt?
* Implementieren Sie Schlafmethoden, sowohl im Tier als auch im Hund. Überprüfen Sie, welche Methode wird jeweils aufgerufen?


Was passiert bei folgenden Aufrufen?

* Katze katze = new Tier();
* Katze katze = (Katze) new Tier();

Überlegen Sie sich, warum diese Aufrufe nicht möglich sind.

Hinweis:
Nicht jedes Tier ist eine Katze und nicht jedes Tier kann einfach in eine Katze umgewandelt werden. 


>**Polymorphismus**

Eine Variable vom Typ einer Oberklasse kann ein beliebiges Objekt seiner Unterklasse aufnehmen. Alle Methoden, die in der Oberklasse definiert sind, können aufgerufen werden: Da das Unterklassenobjekt alle Methoden der Oberklasse erbt, erweitert oder implementiert, kann man sich darauf verlassen, dass alle Methoden der Oberklasse verfügbar sind. Ausgeführt wird (natürlich) der Code des aktuellen Objekts. Methoden, die nur in der Unterklasse vorliegen, können nicht aufgerufen werden (sie sind da, sind aber nicht sichtbar).

Das bedeutet nun: Objekte können spezialisiertes Verhalten hinzufügen. Man muss dabei nicht über Verhalten-Details Bescheid wissen, sondern nur wissen, dass ein Verhalten angeboten wird.


### UML-Klassendiagramme 
Die UML (= Unified Modeling Language) ist eine graphische Modellierungssprache mit welcher Objekte, Zustände und Prozesse eines Systems dargetsellt werden können. Hierbei gibt es verschiedene Diagrammtypen, je nachdem wie das Softwaresystem betrachtet werden soll. Wir nutzen in diesem Kurs das Klassendiagramm , welches eine Übersicht über die verschiedenen Klassen gibt und wie diese in Beziehung zueinander stehen. 

Im Klassendiagramm werden die Elemente, d.h. die Attribute und Methoden dargestellt, wie im folgenden Beispiel:

<p align="center">
<img src="Haustier.png" alt="HaustierKlassendiagramm" width="50%">
</p>

In dem Beispiel ist die Vererbung von Haustier zu Hund und Katze eingezeichnet (mit einem nicht-ausgefüllten Pfeil)

Es gibt neben der Vererbung aber auch eine weitere Verbindung zwischen Klassen, die Delegation.

>**Delegation**

Im Gegensatz zur Vererbung, bei der eine Klasse die Eigenschaften einer anderen Klasse übernimmt, wird bei der Delegation eine Aufgabe an eine andere Klasse weitergegeben. Dies bedeutet, dass diese Klasse ein Objekt einer anderen Klasse als Instanzvariable verwendet. Die Delegation kann als eine hat-ein-Beziehung zwischen Objekten betrachtet werden, bei der ein Objekt bestimmte Methodenaufrufe an ein anderes Objekt weiterleitet. Die Vererbung dagegen kann als eine ist-ein-Beziehung betrachtet werden. 

Eine Katze ist ein Haustier: Vererbung
Ein Fotoapparat hat ein Objektiv: Delegation

Ein Mitarbeiter ist ein Nutzer: Vererbung
Ein Nutzer hat eine Adresse: Delegation


Betrachten Sie nun folgendes Beispiel und versuchen Sie die Delegation nachzuvollziehen:

```java
class Professor {
    public void lehren() {
        System.out.println("Professor hält eine Vorlesung.");
    }

    public void benoten() {
        System.out.println("Professor benotet Hausaufgabe.");
    }
}
```

```java
class Student {
    private Professor professor;

    public Student(Professor professor) {
        this.professor = professor;
    }

    public void vorlesungBesuchen() {
        professor.lehren();
    }

    public void hausaufgabeEinreichen() {
        System.out.println("Student reicht Hausaufgabe ein.");
    }

    public void noteErhalten() {
        professor.benoten();
    }
}
```

```java
public class Delegation {
    public static void main(String[] args) {
        Professor professor = new Professor();
        Student student = new Student(professor);

        student.vorlesungBesuchen();
        student.hausaufgabeEinreichen();
        student.noteErhalten();
    }
}
```

Die Professor-Klasse ist für das Unterrichten und Bewerten von Arbeiten zuständig, während die Student-Klasse Vorlesungen besucht, Aufgaben einreicht und Rückmeldung vom Professor erhält. Die Student-Klasse hat eine Referenz auf ein Professor-Objekt, und wenn die Methoden der Student-Klasse aufgerufen werden, wird diese Funktionalität an die entsprechenden Methoden der Professor-Klasse delegiert.


>**Assoziationen**

Klassen stehen in Beziehungen zueinander. Eine Assoziation wird mit einer durchgezogenen Linie repräsentiert. 

Es werden hier zwei besondere Fälle unterschieden:

* Aggregation: Die Teile können existieren, wenn auch das Ganze (noch) nicht existiert.
Die Aggregation wird mit einer durchgezogenen Linie mit einer nicht ausgefüllten Raute an einem Ende dargestellt. Die Raute befindet sich immer auf der Seite des "Ganzen". Die Abbildung zeigt: Jedes Regal besitzt 1 bis beliebig viele Bücher. Jedes Buch befindet sich in 0 bis 1 Regalen.

<img src="aggregation.png" alt="aggregation" width="40%">

* Komposition: Die Teile können nicht ohne das Ganze existieren.
Die Komposition wird mit einer durchgezogenen Linie mit einer ausgefüllten Raute an einem Ende dargestellt
Die Multiplizität auf der Seite des Ganzen muss zwangsläufig 1 sein! Die Abbildung zeigt: Jedes Buch besitzt 1 bis beliebig viele Seiten. Und jede Seite existiert in genau einem Buch. 

<img src="komposition.png" alt="komposition" width="40%">

Weitere Beziehungen in UML-Diagrammen sind z.B. Interfaces mit einer gestrichelten Linie gekennzeichnet (siehe Kapitel Interfaces).

Mit folgendem Programm können einfach Klassendiagramme erstellt werden:
[yEd](https://www.yworks.com/yed-live/)
Gehen Sie hierzu auf neues Diagramm erstellen und wählen Sie rechts UML aus. Dann stehen Ihnen (abstrakte) Klassen und Interfaces, jeweils mit verschiedenen Beziehungen zur Verfügung.


### Übungen

Machen Sie die Aufgaben aus der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus Kapitel 06.


## Abstrakte Klassen, Interfaces und geschachtelte Klassen

In diesem Kapitel beschäftigen wir uns mit abstrakten Klassen, Interfaces und geschachtelte Klassen, die die Flexibilität und Modularität von Java-Programmen stark verbessern können. 
Diese Konzepte bieten Möglichkeiten, wie Klassen miteinander interagieren und wie Verhaltensweisen und Eigenschaften von Objekten definiert werden können.

Abstrakte Klassen ermöglichen es uns, Klassen zu definieren, die nicht direkt instanziiert werden können, sondern als Vorlage für konkrete Unterklassen dienen. Durch die Verwendung von abstrakten Methoden können wir sicherstellen, dass bestimmte Verhaltensweisen in Unterklassen implementiert werden müssen, während bereits vorhandene Methoden in der abstrakten Klasse wiederverwendet werden können.

Interfaces definieren eine Schnittstelle, die von Klassen implementiert werden kann. Sie bieten eine Möglichkeit, Verträge zwischen verschiedenen Teilen des Codes herzustellen, indem sie eine Sammlung von Methoden ohne Implementierungen bereitstellen. Dadurch wird die Interoperabilität zwischen verschiedenen Klassen  verbessert, und es ermöglicht die Umsetzung von Polymorphismus.

Geschachtelte Klassen sind Klassen, die innerhalb einer anderen Klasse definiert sind. Sie bieten eine Möglichkeit, die Struktur unseres Codes zu organisieren und den Zugriff auf Klassen zu kontrollieren. Geschachtelte Klassen können statisch oder nicht-statisch sein und haben Zugriff auf alle Mitglieder der äußeren Klasse, einschließlich privater Mitglieder.


### Abstrakte Klassen
Bisher haben wir gemeinsames Verhalten in einer gemeinsamen Oberklasse festgelegt. Manchmal ist es aber aus Anwendersicht nicht sinnvoll, von diesen Klassen ein Objekt zu erzeugen. 

Betrachten Sie hierzu folgendes Beispiel. Dreieck und Kreis sind beides geometrische Figuren, von denen man den Umfang berechnen kann. Die Berechnung des Umfangs erfolgt jedoch auf unterschiedliche Art und Weise, so dass es nicht sinnvoll erscheint, diese Methode in der gemeinsamen Oberklasse `Figur` bereits zu implementieren. Man bekommt somit zwangsläufig eine Dopplung der Methode. Ebenso erscheint es unter Umständen wenig sinnvoll, ein Objekt vom Typ `Figur` zu erzeugen, sondern nur konkrete Figure, wie z.B. Dreiecke oder Kreise.

Beispiel:

<p align="center">
<img src="Figur.png" alt="UMLAbstrakteKlasse" width="60%">
</p>

Diese Problem kann mit Hilfe von abstrakten Klassen gelöst werden. Dies bedeutet: Die Klasse `Figur` wird als `abstract` markiert. Dann können von dieser Klasse keine Objekte erzeugt werden. Weiterhin können Methoden auch unimplementiert vererbt werden. Die konkreten Unterklassen müssen für diese Methoden dann eine Implementation bereitstellen. 

Abstrakte Klassen werden im UML-Klassendiagramm kursiv geschrieben oder als `abstract` markiert

<p align="center">
<img src="FigurAbstrakt.png" alt="UMLAbstrakteKlasse2" width="60%">
</p>

Im Code werden abstrakte Klassen mit dem Schlüsselwort `abstract` gekennzeichnet. 

Methoden abstrakter Klassen können zusätzlich `abstract` markiert werden. Abstrakte Methoden enthalten keine Implementierung. Dies zwingt eine nicht abstrakte Unterklasse eine Implementierung zu liefern. Wenn eine Klasse nicht alle abstrakten Methoden der abstrakten Oberklasse implementiert, muss sie selbst wieder abstrakt sein.


```
// abstrakte Klasse
public abstract class Figur{

    // abstrakte Methode ohne Implementierung
    public abstract double berechneUmfang(){

    }
}
```


>**Quiz** 

Führen Sie nun folgendes Quiz durch und testen Sie Ihr Wissen: 

**Frage 1**

Gibt es abstrakte Klassen ohne abstrakte Methoden?

[(x)] Ja
[( )] Nein

**Frage 2**

Gibt es konkrete Klassen mit abstrakten Methoden?

[( )] Ja
[(x)] Nein

**Frage 3**

Müssen Unterklassen die abstrakten Methoden der Oberklasse implementieren?

[( )] Ja
[(x)] Nein

**Frage 4**

Stehen abstrakte Klassen immer oben in der Hierarchie?

[( )] Ja
[(x)] Nein

**Frage 5**

Können abstrakte Klassen nur instanziiert werden, wenn sie einen Konstruktor mit Parametern haben?

[( )] Ja
[(x)] Nein


>**Aufgabe** 
Lesen Sie die Aufgabe privater Zoo aus der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus Kapitel 07. Erstellen Sie das UML-Klassendiagramm und implementieren Sie die Klassen.


### Interfaces

Ein Interface ist eine Sammlung von abstrakten Methoden, die eine Klasse implementieren kann. Es enthält lediglich Methodensignaturen, aber keine konkreten Implementierungen. 
Klassen können nun ein oder mehrere Interfaces implementieren, und somit für die darin definierten Methoden eine konkrete Implementierung bereitstellen. 
Interfaces werden verwendet, um eine Vertragsvereinbarung zwischen verschiedenen Teilen des Codes / zwischen verschiedenen Klassen herzustellen. 
Sie ermöglichen es, dass verschiedene Klassen unabhängig voneinander die gleiche Funktionalität bereitstellen, indem sie die im Interface definierten Methoden implementieren. 
Interfaces werden häufig verwendet, um Polymorphismus zu ermöglichen und die Flexibilität und Erweiterbarkeit des Codes zu verbessern.

Eingeleitet wird ein Interface durch das Schlüsselwort `interface`. Beispiel:

```
// Interface
public interface Berechenbar{
    double berechneUmfang();
    double berechneFlaeche();
}
```

Alle Klassen, die das Interface `Berechenbar` implementieren, müssen nun eine konkrete Implementierung für die beiden Methoden berechneUmfang() und berechneFlaeche() bereitstellen.

Die Klasse `Kreis` könnte dann beispielsweise so aussehen:

```
public class Kreis extends Figur implements FlächeBerechnbar {
    private double radius;

    public Kreis(double radius) {
        this.radius = radius;
    }

    @Override
    public double berechneFläche() {
        return Math.PI * Math.pow(radius, 2);
    }
}
```


Hinweise:

* Klassen erben nicht von Interfaces sondern implementieren diese Interfaces.
* Interfaces können nicht instanziiert werden.
* Eine Klasse kann mehrere Interfaces implementieren.

Wann nimmt man nun Verwerbung und wann ein Interface? Leitfragen können sein: 

* Vererbung: Unterklasse Student ist eine Person.
* Interfaces: Implementierende Klasse Student hat eine Brille.

In der Regel werden Interfaces verwendet

* Für Objekte mit ähnlichen Eigenschaften (die im gleichen Methodennamen zum Ausdruck kommt) – aber nicht in einer (sinnvollen) gemeinsamen Oberklasse
* Zur Definition eines bestimmten Aspekts einer Anwendung, der von einer Klasse erfüllt ist

Es gilt wieder Polymorphismus:

* Variablen von einem Interface-Typ können alle Objekte enthalten, deren Klassen (oder Oberklassen) dieses Interface implementieren.
* Es können dann wieder nur die Methoden aufgerufen werden, die das Interface definiert.

Ein Interface kann als „Vertrag“ verstanden werden:

* Das Interface gibt die Bedingungen vor, die ein Programmierer einhalten muss, wenn er das Interface implementiert.
* Interfaces können als Vorgaben für andere Programmierer verwendet werden.

Interfaces trennen also die Schnittstelle von der Implementierung. Für ein Interface kann es viele implementierende Klassen geben. 
Wenn zwei verschiedene Interfaces die gleiche Methode haben, muss die Klasse, die beide Interfaces implementiert, nur eine Implementierung liefern.

Auch Schnittstellen können Hierarchien bilden. Das abzuleitende Interface (Subinterface) kann dann eigene Methoden hinzufügen. Die Klasse, die dieses Interface implementiert, muss dann auch die von den Superinterfaces (Oberinterfaces) geerbten Methoden implementieren.

```
public interface KannManEssen(){
    void essen();
}

// Abzuleitendes Interface (Subinterface) kann eigene Methoden hinzufügen
public interface IstLecker extends KannManEssen{
    void geniessen();
}

// Klasse muss alle Methoden implementieren, auch die von den Superinterfaces geerbten Methoden
public class Pizza implements IstLecker{
    @Override
    public void essen(){
    }

    @Override
    public void geniessen(){
    }
}

```

Auch Datenfelder in Interfaces möglich. Diese sind automatisch immer `public static final`. Konstanten können auch in eigenen Klassen stehen, sogenannte Konstantenklassen (besser als in Interfaces)


>**Quiz** 

Führen Sie nun folgendes Quiz durch und testen Sie Ihr Wissen: 

**Frage 1**

Kann ein Interface instanziiert werden?

[( )] Ja
[(x)] Nein


**Frage 2**

Besitzt ein Interface Konstruktoren?


[( )] Ja
[(x)] Nein

**Frage 3**

Kann eine abstrakte Klasse instanziiert werden?

[( )] Ja
[(x)] Nein

**Frage 4**

Besitzt eine abstrakte Klasse Konstruktoren?

[(x)] Ja
[( )] Nein

>**Aufgabe** 
Fügen Sie Ihrem privaten Zoo aus der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus Kapitel 07 nun ein eigenes Interface hinzu.


### Geschachtelte Klassen
Die bisher besprochenen Klassen befinden sich direkt innerhalb von Paketen. Wir nennen Sie auch Top-Level-Klassen. Eine Klasse darf sich aber auch innerhalb einer anderer Klasse befinden. Hier unterscheiden wir vier verschiedene Typen: 

1. Statischer geschachtelter Typ:

```
class Out { static class In{} }
```

2. Innerer Typ (nichtstatischer geschachtelter Typ):
```
class Out { class In{} }
```

3. Lokaler (innerer) Typ:

```
class Out { methode(){ class In{} }}
```

4. Anonyme innere Klasse
```
class Out {methode() {
            Runnable r = new Runnable(){public void run(){}; }}

```

Nichtstatische geschachtelte Typen heißen `innere Typen`. Hierzu zählen die Typen 2.-4.

Innere Typen haben immer eine Referenz auf ihren äußeren Typen. Eine geschachtelte Klasse heißt auch Mitgliedsklasse. 
Die Laufzeitumgebung kennt nur Top-Level-Typen. Auch geschachtelte Typen werden letztendlich zu ganz „normalen“ Klassendateien.
Klassen, Interfaces und Aufzählungen können verschachtelt sein. Man spricht auch allgemeiner von „geschachtelten Typen“.

Wir schauen nun die oben aufgezählten vier Typen genauer an:

>**1. Statischer geschachtelter Typ**

Ein Synonym für den statischen, geschachtelten Typ ist auch „statische Mitgliedsklasse“ (oder statische Memberklasse). Warum brauchen wir diesen?
Die statische Mitgliedsklasse gehört inhaltlich zur umschließenden Klasse und wird eigentlich nur von ihr verwendet.
Wir nutzen Sie um eine Eigenschaft darzustellen, welche für die umschließende Klasse zu komplex wäre, um hierfür einen prototypischen Datentyp zu verwenden, aber auch zu speziell, um eine Top-Level-Klasse zu begründen. Beispiel: GUI-Programmierung (siehe Swing in PRO2)

Die Funktionalität statischer Mitgliedsklassen entspricht den Top-Level-Klassen. Sie bilden „eine Art kleines Unterpaket“ mit eigenem Namensraum.
Es sind keine Objekte der äußeren Klasse nötig. Manche Autoren zählen die statischen Mitgliedsklassen zu den Top-Level-Klassen.

Die statische geschachtelte Klasse liegt analog zu Top-Level-Klassen im gleichen Paket. Der Zugriff erfolgt über `AeussererTyp.GeschachtelterTyp`.
Top-Level-Klassen können public oder paketsichtbar sein.
Geschachtelte Klassen dürfen zusätzlich protected oder private sein. Die Semantik ist analog zu entsprechenden statischen Variablen.
Der Compiler generiert aus geschachtelten Typen normale Klassendateien nach dem Muster `AeussererTyp$GeschachtelterTyp.class`.

Beispiel:

```java
public class Bank{
// Variablen der Bank
// Konstruktor der Bank

    // statische Memberklasse
    public static class Tresor{
        // Zugriff auf private Variablen der Bank nicht möglich
        void oeffnen();
    }
}
```

Verwendung:

```java
public class BankAnwendung{

    public static void main(String[] args){
        // Da die statische Memberklasse Tresor public ist, 
        // kann außerhalb von Bank eine neue Instanz von Tresor erzeugt werden        
        Bank.Tresor tresor = new Bank.Tresor();
        tresor.oeffnen;
    }
}
```

Sie können nun den ersten Teil der Übung Würfel aus der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus Kapitel 07 machen. 

>**2. Nichtstatischer geschachtelter Typ**

Ein nichtstatischer geschachtelter Typ (Synonym nichtstatische Memberklasse) ist ein innerer Typ, der mit einer Objekteigenschaft vergleichbar ist.
Eine Instanz der inneren Klasse hat Zugriff auf alle Eigenschaften der äußeren Klasse (auch auf private Attribute).
Innere Klassen dürfen selbst keine statischen Eigenschaften deklarieren.
Um eine Instanz einer inneren Klasse zu erzeugen, muss schon eine Instanz der äußeren Klasse existieren.
Statische geschachtelten Typen dagegen existieren auch ohne Instanz der äußeren Klasse. 

Für die Objekterzeugung wird also vorausgesetzt, dass es bereits eine Instanz der äußeren Klasse gibt: 

`referenz.new InnereKlasse(…)`, wobei referenz eine Referenz vom Typ der äußeren Klasse darstellt.

Beispiel:

```java
public class Bank{
// Variablen der Bank
// Konstruktor der Bank

    // statische Memberklasse
    class Tresor{
        // Zugriff auf private Variablen der Bank möglich
        private double vermoegen;
        public Tresor (double vermoegen){
            this.vermoegen = vermoegen;
        }
    }
}
```

Verwendung:

```java
public class BankAnwendung{

    public static void main(String[] args){
        // Zuerst Instanz der äußeren Klasse nötig, 
        // dann kann Instanz der nichtstatischen Memberklasse erstellt werden

        Bank bank = new Bank();   
        Bank.Tresor tresor = bank.new Tresor(100.0);
    }
}
```

Die Qualifizierung `AeussererTyp.GeschachtelterTyp` bedeutet nicht, dass `AeussererTyp` ein Paket ist, in dem die Klasse `GeschachtelterTyp` existiert.
Die Doppelbelegung des Punktes kann zu Verwechslungen zwischen inneren Klassen und Paketen führen. Deshalb sollte die Namenskonvention beachtet werden:

* Klassennamen beginnen mit Großbuchstaben
* Paketnamen beginnen mit Kleinbuchstaben

Der Compiler generiert folgende Klassen:

* AeussererTyp.class
* AeussererTyp$GeschachtelterTyp.class

Sie können nun den zweiten Teil der Übung Würfel aus der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus Kapitel 07 machen. 

>**3. Lokaler (innerer) Typ**

Lokale Klassen stehen in Anweisungsblöcken von Methoden, Konstruktoren und Initiatialisierungsblöcken. Es gibt keine Sichtbarkeitsmodifizierer. Es gibt weder Klassenattribute noch Klassenmethoden.
Finale Konstanten sind möglich. Es gibt keine lokalen Schnittstellen. Das bedeutet: Auf die lokale Klasse kann immer nur innerhalb des jeweiligen Kontextes zugegriffen werden. 

Beispiel:

```java
public class Bank{
    private double vermoegen = 40.0;

    public double getVermoegen() {
        {
        // Lokale Klasse ohne Sichtbarkeitsmodifikator, 
        // lokale Klasse nur sichtbar im Kontext des Getters in diesem Beispiel
        // geschweifte Klammer machen Kontext deutlich
        
        class Tresor{
            private double vermoegen = 50.0;
            private double getInhalt(){
                return vermoegen;
            }
        }
        // Innerhalb des Kontexts können Instanzen erzeugt werden und private Methoden aufrufen
        Tresor tresor = new Tresor();
        return vermoegen + tresor.getInhalt;
        }
    }
}
```

Verwendung:

```java
public class BankAnwendung{

    public static void main(String[] args){
        Bank bank = new Bank();   
        System.out.println(bank.getVermoegen());
    }
}
```

Überlegen Sie sich, welches Vermögen hier ausgegeben wird.

Sie können nun den dritten Teil der Übung Würfel aus der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus Kapitel 07 machen. 

>**4. Anonyme innere Klasse**

Anonyme innere Klassen haben keinen Namen und erzeugen immer automatisch ein Objekt. Es gibt nur eine einzige Instanz, d.h. im Gegensatz zu lokalen Klassen kann von anonymen Klassen nur eine einzige Objektinstanz erzeugen werden. 

```
new KlasseOderSchnittstelle() {
    /* Eigenschaften der inneren Klasse */
}
```

Im Block { } können Methoden und Attribute deklariert oder Methoden überschrieben werden. `new Klassentyp(…){…}` erzeugt eine Unterklasse von Klassentyp. Es lassen sich Argumente für den Konstruktor der Oberklasse angeben. `new Schnittstellenname (…){…}` bewirkt, dass die Schnittstelle Schnittstellenname implementiert wird. Es lassen sich keine zusätzlichen extends oder implements angeben.

Beispiel:

```java
public class Bank{
    private double vermoegen = 40.0;

    public double getVermoegen() {
        {
            Tresor tresor = new Tresor(){
                @Override
                public double getInhalt() {
                    return 50.0;
                }
            };
            return vermoegen + tresor.getInhalt();
        }
    }
}        
```

```java
public abstract class Tresor{
    public abstract double getInhalt();
}
```

Verwendung:

```java
public class BankAnwendung{

    public static void main(String[] args){
        Bank bank = new Bank();   
        System.out.println(bank.getVermoegen());
    }
}
```

Überlegen Sie sich wiederum, welches Vermögen hier ausgegeben wird.

Sie können nun den vierten Teil der Übung Würfel aus der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus Kapitel 07 machen. 

### Übungen

Machen Sie nun alle offenen Aufgaben aus der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus Kapitel 07.


## Exkurs: Enums

Enumerationen (kurz: Enums) sind spezielle Typen, die eine Menge von konstanten Werten repräsentieren. 
Sie bieten eine Möglichkeit, eine begrenzte Menge von konkreten Werten zu definieren, die eine Variable annehmen kann.
Enums werden oft verwendet, um eine Gruppe von verwandten Konstanten zu definieren, die in einem klar definierten Kontext verwendet werden sollen. 

Beispiele sind die Tage der Woche, Monate des Jahres, die Richtungen (Norden, Süden, Osten, Westen) oder die Zustände eines Objekts (z.B. "aktiv", "inaktiv", "ausgefallen"), Farben, Prioriäten (z.B. "niedrig", "normal", "hoch").

Angelegt werden Sie in Eclipse mit rechte Maustaste auf das Projekt / Paket -> New -> Enum.

```
// Schlüsselwort enum
public enum Wochentag {
    MONTAG, DIENSTAG, MITTWOCH, DONNERSTAG, FREITAG, SAMSTAG, SONNTAG;
}
```

Vorteil von Enums sind, dass keine Vermischung verschiedener Typen mehr möglich ist. Enums können auch durchwandert werden, wie im folgenden Beispiel.

```
public class HierNunMeineKlasse{
    public static void main(String[] args){   
        Wochentag montag = Wochentag.MONTAG;
        System.out.println(montag);

        for (Wochentag wochentag : Wochentag.values()){
            System.out.println(wochentag);
        }
    }
}
```

Weiterhin können Enumerations zusätzliche Werte aufnehmen:

```
public enum Prioritaet{
    //Impliziter Aufruf des Konstruktors
    NIEDRIG(-1), NORMAL(0), HOCH(1);
    private int wert;
    
    //Privater Konstruktor
    private Prioritaet(int wert){
        this.wert = wert;
        }
    
    public int wert(){
        return wert;
    }
}
```

Verwendung in einer Klasse:

```
Prioritaet prio = Prioritaet.HOCH;
System.out.println(prio.wert()); 
```

Enums können auch einfach innerhalb eines switch-Statements verwendet werden:

```
Prioritaet prio = Prioritaet.HOCH;

switch (prio){
    case HOCH:
        ...
        break;
    case NORMAL:
        ...
        break;
    case NIEDRIG:
        ...
        break;
    default:
        break;
}
```


### Übung

Sie können in der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus der Kategorie sonstige Übungen nun die Aufgaben Jahreszeiten und Monate lösen. 

## Collections & Maps

Wir haben bisher mit Arrays gearbeitet um primitive Datentypen oder Objekte des gleichen Typs zu speichern. Sie haben schon gemerkt, dass das Arbeiten mit Arrays zum Teil sehr mühsam sein kann, da sie eine feste Länge haben und es keine vordefinierten Methoden für das Hinzufügen, Entfernen oder Suchen von Elementen gibt. 

In diesem Kapitel werden wir uns Collections und Maps beschäftigen, welche zwei wesentliche Bestandteile des Java Collections Frameworks sind. Collections und Maps bieten viele Vorteile. Sie können dynamisch ihre Größe ändern, was das Hinzufügen oder Entfernen von Elementen erleichtert, sie bieten Methoden für gängige Operationen, was die Verwendung bequemer macht und sie unterstützen Generics (siehe Kapitel Generics), was das Daten mit jedem Datentyp ermöglicht.

Collections sammeln Elemente (gleichen Typs) und stellen Methoden zum Eintragen, Suchen und Durchwandern zur Verfügung.
Interfaces (Set, List, Queue, Deque) definieren hierbei das allgemeine Verhalten (d.h. sie definieren nur Methoden, haben aber keine Implementierung). 
Die konkrete Implementierung wird dann in der konkreten Klassen (z.B. ArrayList, LinkedList) zur Verfügung gestellt, jeweils mit unterschiedlichen Techniken. 

Collections sind im Paket java.util enthalten. 
Siehe auch:  https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/doc-files/coll-overview.html

Eine Übersicht über die in dieser Vorlesung behandelten Klassen gibt auch folgende Grafik:

![Overview over collections](CollectionsMapsOverview.png)

Oben sehen Sie die Interfaces des Collection Frameworks (hellgrau hinterlegt), links die Interfaces, welche zu java.util.Collection gehört, rechts die Interfaces von java.util.Map.
Unten im Bild (dunkelgrau hinterlegt) stehen dann die konkreten Klassen mit den jeweiligen Implementierungen. 
Streng genommen sind Maps keine Collections, sie können jedoch wie Collections genutzt werden, so dass wir dies

Die allgemeine Form der Deklaration einer Collection lautet:

```
CollectionIF<Typ> coll = new CollectionKlasse<>();
// zum Beispiel
List<Konto> konten = new ArrayList<>();
```

`List` ist hierbei die Deklaration der Variablen auf Basis des Interfaces. Dies hat den Vorteil, dass die konkrete Implementierung später ausgetauscht werden kann.
`Konto` ist die Angabe des Typs, der gesammelt werden soll. 
`konten` ist der Name der Variablen. 

Mit `ArrayList<>()` rufen Sie den Konstruktor der konkreten, implementierenden Klasse auf, alternativ kann der Typ in den Diamond-Klammern wiederholt werden. 

In folgender Tabelle erhalten Sie einen Überblick über die Interfaces des Java-Collection-Frameworks:

| Interface  | Charakteristik   | Nutzung   |
| :--------- | :--------- | :--------- |
| Set<T>     | Ungeordnete Menge von Elementen | Prüfung auf "enthalten" |
| SortedSet<T>     | Geordnete Menge von Elementen (gemäß Sortierung) | Prüfung auf "enthalten" |
| List<T>     | Indizierte Menge von Elementen | Zugriff über Index |
| Deque<T>     | Geordnete Menge von Elementen (als Stack oder Queue) | Einfügen vornde oder hinten, Auslesen gemäß Einfügereihenfolge |
| Map<K,V>     | Über Schlüssel indizierte Menge von Elementen | Assoziativer Zugriff key -> value |

Nachfolgende Tabelle gibt Ihnen nun einen Überblick über die konkreten Implementierungen der jeweiligen Interfaces. 

| Interface  | Klasse   | Charakteristik  | Nutzung  |
| :--------- | :--------- | :--------- | :--------- |
| Set    | HashSet  | Hash-Werte   |   |
| SortedSet    | TreeSet  | sortierter Baum |    |
| List    | ArrayList  | Array-Datentyp |Effizienz beim Zugriff  |
| List    | LinkedList  | Knoten und Zeiger   | Effizienz beim Einfügen  |
| Deque    | ArrayDeque  | Array-Datentyp    | Effizienz beim Zugriff    |
| Deque    | LinkedList  | Knoten und Zeiger   | Effizienz beim Einfügen   |
| Map    | HashMap  | Keys als HashSet    |    |
| SortedMap    | TreeMap  | Keys als TreeSet     |     |

>**Methoden des Interface Collection**

* `add(E e)` fügt Element e ein
* `clear()` leert die Liste
* `contains(Object o)` prüft, ob o in der Liste ist
* `isEmpty()` prüft, ob Liste leer ist
* `remove(Object o)` entfernt das (zuerst) vorkommende o aus der Liste
* `size()` liefert die Anzahl der vorhandenen Elemente

Weitere Methoden finden Sie unter:
https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/util/Collection.html


>**Methoden des Interface Map**

* `put(key, value)`: Verknüpft den angegebenen Wert mit dem angegebenen Schlüssel in dieser Map
* `get(key)`: Gibt den Wert zurück, auf den der angegebene Schlüssel abgebildet ist, oder null, wenn diese Map keine Abbildung für den Schlüssel enthält

Weitere Methoden finden Sie unter:
https://docs.oracle.com/en/java/javase/21/docs//api/java.base/java/util/Map.html


### Listen

Eine Liste ist ein geordnete Sammlung von Elementen, d.h. sie speichert Elemente in einer bestimmten Reihenfolge, die durch ihren Index zugänglich ist. Elemente können auch mehrfach vorkommen. Man kann Elemente zu einer Liste dynamisch hinzufügen und entfernen.

Das Interface java.util.List erweitert das Collection-Interface und fügt weitere Methoden in Bezug auf die Position eines Elements hinzu:

* `add(E e)` fügt das Element e am Ende an
* `add(int i, E e)` fügt das Element e an der Stelle i ein – alle Elemente danach werden verschoben.
* `get(int i)`  liefert das Element an der Position i
* `set(int i, E e)` ersetzt das Element an der Stelle i mit e 
* `remove(E e)` entfernt das (zuerst) vorkommende e aus der Liste – alle Elemente danach werden verschoben.
* `remove(int i)` entfernt das Element an der Stelle i – alle Elemente danach werden verschoben


Implementierende Klassen (im Paket java.util):

* ArrayList: Grundlage ist ein Array
* LinkedList: Verkettete Elemente, jedes Listenelement beinhaltet ein Hilfsobjekt

Deklaration (Beispiel):

* List<Integer> list = new ArrayList<>();
* List<Integer> list = new LinkedList<>();

Vergleichen wir nun die Implementierungen. Dies hilft Ihnen dann auchzu entscheiden, wann Sie welche Implementierung nutzen sollten:

Zugriff auf ein Element

* ArrayList: Schnell
* LinkedList: Zeitaufwändig

Element einfügen oder löschen

* ArrayList: Zeitaufwändig
* LinkedList: Schnell

Größe des reservierten Speicherplatzes

* ArrayList: Ggf. Anlage eines neuen, größeren Arrays nötig
* LinkedList: Speicheranforderungen immer nur für neues Element

Ihr Programm läuft mit beiden Implementierungen (es arbeitet ja auf dem Interface „List“.) Die Wahl der Implementierung bestimmt „nur“ die Performance.

>**ArrayList**

Definiert ein Feld (Array) mit prinzipiell unbeschränkter Größe, welches bei Bedarf dynamisch wächst.
Bei der Deklaration muss deshalb keine Größe mit gegeben werden, es sollte jedoch ein „Typparameter“ mitgegeben werden. 
Dieser Parameter kann nur eine Klasse sein – deshalb muss statt den primitiven Typen deren Hüllklasse verwendet werden.

Beispiel: `List<Integer> list = new ArrayList<>();`

Beispiel-Operationen für ArrayList<T> (T steht für den Typ der abgespeichert werden soll):

* `add(T t)` fügt das Element t am Ende an
* `get(int i)` liefert das Element an der Position i – wie beim Feld beginnt der Index bei 0
* `add(int i, T t)` fügt das Element t an der Stelle i ein – alle Elemente danach werden verschoben.
* `set(int i, T t)` ersetzt das Element an der Stelle i mit t 
* `remove(T t)` entfernt das (zuerst) vorkommende t aus der Liste – alle Elemente danach werden verschoben.
* `remove(int i)` entfernt das Element an der Stelle i – alle Elemente danach werden verschoben.
* `size()` liefert die Anzahl der vorhandenen Elemente
* `clear()` leert die Liste
* `contains(T t):boolean` prüft ob t in der Liste ist

Wie zuvor erfolgt eine `ArrayOutOfBoundsException` bei illegalem Zugriff.

Betrachten Sie nun folgendes Beispiel zur Nutzung einer Liste.

```java
import java.util.ArrayList;
import java.util.List;

public class BeispielArrayList {
    public static void main(String[] args){
        List<String> monate = new ArrayList<String>();
        monate.add("Januar");
        monate.add("Februar");
        System.out.println("Größe der Liste: " + monate.size());
        System.out.println("Erster Monat: " + monate.get(0));
    }
}
```
@LIA.java(BeispielArrayList)

Die Klasse `Collections` bietet statische Methoden zur Verarbeitung von Arrays. Erweitern Sie das Beispiel, in dem Sie weitere Monate hinzufügen und dann den Befehl `Collections.sort(monate)` hinzuführen. Vergessen Sie nicht, hierfür den passenden Import aufzurufen: `import java.util.Collections;` 

* Was ist mit Ihrer Liste passiert? Geben Sie die Liste aus. 
* Nach welchen Kriterien wurde diese sortiert und warum?
* Probieren Sie weitere Methoden für ArrayLists aus.
* Sie wollen nun eine LinkedList statt einer ArrayList verwenden. An welcher Stelle müssen Sie den Code ändern?

>**Übungen**

Sie können nun die Aufgaben Wochentage, Wunschliste und Kofferpacken aus der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus Kapitel 08 machen.

### Mengen

Eine Menge (engl. Set) eine Sammlung von einzigartigen Elementen, das bedeutet jedes Element kann in einer Menge nur einmal vorkommen. 

Implementierende Klassen (im Paket java.util) sind unter anderem

* HashSet: Aufbauend auf der HashMap (siehe „Assoziativspeicher“)
* TreeSet: Balancierte Binärbäume, sortierbar
* LinkedHashSet: Klasse behält die Einfügereihenfolge bei

Deklaration (Beispiel):

* Set<Integer> set = new HashSet<>();
* Set<Integer> set = new TreeSet<>();

Das Interface java.util.List erweitert das Collection-Interface und fügt weitere, spezifische Methoden hinzu:

* `addAll()` bedeutet die Vereinigung zweier Mengen
* `removeAll()` bedeutet die Differenz zweier Mengen
* `retainAll()` bedeutet die Schnittmenge zweier Mengen
* `containsAll()` berechnet, ob eine Menge eine Teilmenge einer anderen Menge ist

Beispiel: 

```java
import java.util.HashSet;
import java.util.Set;

public class BeispielSet {
	public static void main(String[] args) {
		Set<Integer> zahlen = new HashSet<>();
		zahlen.add(1);
		zahlen.add(2);
		zahlen.add(3);
		zahlen.add(1);
		System.out.println(zahlen);
		
		// Mit Set.of können unveränderliche Mengen erzeugt werden
		Set<Integer> geradeZahlen = Set.of(2,4,6,8);
		System.out.println(geradeZahlen);
		// diese Anweisung liefert eine Fehlermeldung
		// geradeZahlen.add(10);
	}
}
```
@LIA.java(BeispielSet)

>**Aufgabe**

* Erstellen Sie eine HashSet A mit allen geraden Zahlen von 2 bis 40.
* Erstellen Sie eine HashSet B mit allen Teilern von 20. 
* Geben Sie die beiden Menge aus.
* Bilden Sie nun die Schnittmenge, so dass in A diejenigen Elemente erhalten bleiben, die auch in B vorkommen. Geben Sie die Lösungsmenge aus.
* Nutzen Sie nun eine TreeSet für die gleiche Aufgabe. Was fällt auf?

>**Übungen**

Sie können nun die Aufgaben MathSet und Tator aus der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus Kapitel 08 machen.

### Queues

Das Interface Queue (deutsch: Schlange) erweitert das Collection-Interface. Das Interface Deque (= „double ended queue“) erweitert wiederum das Queue-Interface. 

>**Queues**

Die Verarbeitung einer Queue erfolgt nach dem FIFO-Prinzip: First In, First Out. Das Element, welches zuerst hinzugefügt wurde, wird auch zuerst entfernt.
Implementierende Klassen (im Paket java.util) von dem Interface Queue sind z.B. LinkedList und die ArrayDeque.

Die Deklaration sieht für eine Queue beispielsweise folgendermaßen aus:

```
Queue<String> queue = new LinkedList<>();
```

Methoden der Queue sind:

* Zum Hinzufügen von Elementen: `add(e)` bzw. `offer(e)`
* Zum Entfernen von Elementen: `remove()` bzw. `poll()`
* Zum Abfragen des ersten Elements (ohne diese zu entfernen): `element()` bzw. `peek()`

Unterschiede der jeweils zwei Methoden für obige Operationen liegen in den Rückgabewerten:

* `add(e)` liefert true zurück, wenn das Element erfolgreich hinzugefügt werden konnte, ansonsten wird eine Exception geworfen (IllegalStateException), für eine genauer Erklärung, siehe Kapitel Exception
* `offer(e)` liefert nur einen Booleschen Wert zurück
* `poll()` gibt null zurück, sollte kein Element mehr in der Queue sein, während `remove()` eine Exception wirft (NoSuchElementException)
* `peek()` gibt null zurück, sollte kein Element mehr in der Queue sein, während `element()` eine Exception wirft (NoSuchElementException)

Eine Übersicht zur Queue finden Sie auch hier: https://docs.oracle.com/en/java/javase/21/docs//api/java.base/java/util/Queue.html#element()


Beispiel:

```java
import java.util.LinkedList;
import java.util.Queue;

public class BeispielQueue {

	public static void main(String[] args) {
		Queue<String> schlange = new LinkedList<>();
		schlange.offer("Herr Maier");
		schlange.offer("Frau Müller");
		schlange.offer("Herr Mustermann");
		while (schlange.peek()!= null) {
			System.out.println("Hallo " + schlange.poll());
		}
	}
}
```
@LIA.java(BeispielQueue)


>**Deques**

Eine Deque (Double Ended Queue) kann nun im Gegensatz zu einer Queue Elemente an beiden Enden verwalten und sowohl als Stapel (LIFO - Last-In-First-Out) als auch als Schlange (FIFO - First-In-First-Out) verwendet werden kann. Implementierende Klassen (im Paket java.util) von dem Interface Deque sind z.B. LinkedList und die ArrayDeque. Sie erkennen hier, dass eine LinkedList die Interfaces List, Queue und Deque (und weitere) implementiert.

Spezielle Methoden, die für eine Deque relevant sind, sind `addFirst(e)`, `offerFirst(e)`, `addLast(e)`, `offerLast(e)`, `removeFirst()`, `pollFirst()`, `removeLast()`, `pollLast()`,`getFirst()`, `peekFirst()`, `getLast()` und `peekLast()`,, um Elemente hinzuzufügen, zu entfernen und auf die ersten und letzten Elemente zuzugreifen.

Eine Übersicht zur Deque finden Sie auch hier: https://docs.oracle.com/en/java/javase/21/docs//api/java.base/java/util/Deque.html

Beispiel:

```java
import java.util.Deque;
import java.util.LinkedList;

public class BeispielDeque {
	public static void main(String[] args) {
		Deque<String> deque = new LinkedList<String>();
		deque.offer("Erstens"); // entspricht offerLast()
		deque.offerFirst("Zweitens");
		deque.offerLast("Drittens");
		
		// Wie sieht die Deque nun aus?
		while (!deque.isEmpty()) {
			System.out.println(deque.poll()); //entspricht pollFirst()
		}
	}
}
```
@LIA.java(BeispielDeque)

>**Übungen**

Sie können nun die Aufgabe Fährterminal aus der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus Kapitel 08 machen.

### Maps
In diesem Abschnitt schauen wir uns nun das Interface Map an, welches ebenso im Paket java.util zu finden ist. Es ist jedoch keine Erweiterung des Interfaces Collection, wird jedoch oft im Zusammenhang des Collection-Frameworks mitangeführt. Ein für Sie relevantes Subinterface von Map ist die SortedMap.

Eine Map stellt Schlüssel-Wert-Paare dar, wobei jeder Schlüssel eindeutig ist und einem bestimmten Wert zugeordnet wird. Eine Map kann keinen duplizierten Schlüssel enthalten. Wenn ein Schlüssel bereits vorhanden ist und ein neuer Wert für ihn zugewiesen wird, wird der alte Wert überschrieben. Es gibt jedoch (im Gegensatz zur List), keine Position eines Schlüssels oder eines Wertes.

Folgende zwei Methoden sind hierbei die wichtigsten:

* `put(key, value)`: Verknüpft den angegebenen Wert mit dem angegebenen Schlüssel in dieser Map
* `get(key)`: Gibt den Wert zurück, auf den der angegebene Schlüssel abgebildet ist, oder null, wenn diese Map keine Abbildung für den Schlüssel enthält

Implementierende Klassen von Map sind zum Beispiel HashMap und TreeMap. Eine implementierende Klasse von SortedMap ist ebenso TreeMap.

Bei der HashMap müssen die Schlüsselobjekte die Methoden equals() und hashCode() implementieren.
Bei der TreeMap muss die Ordnung der Elemente mit den Interfaces Comparable oder Comparator festgelegt sein.

Die Deklaration sieht dann jeweils folgendermaßen aus:

```
Map<Integer,String> map = new HashMap<>();
Map<Integer,String> map = new TreeMap<>();
```

```java
import java.util.HashMap;
import java.util.Map;
import java.util.Set;

public class BeispielMap {

	public static void main(String[] args) {

		Map<String, Integer> tageImMonat = new HashMap<>();
		tageImMonat.put("Januar", 31);
		tageImMonat.put("Februar", 28);
		tageImMonat.put("März", 31);
		tageImMonat.put("April", 30);

		Set<String> alleSchluessel = tageImMonat.keySet();
		for (String schluessel : alleSchluessel) {
			System.out.println(schluessel + ": " + tageImMonat.get(schluessel) + " Tage");
		}
	}
}
```
@LIA.java(BeispielMap)

Schauen Sie sich obiges Beispiel an. Was sind die Schlüssel und was sind die Werte? Denken Sie daran, Schlüssel sind eindeutig, Werte können jedoch mehrfach vorkommen. 

Nachfolgend ein weiteres Beispiel, welches weitere Methoden von Maps benutzt.

```java
import java.util.HashMap;
import java.util.Map;

public class MapDemo {
	public static void main(String[] args) {
		Map<Integer, String> map = new HashMap<Integer, String>();
		map.put(1, "eins");
		map.put(2, "zwei");
		map.put(3, "drei");
		map.put(4, "vier");
		
		for(String value : map.values()) {
			System.out.println(value);
		}
		
		for (Integer key : map.keySet()) {
			System.out.println(key);
		}
		
		map.replace(3, "three");
		System.out.println(map);
	}
}
```
@LIA.java(MapDemo)

>**Übungen**

Sie können nun die Aufgabe Fussball-Map aus der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus Kapitel 08 machen.

### Iteratoren

Iteratoren liefern nacheinander alle Elemente einer Collection. Das Interface Iterator befindet sich ebenso im Paket java.util und gehört ebenso zum Collection-Framework. Jede Collection besitzt einen Iterator. 
Ein Iterator ist prinzipiell wie eine Mengenschleife, aber der Iterator kann Elemente auch löschen! Einen Iterator `iterator` zu einer Collection `collection` wird mit der Methode `collection.Iterator()` erhalten 

Methoden eines Iterators sind:

* `hasNext()`: gibt true zurück, wenn es noch mehr Elemente gibt
* `next()`: gibt das nächste Element zurück
* `remove()`: löscht das letzte Element

Beispiel: 

```java
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

public class BeispielIterator {

	public static void main(String[] args) {

		List<String> liste = new ArrayList<>();

		liste.add("drei");
		liste.add("vier");
		liste.add("eins");
		liste.add("zwei");
		
		// herkömmlich
		for(String element : liste) {
			System.out.println(element);
		}
		
		System.out.println("----");
		
		// mit Iterator
		Iterator<String> iterator = liste.iterator();
		while(iterator.hasNext()) {
			System.out.println(iterator.next());
		}	
	}
}
```
@LIA.java(BeispielIterator)

>**Übungen**

Sie können nun die Aufgabe digitaler Würfel aus der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus Kapitel 08 machen.


### Übungen

Machen Sie nun die verbleibenden Aufgaben aus der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus Kapitel 08, falls Sie noch nicht alle gelöst haben.

## Exceptions
In diesem Kapitel beschäftigen wir uns mit der Behandlung von Fehlern, was in der Programmierung ein wichtiger Bestandteil ist. Hierbei werden `Exceptions` und `Errors` unterschieden. 

`Exceptions` sind dabei unerwartete Ereignisse, die während der Ausführung eines Programms auftreten und den normalen Programmfluss unterbrechen. Sie können durch Programmierfehler, unvorhersehbare Bedingungen oder systembedingte Probleme verursacht werden. 

`Errors` hingegen sind schwerwiegende Probleme, die meistens auf systembedingte Fehler zurückzuführen sind und außerhalb der Kontrolle des Entwicklers liegen. Beispiele sind `OutOfMemoryError` und `StackOverflowError`. Diese sollten in der Regel nicht abgefangen werden, da sie auf kritische Probleme hinweisen, die eine Fortsetzung des Programms unmöglich machen.

Betrachten wir zunächst ein paar Beispiele:

>**Beispiel 1**

```java
public class BeispielArray {
    public static void main(String[] args) {
        int[] meinArray = new int[10];
        System.out.println(meinArray[2]);
   }
}
```
@LIA.java(BeispielArray)

Versuchen Sie das Beispiel dermaßen abzuändern, dass auf ein Arrayfeld mit falschem Index zugegriffen wird. Sie können den Code dennoch im Workbook laufen lassen. Sie sehen als Ausgabe dann die Meldung der Exception.  

```java
public class BeispielArray {
    public static void main(String[] args) {
        int[] meinArray = new int[10];
        System.out.println(meinArray[10]); //Zugriff auf ein Array mit falschem Index
   }
}
```

![](Exception-1.png)

>**Beispiel 2**

```java
public class EndlosRekursion {
    public static void main(String[] args) {
        endlosRekursion();
   }

    public static void endlosRekursion() {
        endlosRekursion();
   }
}
```
![](Exception-2.png)

<h3 style="text-align:center">Fehlerarten in Java</h3>

Wie oben bereits erwähnt, gibt es zwei Fehlerarten: `Exceptions` und `Errors`. Beides sind Objekte, die von der Klasse Throwable abgeleitet sind, wie in folgender Grafik ersichtlich. 

![](Exceptions-3.JPG)

Hier die wichtigsten Punkte zusammengefasst.

- Exception ist die Mutterklasse aller Ausnahmen, während java.lang.Error die Mutterklasse aller Fehler ist.
- Beide Klassen haben die gemeinsame Oberklasse java.lang.Throwable.
- Alles, was "throwable" ist, kann innerhalb eines Programms von einer Methode an die aufrufende Methode geworfen werden.
- In Java unterscheidet man zwischen Fehlern (Errors) und Ausnahmen (Exceptions).
- Ausnahmen sind in der Regel behandelbare Fehlerfälle, während Fehler schwerwiegende Probleme darstellen, die normalerweise nicht behandelt werden können.
- Exceptions sind Klassen, die von java.lang.Exception abgeleitet sind.

![](Exception-4.JPG)

>**Strukturierte Fehlerbehandlung**

Wie werden Fehler nun strukturiert behandelt?

- Im Fall behebbarer Fehler wird eine "Ausnahme" mit Informationen über den Fehler erzeugt.
- Die Ausnahme wird an die jeweils aufrufende Methode weitergereicht.


  * Wenn diese Methode untätig bleibt ⟶ Ausnahme wird hochgereicht
  * Eine aufrufende Methode kann den Fehler „abfangen“
  * Im „worst-case“ bricht die Programmausführung ab
 
Wenn wir Fehler und Ausnahmen nicht behandeln und auf diese reagieren, wird der geworfene Fehler auf der Konsole ausgegeben. Das bedeutet, wir wollen diese an der richtigen Stelle behandeln und wie das funktioniert, wird nun in den folgenden Unterkapiteln erklärt.

### Exceptions werfen und fangen

Um eine Exception zu behandeln, verwendet man in Java die Schlüsselwörter `try`, `catch`, `finally` und `throw`.

* `try`: Der Code, der potenziell eine Exception verursachen könnte, wird in einem try-Block platziert.
* `catch`: Falls eine Exception auftritt, wird sie von einem catch-Block abgefangen, der die Ausnahme behandelt.
* `finally`: Dieser Block wird immer ausgeführt, unabhängig davon, ob eine Exception aufgetreten ist oder nicht. Er eignet sich für Aufräumarbeiten wie das Schließen von Ressourcen.
* `throw`: Mit diesem Schlüsselwort wird eine Exception manuell ausgelöst.

Betrachten wir hierzu folgendes Beispiel, zunächst nur mit `try` und `catch`:

```java
public class BeispielNullpointer1 {
    public static void main(String[] args) {
        String[] meinStringArray = new String[10];

        try {
            System.out.println(meinStringArray[2].equals("null"));
        } 
        catch(NullPointerException e) {
            System.out.println("Vergleich mit Null nicht möglich");
        }
   }
}
```
@LIA.java(BeispielNullpointer1)

- Der `try-Block` überprüft, ob etwas nicht funktioniert
- Der `catch-Block` ist dann zum Behandeln der Ausnahme da

  
  * In diesem Fall eine `NullPointerException`, also eine Exception, die man abfangen möchte

  * `e` beinhaltet Informationen über das Problem, dies ist die gängige Namenskonvention für `Exceptions`
- Das Programm läuft nach der Ausnahme normal weiter


>**Finally-Block**

Nun ein Beispiel mit zusätzlichem`finally`-Block:

```java
public class BeispielNullpointer2 {
    public static void main(String[] args) {
        String[] meinStringArray = new String[10];

        try {
            System.out.println(meinStringArray[2].equals("null"));
        } 
        catch(NullPointerException e) {
            System.out.println("Vergleich mit Null nicht möglich");
            e.printStackTrace();
        }
        finally {
            System.out.println("Dies wird immer ausgeführt.");
        }
   }
}
```
@LIA.java(BeispielNullpointer2)

- `finally`-Block (optional) wird immer ausgeführt, egal ob Exception geworfen wird oder nicht; muss am Schluss stehen


  - Zweck des `finally`-Blocks: z.B. Schließen von Dateien

  - Falls im finally-Block ein Fehler auftreten kann, müssen ggf. weitere `try`-Blöcke stehen
- `printStackTrace()` ist die Standardfehlerausgabe der Exception

>**Mehrere Catch-Blöcke**

Es sind auch mehrere catch-Blöcke möglich:

Wenn die erste `catch`-Anweisung nicht zur Art des aufgetretenen Fehlers passt, werden der Reihe nach alle übrigen `catch`-Anweisungen untersucht, und die erste übereinstimmende wird ausgeführt

```java
public class BeispielNullpointer3 {
    public static void main(String[] args) {
        String[] meinStringArray = new String[10];

        try {
            System.out.println(meinStringArray[10]);
        } 
        catch(NullPointerException e) {
            System.out.println("Vergleich mit Null nicht möglich");
            e.printStackTrace();
        } 
        catch(Exception e) {
            System.out.println("Ein Problem ist aufgetreten");
        }
        finally {
            System.out.println("Dies wird immer ausgeführt");
        }
   }
}
```
@LIA.java(BeispielNullpointer3)

>**Mehrere Exceptions in einem Catch-Block**

In einem `catch`-Block kann man auch mehrere Exceptions fangen:

- Klassennamen durch | (Strich) getrennt angeben
- Es gibt nicht für jede der gefangenen Exceptions eine eigene Variable, sondern nur eine gemeinsame


```java
public class BeispielNullpointer4 {
    public static void main(String[] args) {
        String[] meinStringArray = new String[10];

        try {
            System.out.println(meinStringArray[10]);
        } 
        catch(NullPointerException | ArrayIndexOutOfBoundsException e) {
            System.out.println("Vergleich mit Null nicht möglich oder falscher Index");
            e.printStackTrace();
        } 
        finally {
            System.out.println("Dies wird immer ausgeführt");
        }
   }
}
```
@LIA.java(BeispielNullpointer4)

>**Übersicht: Aufbau try/catch/finally**

Zusammengefasst:

- Es gibt immer mindestens zwei Blöcke:


  * try / (catch)+
  * try / (catch)* / finally



- Notation:


  * +: Mindestens ein catch
  * *: Kein oder beliebig viele catch


>**Eigene Exceptions**

- Exceptions sind nicht anderes als Klassen, die von java.lang.Exception ableiten, d.h. wir können auch eigene Exceptions erstellen.
- Über den Konstruktor kann direkt eine angepasste Fehlernachricht mitgegeben werden, falls dies gewünscht wird. 

Schauen Sie sich beide Punkte im untenstehenden Beispiel an.

```java
public class DivisionsCheckException extends Exception {

    public DivisionsCheckException() {
        super("Division war nicht erfolgreich");
    }

     public DivisionsCheckException(String message) {
        super(message);
    }

}
```


Achtung: Wenn Sie eine eigene Exception erstellen, warnt Eclipse, dass keine serialVersionUID angegben wird. Dies können Sie in diesem Semesternoch ignorieren.


>**Behandeln vs. Weiterleiten**

Bisher haben wir die Exception behandelt. Dies bedeutet, dass diese direkt im `catch`-Block aufgefangen und dort eine entsprechende Reaktion oder Fehlerbehebung vorgenommen wird. Weiterleiten dagegen bedeutet, dass die Exception nicht direkt behandelt, sondern an eine höhere Ebene der Programmausführung weitergegeben wird, indem sie mit dem Schlüsselwort `throws` in der Methodensignatur angegeben wird.

Vergleichen Sie hierzu folgendes Beispiel:

```java
public class DivisionTest {
    
	public static void main(String[] args) {
		
		// "Behandeln"
            try {
				System.out.println(dividieren(10, 3));
			} catch (DivisionsCheckException e) {
				e.printStackTrace();
			}        
    }

    // Über throws angeben, dass Methode eine Exception werfen könnte
    static int dividieren(int a, int b) throws DivisionsCheckException { 
        int c = a / b;

        if (a % b != 0) {
            // Innerhalb der Methode Exception mit Schlüsselword throw werfen, damit wird die Ausnahme ausgelöst
            throw new DivisionsCheckException("Division geht nicht auf"); 
        }
		return c;
   }
}
```


Aufgabe: 

Programmieren Sie obiges Beispiel in Eclipse nach und erstellen Sie die dazugehörige notwendige Exception. Von welcher Exception würde Sie Ihre spezielle `DivisionsCheckException` ableiten? 

>**Weitere Anmerkungen zu Exceptions**

- Exceptions sind normale Klassen, d.h. man kann eigene Unterklassen erstellen
- Dies macht z.B. Sinn, wenn eine Exception ein Spezialfall einer anderen Exception darstellt
- Bei catch-Blöcken auf richtige Reihenfolge achten (erst die spezielle, dann die allgemeine Exception fangen) 
- In einem catch-Block können mehrere Exceptions gefangen werden (Klassennamen durch | getrennt angeben)
- Beim Fangen der allgemeinen Exception java.lang.Exception verliert man Flexibilität
- Exceptions sollten dort behandelt werden, wo man angemessen, auf die Exception reagieren kann
- Exceptions mit angepassten, nutzerfreundlichen Meldungen versehen
- Produktive Programme:

Generell kann man grob sagen: Unter ein Drittel des Codes ist für eigentliche Funktionalität und über zwei Drittel des Codes sind für die Fehler-/Ausnahmenbehandlung.


### Unchecked Exceptions
- Bisher: `Checked Exceptions` (überprüfte/geprüfte Exceptions):
  
  
  * Compiler prüft, ob Exception behandelt wird
  * Beschreiben fachliche Fehler, d.h. diese müssen vom Entwickler vorhergesehen und explizit behandelt werden

- `Unchecked Exceptions` (ungeprüfte Exceptions):
    
  * Werden vom Compiler nicht beachtet
  * Sind Laufzeitfehler
  * Treten auf, wenn der Code fehlerhaft programmiert ist bzw. Schwachstellen hat
  * Haben Oberklasse `java.lang.RuntimeException`
  * Beschreiben technische Fehler, d.h. diese müssen nicht explizit behandelt werden

>**Übersicht einiger Runtime-Exceptions**

![](Exception-5.svg)

| Exception                      | Beschreibung                                                                                                                |
|--------------------------------|-----------------------------------------------------------------------------------------------------------------------------|
| ArithmeticException            | Wird geworfen, wenn beim Rechnen mit den Zahlen nicht aufpasst wird, z.B. durch Division durch Null.                          |
| ArrayIndexOutOfBoundsException | Tritt auf, wenn versucht wird, auf einen Array-Index außerhalb des Arrays zuzugreifen.                                       |
| ClassCastException             | Tritt auf, wenn versucht wird, eine Objektreferenz in einen nicht kompatiblen Typ umzuwandeln.                               |
| IllegalArgumentException       | Tritt auf, wenn ein ungültiger Parameter an eine Methode übergeben wurde.                                                   |
| NumberFormatException          | Wird geworfen, wenn bei der Umwandlung eines Strings in eine Zahl ein nicht-zahlartiger Wert übergeben wird.                |
| IllegalStateException          | Tritt auf, wenn eine Methode in einem ungültigen Zustand des Programms aufgerufen wurde.                                    |
| NullPointerException           | Tritt auf, wenn versucht wird, auf eine Methode auf einer Objektreferenz zuzugreifen, die den Wert null hat.                 |


> **Defensiv Programmieren**

Das Ziel hier für heißt defensiv programmieren. Dies bedeutet, den Code so zu schreiben, dass er robust gegenüber unerwarteten Eingaben oder Zuständen ist, indem er potenzielle Fehlerquellen proaktiv abfängt und behandelt. Im Zusammenhang mit Unchecked Exceptions wie `NullPointerException` oder `ArrayIndexOutOfBoundsException` bedeutet dies, präventive Prüfungen und Validierungen durchzuführen, um solche Ausnahmen zu vermeiden, bevor sie auftreten. Betrachten Sie hierzu untenstehende Beispiele:

| Code, der eine Exception werfen könnte                            | Exception, die geworfen werden könnte | Nicht fangen, sondern besser ...                                                                                                     |
|-------------------------------------------------------------------|-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|
| int x = array[index];                                             | ArrayIndexOutOfBoundsException         | ... mit index < array. length vorher prüfen, ob das Array überhaupt eine entsprechende Größe hat.                                                    |
| String name = (String) objekt;                                    | ClassCastException                     | ... mit dem instanceof-Operator prüfen, ob die Klassen kompatibel sind.                                                                   |
| (String name = null; name.toLowerCase();)                         | NullPointerException                   | ... mit name != null prüfen, ob die entsprechende Variable überhaupt initialisiert ist.           |

### Errors

Zuletzt betrachten wir `Errors`. Dies sind schwerwiegende Fehler, die man nicht mehr beheben kann. `Errors` werden ebenfalls von `Throwable` abgeleitet. Sie werden jedoch nicht vom Compiler geprüft und müssen daher auch nicht abgefangen werden.

![](Exception-8.png.svg)

> **Übersicht über einige Fehler**

| Fehler                      | Beschreibung                                                                                                                         |
|-----------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
| ExceptionInInitializerError | In einem statischen Initialisierungsblock hat etwas nicht funktioniert.                                                      |
| IOError                     | Steht für einen Fehler bei der Ein- oder Ausgabe.                                                                                    |
| NoClassDefFoundError        | Wird geworfen, wenn eine Klasse nicht gefunden wurde.                                                                                |
| StackOverflowError          | Der Stack ist übergelaufen.     |
| OutOfMemoryError            | Es gibt keinen Platz mehr auf dem Heap. |

### Zusammenfassung
> **Schlüsselwörter**
Es gibt fünf Schlüsselworte:

- `throws`: Methode kann einen Fehler erzeugen
- `throw`: Methode erzeugt tatsächlich einen Fehler
- `try`: Start eines Blocks, innerhalb dessen ein Fehler abgefangen werden kann
- `catch`: Behandeln eines Fehlers --> Die Ausnahmen sollen von „speziell“ zu „allgemein“ angeordnet sein
- `finally`: Abschluss eines Blocks zur Fehlerbehandlung, der bei normaler Verarbeitung und im Fehlerfall aufgerufen wird

> **Zusammenfassung**

- Ausnahmen werden über `Exception`-Klassen abgebildet
- Diese Klassen leiten von der Klasse `Exception` ab, die wiederum von der Klasse `Throwable` ableitet
- Alles, was `Throwable` ist, kann mit `throw` geworfen werden und mit `try-catch` gefangen werden
- Eine `RuntimeException` (und alle Unterklassen) muss nicht gefangen werden („`unchecked Exceptions`“)
- Unchecked Exceptions mit defensiver Programmierung verhindern
- Bei checked Exceptions sorgt der Compiler dafür, dass sie behandelt werden (fangen oder weiterwerfen)
- Wenn eine Methode eine checked Exception wirft, muss sie nach dem `throws` in der Methodendeklaration angegeben werden


### Übungen

Machen Sie die Aufgaben aus der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus Kapitel 09.


## Dateiverarbeitung und Datenströme

Datenströme sind grundlegende Werkzeuge zur Verarbeitung von Daten, die aus verschiedenen Quellen gelesen und in verschiedene Ziele geschrieben werden können. 

Man unterscheidet hier zwischen:

- **Eingabeströmen (Input-Streams)**: Diese werden verwendet, um Daten aus einer Datenquelle in ein Java-Programm zu lesen.
- **Ausgabeströmen (Output-Streams)**: Diese werden verwendet, um Daten aus einem Java-Programm in ein Datenziel zu schreiben. Dieses Ziel wird auch als **Datensenke** bezeichnet.


Es gibt untersschiedliche Arten von Datenströmen, wie z.B. Zeichenströme (Character Streams) oder Bytestrom (Byte Streams). 
Zeichenströme werden für die Verarbeitung von Textdaten genutzt, während Bytestrom für die Verarbeitung von binären Daten wie Bildern, Audiodateien oder anderen nicht-textuellen Daten verwendet werden.

Wir beschäftigen uns in diesem Kapitel zunächst mit Datenströmen und werden danach lernen, wie man Dateien erstellt, liest und schreibt. Zum Schluss beschäftigen wir uns im Kapitel Serialisierung mit der Umwandlung von Objekten in einen Bytestrom zur Speicherung für Objekte.


### Vorgehen

In Java gibt es das Konzept der sogenannten `Streams` oder Datenströme. 
Vorgehen

- Öffnen des Streams
- Einlesen bzw. Ausgeben des Streams
- Schließen des Streams


Für jeden Datentyp der richtige Strom:

> Byte-Streams
  
Byte-Streams sind dazu da, Daten in Form von "einzelnen" Bytes zu lesen und zu schreiben. Dies ermöglicht prinzipiell die Verarbeitung aller Dateien. Sie sind jedoch in der Regel dazu da, Binärdateien (Bilder, MP3, Videos) zu verarbeiten. 

Wenn Sie z.B. eine Text-Datei einlesen, die folgendermaßen aussieht,

```
Das ist ein Text, 
der so tut, 
als sei er eine Binaerdatei, 
dabei ist es ein Text.
```

dann kann man den Inhalt in ein Character casten und wieder auf der Konsole ausgeben. 

**Byte-Streams (einlesen)**

```java
try (InputStream eingabe = new FileInputStream(new File("./keineBinaerDatei.txt"))) {
    int zeichen;
    while ((zeichen = einbgabe.read()) != -1) {
        // System.out.print(zeichen); Ausgabe: 68971153210511511632101105110328410...
        System.out.print((char)zeichen); //Ausgabe: Das ist ein Text, 
                                        //der so tut, 
                                        //als sei er eine Binärdatei,
                                        // dabei ist es ein Text.
    }
} catch (IOException e) {

}
```

Anmerkungen zum Code:

* `InputStream` : Dies ist die abstrakte Basisklasse für Eingabe-Streams.
* `FileInputStream` : Diese Klasse öffnet einen Eingabestrom zum Lesen einer Datei.
* `File` : Dies repräsentiert die Datei, mit `new File` wird eine Objektreferenz erzeugt.
* `read()` : Diese Methode liest ein Byte des Eingabestroms, -1 bedeutet „Dateiende“. Der Rückgabewert ist vom Typ int, weil 257 Werte dargestellt werden müssen.

**Byte-Streams (ausgeben)**

Als nächstes sehen Sie ein Beispiel für das Schreiben eines Textes in eine Datei.

```java
    try(OutputStream ausgabe = new FileOutputStream(new File("meineDatei.txt"), true)) {
		ausgabe.write("Hallo, dies ist mein Text.\n".getBytes()); //Schreibe "Hallo, dies ist mein Text die Datei meineDatei.txt 
	} catch (IOException e) {
	
    }
```

* `OutputStream`: Dies ist die abstrakte Basisklasse für Ausgabe-Streams.
* `FileOutputStream`: Diese Klasse öffnet einen Ausgabestrom zum Schreiben in eine Datei.
* `write()`: Diese Methode schreibt das angegebene Byte-Array in den Ausgabestrom. Hier wird `"Hallo, dies ist mein Text.\n".getBytes()` verwendet, um den Text in ein Byte-Array zu konvertieren und dann in die Datei zu schreiben.
* `true` = Anhängen an bestehende Datei

> Character-Streams

Zweck: Verarbeiten von Textdateien

**Character-Streams: Zeichenweises Einlesen**

Character-Streams sind darauf ausgelegt, Daten in Form von einzelnen Zeichen zu lesen und zu schreiben. Hierbei können verschiedene Zeichencodierungen berücksichtigt werden.

```java
    try (FileReader dateiLeser = new FileReader(new File("./meineDatei.txt"))) {
        int zeichen;
        while ((zeichen = dateiLeser.read()) != -1) {
           System.out.print((char)zeichen);
        }
    } catch (IOException e) {
    }
```

* `FileReader`: Ist eine Klasse, die Text aus Zeichen-Dateien liest, wobei standardmäßig ein Puffer verwendet wird. Die Umwandlung von Bytes in Zeichen erfolgt dabei entweder unter Verwendung eines angegebenen Zeichensatzes oder des Standard-Zeichensatzes des Betriebssystems.
* `read()`: Die read()-Methode liest das nächste Zeichen aus dem Eingabestrom und gibt es als ASCII-Wert zurück. Wenn das Ende der Datei erreicht ist, wird -1 zurückgegeben.

**Character-Streams: Zeilenweises Einlesen**

Der BufferedReader kann Daten in einem Puffer speichern und somit die Anzahl der tatsächlichen Leseoperationen reduzieren. Dies reduziert die Verarbeitungsdauer erheblich.

```java
    try (BufferedReader dateiLeser = new BufferedReader(new FileReader(new File("./meineDatei.txt")))) {
        String zeichen;
        while ((zeichen = dateiLeser.readLine()) != null) {
           System.out.print(zeichen);
        }
    } catch (IOException e) {
    }
```
* `BufferedReader` : Liest Text zeilenweise aus einem Character-Input-Stream und verbessert die Leistung durch Pufferung (Speichern von Daten vorübergehend zur Verbesserung der Leistung).
* `readLine()` (Methode der Klasse `BufferedReader`): Textzeilen werden aus einer Datei gelesen. Die Schleife wiederholt diesen Vorgang, bis das Dateiende erreicht ist.

**Character-Streams: Zeilenweises Schreiben**

Genaus wie "gepuffert" eingeleesen werden kann, kann der eingelesene Puffer auch wieder in die Datei geschrieben werden. 

```java
    try (BufferedWriter dateiSchreiber = new BufferedWriter(new FileWriter(new File("./meineDatei.txt"), true))) {
        String zeichen;
        dateiSchreiber.write("Hallo, mein Text.");
    } catch (IOException e) {
    }
```

* `BufferedWriter`: Schreibt Text in einen Character-Output-Stream und nutzt Pufferung zur Leistungssteigerung.
* `write`: Schreibt den angegebenen Text ("Hallo, mein Text.") in den Ausgabestrom, der von dem `BufferedWriter` verwaltet wird. In diesem Fall wird der Text in die Datei "./meineDatei.txt" geschrieben.

>Fazit: Files lesen und schreiben

- Schritt 1: File-Objekt anlegen (File-Konstruktor mit Pfad zum File rufen)
- Schritt 2: Aus File-Objekt lesen (z.B. mit FileReader)
- Schritt 2a: Eingabe zeilenweise puffern (z.B. mit BufferedReader)
- Schritt 3: Input verarbeiten
- Schritt 4: Ressource schließen (am besten automatisch, Verwendung von try with resource)


>try with ressource

Anmerkung zu Schritt 4:

Dank try with resource muss man sich beim Arbeiten mit Dateien, Datenbanken und anderen Ressourcen im finally-Block nicht mehr selbst um das Schließen der Ressource kümmern. 
Voraussetzung hier für ist, dass die Ressource das Interface java.lang.AutoCloseable implementiert, wie z.B. der BufferedReader. 
Die Ressource wird in den runden Klammern hinter dem try erstellt. Exceptions werden weiterhin geworfen und müssen gefangen werden. 
Aber im finally-Block muss die Ressource nicht mehr geschlossen werden. 

```java
try(// Erstellen bzw. öffnen einer Ressource ){
    //Hier wird etwas mi der Ressource gemacht
} catch(IrgendeineException e){
    //Behandle die Exception
} finally {
    //Hier wird wieder irgendetwas gemacht
}
```

Im konkreten Beispiel:
```java
try(BufferedReader br = new BufferedReader(new FileReader("datei.txt"))){
    System.out.println(br.readLine());
} catch(FileNotFoundException e){
    e.printStackTrace();
} 
```

>Zusammenfassung

Es gibt vier abstrakte Basisklassen zum Lesen und Schreiben von Bytes bzw. Characters:


| Basisklasse für  | Bytes | Zeichen   |
| :--------- | :--------- | :--------- |
| Eingabe    | InputStream   | Reader    |
| Ausgabe    | OutputStream   | Writer    |

In diesen Klassen sind alle wesentlichen Methoden für das Lesen und Schreiben enthalten. Mehr über die darin enthaltenen Methoden können Sie im Buch [Java ist auch eine Insel](https://openbook.rheinwerk-verlag.de/javainsel/20_004.html#u20.4) von Christian Ullenboom nachlesen. 

### java.nio.file

In Java gibt es ein Paket namens `java.nio.file`, das ab Java 1.4 verfügbar ist. Dieses Paket hilft uns beim Arbeiten mit Dateien und Verzeichnissen. Hier sind die grundlegenden Konzepte und wie man sie einfach versteht:

**java.nio.file.Path**

`Path` ist eine Klasse in `java.nio.file`, die uns ermöglicht, Referenzen (Verweise) auf Dateien oder Verzeichnisse zu erstellen. Man kann sich `Path` wie einen Zeiger vorstellen, der auf eine Datei oder ein Verzeichnis zeigt.


- Helferklasse Files enthält Methoden zur Verwaltung von Dateien und Verzeichnissen


- **Beispiel:** 

  ```java
  Path path = Paths.get("example.txt");
  ```
  Die Helferklasse `Paths` liefert über `get()` eine Path-Instanz.

Das Interface `Path` bietet Methoden zur Verarbeitung des betreffenden Pfads:

- Absoluter Pfad: `toAbsolutePath()`. Dies ist ein vollständiger Pfad, der den gesamten Verzeichnispfad von der Wurzel bis zur Zieldatei oder zum Zielverzeichnis angibt. 
- Kanonischer Pfad: `toRealPath()`. Dies ist die kürzeste und doch eindeutige Form eines absoluten Pfads, bei der alle symbolischen Links und relative Pfadkomponenten wie "." und ".." aufgelöst sind.

Ein absoluter Pfad ist dabei ein vollständiger Pfad, der den gesamten Verzeichnispfad von der Wurzel bis zur Zieldatei oder zum Zielverzeichnis angibt. Ein kanonischer Pfad ist die kürzeste und eindeutigste Form eines absoluten Pfads, bei der alle symbolischen Links und relative Pfadkomponenten wie "." und ".." aufgelöst sind.

```java
Path datei = Paths.get("datei.txt");
System.out.println(datei.toAbsolutePath()); 
try {
    System.out.println(datei.toRealPath()); 
} catch (IOException e) {
    e.printStackTrace();
}
```

- Pfade können mit `resolve()` kombiniert werden. Betrachten Sie hierzu folgendes Beispiel aus dem Buch von Philipp Ackermann: Schrödinger programmiert Java, Rheinwerk.

```java
Path Schlafzimmer = Paths.get("C:\\schroedinger\\wohnung\\schlafzimmer");
Path krawatten = Paths.get("kleiderschrank\\obersteSchublade\\krawatten");
Path woSindDieKrawatten = schlafzimmer.resolve(krawatten);
System.out.println(woSindDieKrawatten); //C:\schroedinger\wohnung\schlafzimmer\kleiderschrank\obersteSchublade\krawatten

```
> Umwandlung zwischen `File` und `Path`

Manchmal muss man zwischen den alten `File`-Objekten, welche aus einem älteren Package `java.io` stammen, und den neuen `Path`-Objekten, welche aus dem "neueren" `java.nio` Package stammen, hin- und herwechseln:

- **Von `File` zu `Path`:**
  ```java
  File file = new File("Beispiel.txt");
  Path path = file.toPath();
  ```
- **Von `Path` zu `File`:**
  ```java
  Path path = Paths.get("Beispiel.txt");
  File file = path.toFile();
  ```

> `java.nio.file.Files`

`Files` ist eine Klasse in `java.nio.file`, die viele nützliche statische Methoden bietet, um mit Dateien und Verzeichnissen zu arbeiten, wie z. B. Erstellen und Löschen von Dateien und Verzeichnissen.

Schauen wir uns zunächst an, wie Dateien und Verzeichnisse erstellt werden können:

**Eine Datei erstellen:**

```java
Path path = Paths.get("Beispiel.txt");
Files.createFile(path);
```

  Hier wird eine neue Datei namens "Beispiel.txt" erstellt.

**Ein Verzeichnis erstellen:**

```java
Path dir = Paths.get("neuesVerzeichnis");
Files.createDirectory(dir);
```

  Hier wird ein neues Verzeichnis namens "neuesVerzeichnis" erstellt.

Als nächstes kommen Beispiele, wie Dateien und Verzeichnisse gelöscht werden können:

**Eine Datei löschen:**

```java
Path path = Paths.get("deleteDatei.txt");
Files.delete(path);
```

  Hier wird die Datei "deleteDatei.txt" gelöscht.

**Ein Verzeichnis löschen:**

```java
Path dir = Paths.get("deleteVerzeichnis");
Files.delete(dir);
```

  Hier wird das Verzeichnis "deleteVerzeichnis" gelöscht.

 **Eine Datei kopieren:**

 Eine Datei zu kopieren funktioniert  auch ohne Streams, Reader, Writer und dergleichen, sondern allein mit der Helferklasse `Files`. Damit wird Lesen und Schreiben noch einfacher.

```java
Path datei = Paths.get("./resources/eingabe/datei.txt");
Path andereDatei = Paths.get("./resources/ausgabe/andereDatei.txt");
Path andereDatei2 = Paths.get("./resources/ausgabe/andereDatei2.txt");
Path andereDatei3 = Paths.get("./resources/ausgabe/andereDatei3.txt");

try {
List<String> zeilen = Files.readAllLines(datei, StandardCharsets.ISO_8859_1);

Files.write(andereDatei, zeilen, StandardCharsets.ISO_8859_1);

byte[] ls = System.lineSeparator().getBytes(); 

// Zeilenweise Schreiben in "andereDatei2", jede Zeile gefolgt von einem Zeilenumbruch
for (String zeile : zeilen) {
    Files.write(andereDatei2, zeile.getBytes(), StandardOpenOption.CREATE, StandardOpenOption.APPEND);
    Files.write(andereDatei2, ls, StandardOpenOption.CREATE, StandardOpenOption.APPEND);
}

// Kopieren der Datei "datei" nach "andereDatei3", vorhandene Datei wird überschrieben
Files.copy(datei, andereDatei3, StandardCopyOption.REPLACE_EXISTING);

} catch (IOException e) {
e.printStackTrace();
}
``` 

### Zusammenfassendes Beispiel

Zuletzt kommt ein Beispiel, welches zeigt, wie eine Datei eingelesen und verändert wieder abgespeichert werden kann.

Betrachten wir hierzu folgende Textdatei "sporarten.txt":

```
Schwimmen
Laufen
Radfahren
```

```java
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.Writer;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Paths;
import java.nio.file.StandardOpenOption;
import java.util.Scanner;

public class BeispielDateien {

	public static void main(String[] args) {
		System.out.println("Bisher erfasste Sportarten sind:");
		dateiEinlesenUndAusgeben();
		neueSportartErfassen();
		System.out.println("\nNun sind die Sporarten:");
		dateiEinlesenUndAusgeben();
	}

	private static void neueSportartErfassen() {
		Scanner scanner = new Scanner(System.in);
		System.out.println("\nBitte Sportart eingeben: ");
		String sport = scanner.nextLine();
		dateiAbspeichern(sport);
		scanner.close();
	}

	public static void dateiEinlesenUndAusgeben() {
		try (BufferedReader in = Files.newBufferedReader(Paths.get("sportarten.txt"), StandardCharsets.UTF_8)) {
			for (String line; (line = in.readLine()) != null;)
				System.out.println(line);
		} catch (IOException e) {
			e.printStackTrace();
		}
	}

	public static void dateiAbspeichern(String eingabe) {
		try (BufferedWriter out = Files.newBufferedWriter(Paths.get("sportarten.txt"), StandardCharsets.UTF_8, StandardOpenOption.APPEND)) {
			out.write(eingabe);
			out.write(System.lineSeparator());
		}

		catch (IOException e) {
			e.printStackTrace();
		}
	}
}
```

Zunächst wird die Datei sportarten.txt eingelesen und der Inhalt auf der Konsole ausgegeben. 
Der Nutzer wird gebeten, eine weitere Sportart auf der Konsole einzugebenn. 
Diese wird dann der Datei hinzugefügt. 
Zum Schluss wird erneut die Liste der Sportarten ausgegeben.

>Übung

Versuchen Sie die verschiedenen Beispiele in diesem Kapitel nachzuimplementieren. 

## Abschlussprojekt

Um sich auf die Projektaufgabe vorzubereiten, können Sie die Aufgabe UML-Shop in der [Aufgaben-Datenbank](https://speiser.hft-pages.io/programmieraufgaben/2024-ss-pro-1/) aus der Kategorie sonstige Übungen lösen.

>**Thema**

Es stehen im Sommersemester 2024 zwei Themen zur Auswahl:

1) **Tracker**: Entwickeln Sie einen Programm zum Tracken von etwas Ihrer Wahl, wie z.B. Sportstunden oder Lernstunden.


2) **Vereinsverwaltung**: Entwickeln Sie einen Programm zur Verwaltung von etwas Ihrer Wahl in Ihrem Verein wie z.B. Mitglieder oder Inventar.

>**Projektbeschreibung**

Erstellen Sie zunächst eine ca. zweiseitige Beschreibung des Programm, inkl. einem vorläufigen UML-Diagramm. 

Sie können sich hierfür an folgenden Fragen orientieren:

* Was wollen Sie konkret machen? Z.B. Meine täglichen Sportminuten tracken
* Welche Funktionalitäten muss bzw. soll das Programm haben? Z.B. Sportart auswählen, Minuten tracken, neue Sportart anlegen, Liste aller absoliverten Sportminuten ausgeben (z.B. sortiert nach Minuten, sortiert nach Sportarten)
* Wie sieht die grobe Architektur aus? Welche Pakete, Klassen, Hierarchien, Daten etc. gibt es?
* Wie sieht Ihre grobe Zeitplanung aus?

>**Bewertungskriterien**

1) Inhaltliche Anforderungen

* UML Diagramm
* Bedienbarkeit über Menü und Übersichtsansicht der Daten in Konsole
* Sortierbarkeit nach verschiedenen Kriterien
* Exception Handling bzw. defensive Programmierung
* Datei einlesen und ausgeben

2) Quantitative Anforderungen

* Funktionalitätsumfang des Programm (doppelte Gewichtung)

3) Qualitative Anforderungen

* Namensgebung und Lesbarkeit des Codes
* Strukturierung des Programms, inkl. Kapselung
* Funktionalität der Methoden bzw. Komplexität der Methoden

>**Abschlusspräsentation**

Vorstellung des Programms an Hand des UML-Diagramms und des Programmcodes.


## Generics 

Generics erlauben es, Klassen und Methoden so zu definieren, dass sie mit beliebigen Datentypen arbeiten können, ohne dabei auf die Typsicherheit zu verzichten. Anstatt mit allgemeinen Objekten zu arbeiten und später Typumwandlungen durchzuführen, können hier präzise Typen angegeben werden. Dadurch werden viele potenzielle Laufzeitfehler bereits zur Kompilierzeit abgefangen. Wir haben dies bereits bei Collections verwendet, ohne genau zu wissen, was wir da tun. 

Schauen Sie sich hierzu folgendes Einführungsbeispiel an: 


```java
List<String> meineListe = new ArrayList<>();
meineListe.add("Hallo Du");
String eintrag = meineListe.get(0);
```

In diesem Beispiel ist List<String> eine generische Liste, die nur String-Objekte enthält. Dies erhöht die Typsicherheit, da versehentliche Einfügungen von Objekten anderen Typs zur Kompilierzeit erkannt werden.

Die Vorteile von Generics sind also: 

* Typsicherheit: Fehler werden früher erkannt, da Typkonflikte bereits zur Kompilierzeit identifiziert werden.
* Wiederverwendbarkeit: Generische Klassen und Methoden können mit verschiedenen Datentypen verwendet werden, wodurch der Code flexibler und allgemeiner wird.
* Lesbarkeit: Der Code wird klarer und verständlicher, da keine expliziten Typumwandlungen erforderlich sind.


>**Verwendungsbeispiel Maps -- und ein Problem**

Das folgende Beispiel verdeutlicht nochmal das Problem, welches entsteht, wenn Collections nicht typisiert werden:

```java
import java.util.HashMap;
import java.util.Map;
import java.util.Set;

public class MapDemo {
    public static void main(String[] args)  {

        // Neues Telefonbuch
        Map telefonbuch = new HashMap();

        // Einträge anlegen: ein Paar aus Schlüssel und Wert
        telefonbuch.put("Doro", "071183673");
        telefonbuch.put("Anke", "017927343");   // Hier passt jeder Typ rein!
        telefonbuch.put("Chris","017292828");
        telefonbuch.put("Bert", "017198338");

        // Was ist Chris' Telefonnummer?
        System.out.println("Chris\' Nummer: "+ telefonbuch.get("Chris"));
        
        // Alle gespeicherten Werte ausgeben
        Set keyset = telefonbuch.keySet();
        for(Object name: keyset) {
            System.out.println(name+": "+telefonbuch.get(name));
        }

        // Aber: Es wurde String in die Map gesteckt,
        // (zunächst ein Object zurückbekommen)
        String nummerChris = (String) telefonbuch.get("Chris"); 
        // Das heißt: Der Entwickler muss den richtigen Typ wiederherstellen
    }
}
```
@LIA.java(MapDemo)



>**Hintergrund Typprüfung**

Schauen Sie sich folgendes Beispiel an und überlegen Sie sich, was hier wann passiert.

```java
public class KurzeDemo {
    public static void main(String[] args) {
        Object object = Integer.valueOf(42);
        String string = (String) object;
    }
}
```
@LIA.java(KurzeDemo)

Die Typprüfung geschieht zu zwei Zeitpunkten:

* Durch den Compiler (vor der Ausführung): Code ist ok
* Durch die JVM (während der Ausführung)

Das Ziel bei Generics ist, dass schon der Compiler mehr Informationen über die Typen erhalten soll.

Das heißt, wir wollen als Lösungsmöglichkeit nicht eine explizite Typumwandlung durch Casting (wie im Beispiel oben) nutzen, sondern Generics: Typ ist bei der Deklaration „generisch“ und erst beim Programmieren konkret. Dies hat viele Vorteile:

* Compiler kann korrekte Nutzung überprüfen
* Datenstrukturen und Algorithmen können vom Datentyp unabhängig, d.h. generisch sein (z.B. Sortieralgorithmen)
* Häufigster Einsatz: „Typsichere“ Container-Klassen, welche die Schnittstelle Collection implementieren

>**Verwendung von Generischen Typen**

Und nun das obige Beispiel mit der Nutzung von Generics:

```java
import java.util.HashMap;
import java.util.Map;
import java.util.Set;

public class MapDemo2 {
    static void main(String[] args)  {

        // Neues Telefonbuch vom generischen Typ Map<K,V>
    	// Konkret benötigte Typen (Typparameter) werden beim Anlegen eines neuen Objekts spezifiziert
    	Map<String, String> telefonbuch = new HashMap<String, String>(); 

    	
        // Einträge anlegen: ein Paar aus Schlüssel und Wert
        telefonbuch.put("Doro", "071183673");
        telefonbuch.put("Anke", "017927343");   
        telefonbuch.put("Chris","017292828");
        telefonbuch.put("Bert", "017198338");

        // Was ist Chris' Telefonnummer?
        System.out.println("Chris\' Nummer: "+ telefonbuch.get("Chris"));
        
        // Alle gespeicherten Werte ausgeben
        Set<String> keyset = telefonbuch.keySet();
        for(String name: keyset) {
            System.out.println(name+": "+telefonbuch.get(name));
        }

        // Automatisch bekommt man nun einen String
        String nummerChris = telefonbuch.get("Chris"); 
    }
}
```
@LIA.java(MapDemo2)

### Generische Klassen

Generische Klassen ermöglichen es, Klassen mit Typ-Parametern zu definieren, sodass sie mit verschiedenen Datentypen arbeiten können, ohne dabei die Typsicherheit zu verlieren. 
Dieses Konzept verbessert die Wiederverwendbarkeit und Flexibilität des Codes erheblich.

Eine generische Klasse wird mit einem oder mehreren Typ-Parametern definiert, die als Platzhalter für die tatsächlichen Datentypen fungieren. 
Diese Typ-Parameter werden in spitzen Klammern (<>) angegeben und können bei der Instanziierung der Klasse durch konkrete Typen ersetzt werden. 
Dadurch kann eine einzige Klassendefinition mit unterschiedlichen Datentypen verwendet werden.

Betrachten wir dies am Beispiel eines generischen Kartons. Dies ist ein Karton, in dem wir alles Mögliche verpacken können.

>**Beispiel Karton**

Typvariable steht zu Beginn der Klassendeklaration. Dadurch wird der Originaltyp Karton zum generischen Typ Karton<E>.
Typparameter wird im Code wie ein normaler Typ genutzt, aber es kann kein entsprechendes Objekt erzeugt werden.

Häufige Namen für Typvariablen sind:

- E: Entity
- T: Type
- K: Key

```java
public class Karton<E> { //Generischer Typ (Platzhalter für eine beliebige Klasse oder ein beliebiges Interface)
    private E inhalt; 
    public Karton(E inhalt) { //Parametertyp im Konstruktur
        this.inhalt = inhalt;
    }
    public E getInhalt() { //Rückgabetyp von Methoden
        return inhalt;
    }
    public void setInhalt(E inhalt) { //Parametertyp in Methoden
        this.inhalt = inhalt
    }
}
```

Unterschied:

- Ohne Generics: Erst zur Laufzeit bekannt, welchen Typ der „inhalt“ des Kartons hat (könnte eine ClassCastException auslösen)
- Mit Generics: Information bereits zur Compilezeit bekannt

>**Bezeichnungen**

| Begriff                    | Beispiel        |
|----------------------------|-----------------|
| Generischer Typ            | Set<T>          |
| Typvariable (formal type parameter)                | T               |
| Parametrisierter Typ       | Set<Long>       |
| Typparameter (actual type parameter)               | Long            |
| Originaltyp (raw type)     | Set             |

>**Mehr zur Typvariable**

- Typvariable T kann für fast alles stehen:


  * Klassen
  
  * Schnittstellen
  
  * Aufzählungen von Typen
  
  * Arrays von Typen

  * (aber keine primitiven Datentypen!)


- Typvariable T kann selbst wieder ein generischer Typ sein.

  * List<Map<Integer,String>> (deklariert als List<T> und Map<K,V>)

### Generische Schnittstellen

Nicht nur Klassen können generisch sein, sondern auch Interfaces. Wir haben dies bereits beim Interface Comparable gesehen.

>**Schnittstelle Comparable & Set**

```java
public interface Comparable<T> {
int compareTo(T o);
}

public interface Set<E> extends Collection<E> {
    boolean add(E e);
    int size();
    boolean isEmpty();
    boolean contains(Object o);
    Iterator<E> iterator();
    Object[] toArray();
    <T> T[] toArray(T[] a);
…
}
```

>**Benutzungsmuster**

Implementierung einer generischen Schnittstelle durch Angabe eines konkreten Typs:

```java 
public interface Comparable<T> {
    int compareTo(T o);
}

public final class Integer extends Number implements Comparable<Integer> { 
    //Hinweis: Primitive Datentypen können nicht als generischer Typ verwendet werden

    public int compareTo( Integer anotherInteger ) { ... }
    ...
}
```

### Erstellung und Nutzung

Für eine Menge von Klassen kann eine Schablone konstruiert werden, wenn mit Ausnahme der Typangaben alle Klassen textuell identisch sind

Durch Auslagerung der Typinformation in den Klassenkopf erhält man aus der Klasse eine Schablone:

```java
class Var<T> {
    private T obj = null;

    void setValue(T o) {
        obj = o;
    }

    T getValue() {
        return obj;
    }
}
// T ist eine Typvariable für den sog. formalen Typparameter. 
// I.d.R. nutzt man für die Platzhalter einzelne Großbuchstaben.
```
Instanziieren (Ersetzung der Typparameter durch bekannte Typen) erzeugt eine Schablonenklasse:

```java
Var<String> varString = new Var<String>();
Var<Student> varStudent = new Var<Student>();
```
Schablonenklassen können wie alle Klassen abgeleitet werden, so können auch „dauerhafte“ Instanziierungen mit vollständiger Typinformation erzeugt werden:

```java
class VarStudent extends Var<Student> {}
```

>**Achtung** Fußangeln:

- Die Information über den Typparameter wird nicht in die .class-Datei geschrieben, d.h. `instanceof` funktioniert nicht wie erwartet und `getClass()` liefert die Informationen über die Klassenschablone

- Es gibt **eine** .class-Datei, neue Instanziierungen des Typparameters erzeugen keine neuen Klassen!

>**Generische Schnittstellen**

- Schnittstellen `Comparable` und `Set`:

```java
public interface Comparable<T> {
    public int compareTo(T o);
}
```
- Arten der Benutzung


  - Auflösung des Typs oder

  - Weitergabe der Parametervariable

```java
public interface Set<E> extends Collection<E> {
    int size();
    boolean isEmpty();
    boolean contains(Object o);
    Iterator<E> iterator();
    Object[] toArray();
    <T> T[] toArray(T[] a);
    boolean add(E e);
    boolean remove(Object o);
    boolean containsAll(Collection<?> c);
    boolean addAll(Collection<? extends E> c);
    boolean retainAll(Collection<?> c);
    boolean removeAll(Collection<?> c);
    void clear();
    boolean equals(Object o);
    int hashCode();
}
```

>**Methodenschablone erstellen**

- Klassenschablonen, die nur `static`-Methoden definieren, heißen Methodenschablonen:

```java
class Utilities {
    static <T extends Comparable<T>> T min(T a, T b) {
        return a.compareTo(b) < 0 ? a : b;
    }

    static <T extends Comparable<T>> T max(T a, T b) {
        return a.compareTo(b) > 0 ? a : b;
    }
    //error: The method compareTo(T) is undefined for type T
}
```

>**Beispiel Methodenschablone**
```java
class ZufallBeispiel {
    public static <T> T zufall(T x, T y) {
        return Math.random() > 0.5 ? x : y;
    }
}
```

Aufruf der Methode (ohne Typangabe)_

```java
System.out.println(ZufallBeispiel.zufall(„Kino",„Sport"));
```
>**Methodenschablonen instanziieren**

- Eine Methodenschablone wird vom Compiler instanziiert, indem die Methode mit passenden Parametern gerufen wird.

- Der Compiler erkennt die Typvariable T anhand der Parameter, eine Methodenschablone darf daher T nicht nur im Rückgabewert haben.

>**Spezialisierte Klassenschablonen**

- Normale Klassenschablonen können mit allen von `java.lang.Object` abgeleiteten Typen instanziiert werden
- Manche Klassenschablonen benötigen jedoch spezielle Eigenschaften, z.B. Vergleichbarkeit mit `compareTo()`
- Bei der Definition einer Klassenschablone kann mit `extends` eine Untergrenze für den Typparameter angegeben werden:

```java
class SArray<T extends Comparable>
```

- Weitere Obertypen können mit `&` verkettet werden

### Generics in Collections
>**Collections (Wiederholung)**

- Eine Collection ist eine Klasse, deren Aufgabe die Speicherung von Elementen anderer Klassen ist
- Collections sind generisch formuliert – der Typ der zu speichernden Objekte wird bei der Initialisierung festgelegt
- Die Alternative wäre, Collections für den Typ Object zu schreiben – wegen Class Casts wäre der Code fehleranfällig!

- Collections unterscheiden sich in Bezug auf:


  - Die Art der Speicherung

  - Die Zugriffsmöglichkeiten und Geschwindigkeiten

- Es gibt keine für alle Zwecke ideale Collection, jede Klasse stellt einen Kompromiss in Bezug auf Zeit, Speicher-verbrauch, Zugriff und Sortierung dar.

>**Entwurfsprinzipien**
- **Schnittstellen** legen Operationsgruppen für die verschiedenen „Behältertypen“ fest (z.B. `List`, `Map`).
- **Konkrete Klassen** für „Behältertypen“ erben von der abstrakten Basisklasse (z.B. `ArrayList`, `TreeMap`).
- **Algorithmen** sind für den „Behältertyp“ verfügbar oder für die Utility-Klasse `Collections` (z.B. Suchen, Sortieren).
- (Für Entwickler der „Behältertypen“, d.h. weniger für Anwender: ) Die Vielzahl der abstrakten Basisklassen führt zu einer kleinen Zahl von als abstrakt deklarierten Grundoperation am „Behältertyp“.

>**Hierarchie der Collection Interfaces**
![Overview over collections](CollectionsMapsOverview.png)

Details:

- **Set**:		Menge im mathematischen Sinn
- **List**:		Indizierte Folge
- **Queue**:		Warteschlange (z.B. FIFO)
- **Deque**:		Schlange mit zwei Endpunkten
- **Map**:		Schlüssel-Wert Paare
- **SortedSet**:	Sortierte Menge
- **SortedMap**:	Paare sind nach Schlüssel sortiert


>**Schnittstelle Collection<E>**
<img src="generics-3.png" alt="ProgrammAusfuehren" width="80%">
<img src="generics-4.png" alt="ProgrammAusfuehren" width="80%">

>**Schnittstelle List<E>**

- Operationen: Indizierter Zugriff (get, set, add, remove), Sortieren, Suche, Iteratoren, Bereichsoperationen

- Implementierende Klassen:


  - ArrayList, LinkedList, Stack, ...
```java
public static void main(String[] args) {
    List<Integer> list = new ArrayList<>();
    list.addAll(Arrays.asList(8, 2, 1, 4, 7, 3));

    list.sort(null);

    for (Integer i : list) {
        System.out.println(i);
    }
}
```

>**Schnittstelle Queue<E>**

- Operationen: Hinzufügen, Entfernen, Prüfen
- Reihenfolge meistens FIFO
- Implementierung: `LinkedList`, `PriorityQueue`, ...

```java
public static void main(String[] args) throws InterruptedException {
    Queue<String> queue = new LinkedList<>();
    queue.add("David");
    queue.add("Leah");
    queue.add("Ariel");

    System.out.println("First in queue: " + queue.element());
    while (!queue.isEmpty()) {
        System.out.println(queue.remove());
        Thread.sleep(1000);
    }
}
```

>**Schnittstelle Map<E>**

- Schlüssel-Wert Paare („Mathematischer Funktionsbegriff“)
- Operationen: CRUD-Operationen, Iteratoren, ...
- Implementierende Klassen (analog zu Schnittstelle Set<E>): 
`HashMap`, `TreeMap`, `LinkedHashMap`, …

```java
public static void main(String[] args) {
    Map<Integer, Integer> m = new HashMap<>();

    int attempts = 6000;
    for (int a = 0; a < attempts; a++) {
        Integer i = (int) (Math.random() * 6 + 1);
        Integer count = m.get(i);
        m.put(i, (count == null) ? 1 : count + 1);
    }

    System.out.println("Entries: " + m.size());
    System.out.println(m);
}
```

### Übungen

## Funktionale Programmierung 1

`Funktionale Programmierung` ist ein Programmierparadigma, das sich auf die Verwendung von Funktionen konzentriert, um Probleme zu lösen. Es unterscheidet sich von anderen Paradigmen wie dem imperativen oder objektorientierten Programmieransatz durch die Art und Weise, wie Programme strukturiert und Zustände verwaltet werden.

Wichtige Konzepte der Funktionalen Programmierung:

- Keine Trennung zwischen Daten und Code:
   In der funktionalen Programmierung gibt es keine Unterscheidung zwischen Daten und Code. Funktionen können andere Programme und sogar sich selbst verarbeiten.

- Funktionen können in Variablen gespeichert werden:
   Funktionen können in Variablen gespeichert und als Parameter an andere Funktionen übergeben werden, was eine flexible Nutzung und Kombination ermöglicht.

- Keine Seiteneffekte:
   Funktionen beeinflussen keine äußeren Zustände und modifizieren keine übergebenen Referenzvariablen. Sie liefern immer denselben Rückgabewert für dieselben Eingabewerte, was zu einer deterministischen Ausführung führt.

Ein Beispiel für funktionale Programmierung in Java ist die Sortierung einer Liste: 

```java
import java.util.List;
import java.util.Arrays;

class funktProg {
    public static void main(String args[]) {
        List<Integer> numbers = Arrays.asList(3, 1, 4, 1, 5, 9);
        numbers.sort((a, b) -> a - b);
        System.out.println(numbers);
    }
}
```
@LIA.java(funktProg)

>**Programmierparadigmen**

- Verschiedene Paradigmen in der Programmierung:
  - imperativ
  - objektorientiert
  - deklarativ
  - funktional
- In manchen Programmiersprachen kommen mehrere Programmierparadigmen gleichzeitig zum Einsatz
- Java bei uns bisher: imperativ und objektorientiert
- Ab heute aber auch: deklarativ und funktional

### Funktionale Schnittstellen

>**Methoden in Schnittstellen**
Es gibt 3 Arten von Methodendeklarationen:

- Kein Schlüsselwort oder abstract: Methode muss in einer abgeleiteten Klasse überschrieben werden
- Schlüsselwort default: Methode braucht Implementierung, wird Objektmethode
- Schlüsselwort static: Methode braucht Implementation, wird Klassenmethode

>**Schnittstellen mit Default-Methoden**

Schnittstellen dürfen auch Methoden mit Rümpfen enthalten 
Im Unterschied zu abstrakten Klassen sind Felder in Schnittstellen verboten

```java
interface TestInterface {
    public void berechne (int a, int b); // abstract method
    default void melde() {               // default method
        System.out.println("Berechnung durchgefuehrt");
    }
}
```

>**Comparator**
Die Schnittstelle Comparator enthält 9 static und 7 default Methoden (hier ein Auszug):

```java
public interface Comparator<T> {

    abstract int compare(T a, T b);

    default Comparator<T> thenComparing 				
        (Comparator<? super T> other) {
        // nutzt compare
    }
}
```
Die default-Methode stützt sich auf compare ab – sobald dies implementiert ist, kann thenComparing genutzt werden

>**Funktionale Schnittstellen**

Idee: Funktionale Schnittstellen dienen zur Erstellung von „Service-Objekten“ mit nur einer relevanten Methode. 

Typische funktionale Schnittstellen sind:

- Comparator<T>, definiert int compare(T o1, T o2);
- Runnable, definiert void run();
- ActionListener, definiert actionPerformed(ActionEvent e);

--> Die Schnittstelle `Comparable` ist nicht sinnvoll funktional nutzbar, denn `compareTo(T)` nutzt in der Implementierung normalerweise „this“, also eine Objektvariable.

>**Anonyme innere Klassen und funktionale Schnittstellen**
Bisher haben Sie solche Service-Objekte durch anonyme innere Klassen implementiert

Dieses Vorgehen hat drei wesentliche Nachteile:

- In komplexen Applikationen z.B. mit Dutzenden von Buttons in einem Fenster müssen beim Laden des Fensters auch Dutzende anonyme innere Klassen geladen und instanziiert werden: Verzögerung für den Nutzer!
- Eine einmal geladene Klasse wird i.d.R. erst dann entladen, wenn die Applikation als Ganzes terminiert
- Der Code wird unübersichtlich

### Lambda-Ausdrücke

- Ähnlich wie anonyme innere Klassen, bei denen die Klasse keinen Namen hat (ggf. nur das Objekt), gibt es anonyme Methoden, auch Lambdas genannt
- Sie implementieren eine funktionale Schnittstelle, sind also selbst Objekte: eine Kernidee der Funktionalen Programmierung
- Diese Methoden können zur Implementation abstrakter Methoden in funktionalen Schnittstellen genutzt werden!

Ein Lambda-Ausdruck ist aufs Minimum reduziert:

```java
(a, b) -> a+b
```

- Parameterliste: Welche Argumente werden gebraucht? 
- Rumpf: Was soll mit den Argumenten passieren?
- (Syntax: verbunden durch den Pfeil-Operator)	

>**Beispiel 1: lexikographische Sortierung**

Ziel: Anpassung des Verhaltens von Algorithmen

Mittels anonymer innerer Klasse:

```java
Arrays.sort(zahlen, new Comparator<Integer>() {
    @Override
    public int compare(Integer o1, Integer o2) {
        return o1.toString().compareTo(o2.toString());
    }
});
```

Mittels Lambda-Ausdruck:

```java
Arrays.sort(zahlen, (Integer o1, Integer o2) ->
    o1.toString().compareTo(o2.toString()));
```

>**Beispiel 2: Umgekehrte Sortierung**
```java
    List<Integer> liste = new ArrayList<>();
    Collections.addAll(liste,  1 , 2 , 3 , 4);

    //mit anonymer Klasse
        liste.sort( new Comparator<Integer>() {
            @Override
            public int compare(Integer arg0, Integer arg1) {
            return arg1 - arg0;
        }
    });

    //mit Lambda Ausdruck (Datentyp der Parameter wird abgeleitet)
    liste.sort( (a,b) -> b-a);
```

>**Schnittstelle und Lambda**
Schloss und Schlüssel

Der Compiler prüft bzw. nutzt die Passung zwischen implementierter Schnittstelle und Lambda-Ausdruck:

```java
    public interface Comparator<T> {
        abstract int compare(T a, T b);
    }

    List<Integer> liste = new ArrayList<>();
    liste.sort( (a,b) -> b-a);

```

>**Beispiel mehrere Comparatoren**

```java
ArrayList<Person> alp = new ArrayList<>();
    alp.add(new Person("Hugo",42));
    alp.add(new Person("Hugo",37));
    alp.add(new Person("Christof", 38));
    
    // Definition von drei Comparatoren
    Comparator<Person> byAge = (p1, p2) ->{
        return Integer.compare(p1.getAge(),p2.getAge());  };
    
    Comparator<Person> byFirstName = (p1, p2) -> {
        return p1.getFirstName().compareTo(p2.getFirstName());};
    
    Comparator<Person> byAgeThenFirstName =
             byAge.thenComparing(byFirstName);
    
    // dann Ausgabe in Wunschsortierung (freie Wahl des Comparators)	
```

### Syntax von Lambda-Ausrücken

>**Typinferenz**

(Parameterleiste) -> Rumpf

Parameterleiste:

- Parameter mit Typangabe: Der Compiler nutzt den Typ
- Parameter ohne Typangabe: Der Compiler ermittelt den Typ

Rumpf und Rückgabetyp:

- Ein Ausdruck (ohne { }-Klammern), in diesem Fall liefert die Methode den Wert des Ausdrucks zurück
- Ein Block (mit { }-Klammern) mit `return`, in diesem Fall liefert die Methode  ggf. das Argument von `return` zurück
- Ein Block (mit { }-Klammern) ohne `return`, in diesem Fall ist die Methode `void`

>**Beispiele für anonyme Methoden: Ausdruck**

```
Ohne Parameter: 	         () -> System.in.read()

Mit typlosem Parameter:    (r) -> r.run() 

Mit getyptem Parameter:    (Callable c, String a)->c.apply(a)
```

Ein Ausdruck (ohne { }-Klammern) ist nur möglich, wenn keine lokalen Variablen oder Kontrollstrukturen vorkommen

>**Beispiele für anonyme Methoden: Block**

```
Ohne return, ohne Parameter:  () -> {Thread.sleep(100);}
Ohne return, mit Parameter:	 (Thread t) -> {t.start(); t.join();}
Mit return, mit Parameter: 	(int a) -> { int s = 0;
 					                               while(--a>0) {s+=a}; 	
                                		     return s;}
```
Ein Block (mit { }-Klammern) ist immer möglich!

### Methodenreferenzen
Lambdas definieren Funktionen, über die wir das Programm parametrisieren können

Was aber, wenn eine passende Methode im Code schon vorhanden ist, also kein neues Lambda notwendig?

Lösung sind Methodenreferenzen. Aus:

```java
Arrays.sort(array, (s1,s2) -> myClass.myCompare(s1,s2));
```
wird dann mit der Methodenreferenz noch kürzer:

```java
Arrays.sort(array, myClass::myCompare);
```

>**Methodenreferenzen: Nutzen**

- Methodenreferenzen (Klassenname::Methodenname) dienen zur besonders schnellen Initialisierung funktionaler Schnittstellen mit benannten Methoden
- Auch sie können in Variablen gespeichert werden:	

```java
Runnable runner = System.out::println;
```

- Die linke und rechte Seite der Zuweisung passen:


  - Die Methode `run` der Schnittstelle `Runnable` hat keine Parameter und den Rückgabetyp `void`
  - Ebenso gibt es eine Methode `println` in `System.out` ohne Parameter und mit Rückgabetyp `void`

>**Interface Function**

**Verwendung**: 

```java
Function<Integer,Integer> add1 = x -> x + 1; 
```

![](FunktionaleProgrammierung-1.png)

Wichtigste Methode:

- R apply (T t)
- Applies this function to the given argument

>**Regeln für Methodenreferenzen**
- Rückgabewert der ausgewählten Methode muss zuweisungskompatibel mit Schnittstellenmethode sein:


  - Rückgabewert void, Methodenreferenz void: ok
  - Rückgabewert int, Methodenreferenz String oder void: nicht ok
- Die Parameterliste muss passen:


  - Klassenmethode: alle Parameter passen exakt  ```Function<Object,String> stringMaker=String::valueOf;```
  - Instanzmethode eines konkreten Objekts: alle Parameter passen: ```String meinString = "Hallo"; Function<String, String> fConcat = meinString::concat;```
  - Instanzmethode ohne konkretes Objekt: this wird erster Parameter, Argumente der Methode werden weitere Parameter ```Comparator<String> stringCompare= String::compareToIgnoreCase;```

### Übungen

## Funktionale Programmierung 2

>**Lambdas: Methoden als Objekte**

- Lambda-Ausdrücke erlauben, Methoden wie Objekte zu behandeln: Der Kern der funktionalen Programmierung
- Dadurch lassen sich einfache Methoden in knapper funktionaler Schreibweise zu komplexen Methoden kombinieren

>**Streams: Datenverarbeitung am Fließband**

Die folgende SQL-Abfrage berechnet das mittlere Gehalt der erwachsenen Angestellten einer Firma nach Alter sortiert und gruppiert, wobei nur Gruppen von mindestens 10 Personen gewertet werden:

```java
SELECT AVG(SALARY) FROM EMPLYEE ORDER BY AGE
    WHERE AGE >= 18 GROUP BY AGE HAVING COUNT(AGE) >= 10
```

Schätzen Sie ab, wie hoch der Aufwand zur Berechnung dieses Ergebnisses mit einer Programmierung von Schleifen wäre?

Mit Streams lässt sich dieses Problem in nur wenigen Zeilen Code lösen: auch deklarativer Ansatz wie bei SQL!

>**Streams: Folge von Operationen auf Daten**

Pipeline: (Quelle . Verarbeitung . Verarbeitung ... Zusammenfassung)

Zahlreiche Datenquellen (Collections, Dateien, Supplier ...)

- Parallele Verarbeitung möglich (Nutzung aller Cores)


  - Umformung
  - Filterung
  - Sortierung

**Einfaches Beispiel:**

Gegeben ist eine Liste von Objekten der Klasse `Author` mit den Feldern `fname, vname, age und revenue`

Gesucht sind die beiden umsatzstärksten mindestens 50 Jahre alten Autoren:

```java
authors.stream().
        filter((x)->x.age>=50).
        sorted((x, y)->y.revenue.compareTo(x.revenue)).
        limit(2).
        forEach((x)->System.out.printf("%s %s%n", x.vname, x.fname));
```

- Der Aufruf von filter löscht alle Autoren < 50 Jahren
- Der Aufruf von sorted sortiert absteigend
- Der Aufruf von limit löscht alles ab dem 3. Element
- Der Aufruf von forEach druckt alle verbleibenden Elemente mit der Methode `printf`

>**Eine Warnung**

Achtung: Die im Folgenden behandelten Klassen und Methoden finden sich im Paket java.util
manchmal auch „Java 8 Streams“ genannt

Die anderen behandelten Stream-Klassen z.B. InputStream, OutputStream, etc. befinden sich im Paket java.io

Beide Klassen verarbeiten Ströme von Daten, aber:

- Die Klassen aus java.io verarbeiten elementare Typen
- Die Klassen aus java.util verarbeiten Objekte



### Aufbau von Streams

>**Grundideen hinter Streams**

- Pipelines von Operationen, die einen eingehenden Stream von Objekten verarbeiten
- Oft Lambda-Ausdruck als Parameter: Wie soll sortiert werden, welches Filterkriterium angewandt?


  - basiert auf funktionaler Schnittstelle
- Meistens gilt im Sinne der funktionalen Programmierung: Die Quelldaten des Streams bleiben unverändert, ein Verarbeitungsschritt erstellt jeweils einen neuen Stream mit den Ergebnissen. –> Verarbeitungsmethoden  ohne internen Zustand
- Streams können später nicht mehr wiederverwendet werden. Sobald ein Stream zu Ende verarbeitet wurde, wird er geschlossen!

>**Stream-Pipelines**
- Am Anfang steht immer eine Datenquelle


  - Collections, Arrays
  - Generatoren (z.B. Datenbankabfragen, eigene Methoden)
- In der Mitte steht die Verarbeitung (intermediäre Operationen)


  - Filtern
  - Umformen
  - Begrenzen

- Am Ende steht eine Datensenke (terminale Operation)


  - Minimum / Maximum / Durchschnitt / Anzahl
  - Ausgabe in Collection oder Array / Reduktion / Auswertung



### Streams-Datenquellen

Stream aus einem Array:

```java
int[] data= {1,2,3};
Arrays.stream(data).forEach(System.out::println);
```

Stream aus einer Collection mittels .streams():

```java
List<String> liste = new LinkedList<String>();
liste.stream().forEach(System.out::println);
```

Auch aus Aufzählung möglich: Stream.of()

```java
Stream.of(1,2,3).forEach(n -> System.out.println(n));
```

Vorsicht bei Arrays/Collections (mit primitiven Datentypen):

```java
Stream.of(data).forEach(n -> System.out.println(n));
// liefert: [Z@4564caa5
```

Streams können aber auch (potentiell) unendlich lang sein: 

- `Stream.generate(Supplier<T> s)`: Stream mit Elementen, die  durch wiederholten Aufruf von `s.get()` erzeugt werden
- `Stream.iterate(T t, UnaryOperator<T> f)`: Stream aus `t, f.apply(t)`, `f.apply(f.apply(t))`, ...

In diesen Fällen muss der Stream begrenzt werden, sonst endet die Berechnung nicht

**Beispiel:** Erzeugung eines Streams mit Iterate:

```java
// Hilfsmethode zum schönen Ausdrucken	
Consumer print = x->System.out.print(x+" ");
        
Stream.iterate(1,x->x+1)
    .limit(10).forEach(print);
// Ausgabe: 1 2 3 4 5 6 7 8 9 10		
        
Stream.iterate("*", x-> x+"*")
    .limit(5).forEach(print);
// Ausgabe: * ** *** **** ***** 
```

**Beispiel:** Zusammengesetzter Stream

Zwei Streams lassen sich durch die statische Methode ```Stream.concat(Stream<T> a, Stream<T> b)``` 
verketten:

```java
 Stream<Integer> stream1 = Stream.of(1, 3, 5);  
 Stream<Integer> stream2 = Stream.of(2, 4, 6);
 Stream<Integer> res = Stream.concat(stream1, stream2);
```

### Intermediäre Operationen

Intermediäre Operationen „aus der Mitte der Pipeline“ 

Diese fortführenden Operationen sind „faul“ (engl. lazy), sie werden erst bei Bedarf ausgeführt, wenn die terminale Operation dies verlangt

Kennzeichnend für die Stream-Verarbeitung ist die Tatsache, dass jede Methode einen Stream in einen neuen Stream wandelt

>**Beispiele aus java.util.Stream:**

- limit(long s): Stream mit max. s Elementen
- filter(Predicate<T> p): Stream mit den Elementen, für die p.test(..) true ist
- sorted(Comparator<T> s): Sortierter Stream 
- distinct(): Stream ohne Doubletten

Mit map(Function<T, R> m) wird ein Stream<T> in einen Stream<R> konvertiert, indem für alle Elemente der Eingabe m.apply() aufgerufen wird:

```java
     liste.stream()
                 .map(String::toUpperCase)	
                 .forEach(System.out::println);
```

Umwandlung zwischen Objekt-Streams und Streams primitiver Typen möglich mit: `mapToInt(), mapToLong(), mapToDouble() und mapToObj():`

```java
Stream.of(1.0, 2.0, 3.0, 4.0, 5.0)
             .mapToInt(Double::intValue)	
             .mapToObj(x -> "Wert: " + x)
             .forEach(System.out::println);
```


>**Beispiele: flatMap**
Bsp. 1: Ein 2-dimensionales String-Array in einen Stream konvertieren: {{1,2},{3,4},{5,6}} über flatMap zu {1,2,3,4,5,6}

```java
String[][] listOfNamesLists = foo();
Stream<String> nameStream = 
    Stream.of(listOfNameLists).
    flatMap((x)->Stream.of(x));
```

Bsp. 2: Zu einem Wert jeweils zwei weitere hinzufügen:

```java
Stream.of( 1 , 5 , 19, 7)
.flatMap( x -> Stream.of(x,x+1,x+2))
.forEach(print);

// Ausgabe: 1 2 3 5 6 7 19 20 21 7 8 9 
```

### Streams-Datensenken

- Durch einen Java Stream Ausdruck (```z.B. IntStream.of(1, 2, 3).map(x -> 2 * x).filter(x -> x > 1).sum();```) wird eine Verkettung der Verarbeitungsstufen erstellt, indem jede „mittlere“ Stream Methode (z.B. „map“, „filter“ etc.) ein neues Stream Objekt erzeugt und verkettet.
- Am Ende eines Stream-Ausdrucks steht immer eine Datensenke (terminale Operation), deren Rückgabewert in der Regel **kein Stream** ist.
- Erst durch diese Datensenke wird die Verarbeitung getriggert: Die Quellelemente werden nacheinander durch die Kette von Operationen geschickt, dabei verarbeitet und in der Datensenke „eingesammelt“ (ggf. verteilt auf mehrere parallele „Arbeiter“)

>**Arten von Datensenken**

Es gibt Datensenken:

- Ohne Rückgabewerte, z.B. forEach, forEachOrdered
- Mit elementaren Rückgabewerten, z.B. count, sum
- Mit nutzerdefinierten Rückgabewerten, z.B. collect, reduce

>**Datensenken ohne oder mit primitiven Rückgabewerten**

Die Methode forEach(Consumer<T> a) ruft für alle Elemente des Streams die Methode a.accept() auf

- Consumer<T> ist eine funktionale Schnittstelle. Um damit etwas Sinnvolles machen zu können, muss ein Seiteneffekt (drucken, in Datenbank schreiben, ...) existieren
- Beispiel: ```forEach(System.out::println)```;

Eine Prüfung ob alle (einzelne, keine) Elemente im Stream eine bestimmte Eigenschaft haben, erfolgt mit 
`allMatch(Predicate<T> p)`, `anyMatch(Predicate<T> p)` sowie `noneMatch(Predicate<T> p)`

```    
-> Rückgabe: true/false
```

- Die Methode count() zählt die Elemente im Stream und liefert die Anzahl zurück
- Die Methoden toArray() und toArray(IntFunction<T[]> f) liefern die Elemente im Stream als Object[] bzw. T[] zurück, f ist normalerweise der Ausdruck (n)->new T[n] 

min(Comparator<T> c) und max(Comparator<T> c) finden das kleinste bzw. größte Element im Stream (bzgl. c) 
auch möglich: average() und sum()
Beispiel:

```java
Stream.of("1", "2", "3", "4")
            .mapToInt(Integer::parseInt)
            .max()
            .ifPresent(System.out::println);  // -> 4
```

ifPresent() kommt aus der Klasse Optional<T>

>**Kurzer Exkurs: Optional<T>**

Die Klasse Optional funktioniert wie ein Container, der einen Wert enthalten kann oder nicht
 
- Beispiel: Optional<String> x = Optional.of(“Text“);

Abfragen erfolgen über:

- get() liefert den Wert oder eine NoSuchElementException
- isPresent() prüft, ob ein Wert vorhanden ist
- orElse(T o) liefert o zurück, falls kein Wert vorhanden ist

Grund: bisher häufige und fehleranfällige Überprüfung notwendig, ob ein Wert null sein kann

- vereinfacht den Umgang mit null‘s und macht den Code kürzer, kontrollierter Umgang mit null‘s wird notwendig
- Dafür kann null als Element verarbeitet werden

>**Datensenken mit nutzerdefiniertem Typ**

Die wichtigsten Datensenken sind:

- findAny() findet irgendein Element im Stream
- findFirst() findet das erste Element im Stream

Beispiel: erstes Element eines Streams holen:	

```java		
    Stream.of("Kurs1", "Kurs2", "Kurs3")
            .findFirst()
            .ifPresent(System.out::println); // -> Kurs1
```

Weitere wichtige Datensenken sind:

- reduce(BinaryOperator<T> a) reduziert alle Elemente im Stream durch wiederholte Anwendung von a.apply() auf (maximal) einen Wert


  - zu reduce gibt es auch überladene Methoden, die eine Parallelverarbeitung erlauben

Beispiel für reduce(BinaryOperator<T> a):

```java
    personenListe.stream()
            .reduce((p1, p2) -> p1.age > p2.age ? p1 : p2)
    .ifPresent(System.out::println);
```
Beispiel für reduce(T identity, BinaryOperator<T> a):

```java
    int result = Stream.of(5, 1, 6, 3)
            .reduce(17, (i1, i2) -> i1 > i2 ? i1 : i2);
```

Kollektoren sammeln z.B. die Stream-Elemente in eine Collection

- toList() liefert als Ergebnis eine Liste mit allen Elementen
- toSet() liefert als Ergebnis eine Menge mit allen Elementen
- toMap(Function<T, K> k, Function <T, U> v) liefert eine Map<K, U> deren Elemente vom Typ K bzw. U durch die Funktionen k bzw. v aus Elementen vom Typ T erzeugt sind

>**Collect-Beispiele**

```java
// Erstellen eines Streams von Strings und Sammeln in einem Set
Stream<String> s = Stream.of("a", "b", "c");
Set<String> names = s.collect(Collectors.toSet());
// Ergebnis: [a, b, c]

List<Person> persons = new ArrayList<>();
persons.add(new Person("1", "Isaac", "Newton"));
persons.add(new Person("2", "Albert", "Einstein"));
persons.add(new Person("3", "Nicola", "Tesla"));

Map<String, Person> personMap = persons
    .stream()
    .collect(Collectors.toMap(Person::getId, p -> p));

System.out.println(personMap.get("2"));
// Ausgabe: [2, Albert, Einstein]
```

### Optimierung
>**Reihenfolge der Operationen**

Beim Aufbau der Pipeline sollte man die Reihenfolge der Operationen optimieren.
teils erhebliche Performance-Verbesserungen möglich!

Beispiel:

```java
Stream.of(listeMitNamen)
    .sorted((n1, n2) -> { return n1.compareTo(n2); })
    .map(n -> { return n.toUpperCase(); })
    .filter(n -> { return n.startsWith("A"); })
    .forEach(n -> System.out.println(n));
```
Hier sollte besser zuerst filter vor sorted stehen

>**Parallele Verarbeitung**

- Neben `stream()` kann auch `parallelStream()` für parallele Streams verwendet werden


  - Vielleicht das wichtigste Feature der funktionalen Programmierung !!!


```java
Arrays.asList("Name1", "Name2", "Name3", ...)
    .parallelStream()
    .filter(s -> { ... })
    .sorted((s1, s2) -> { ... })
    .forEachOrdered(s -> { ... });
```
Konvertierung zwischen parallelen und sequentiellen  Streams möglich, Operationen teils „intelligent“, z.B. beim Sortieren über `Arrays.parallelSort()`

>**Parallele Verarbeitung: Primzahlen zählen**

```java
        System.out.println("Primz Start ... ");
        Instant start = Instant.now();
        System.out.println(IntStream.range(1, (int) 5E6) 
            .parallel()
            .filter( // Prüfen ob Primzahl (Stream im Filter ...) 
                x -> IntStream.range(2, (int) (Math.sqrt(x)+1))
                .filter(teiler -> (x % teiler) == 0)  // Teiler gefunden
                .limit(1)  // Ein Teiler reicht
                .count() == 0) // Nur die Werte ohne Teiler zählen
            .count()
        );
        System.out.println(Duration.between(start, Instant.now()));
```

Parallel:
Primz Start ... 
348514
PT1.616196S

Nicht parallel:
Primz Start ... 
348514
PT5.210741S

### Übungen

## Swing

>**Evolution des User Interface ...**

![](swing-1.png)

>**Vergleich: GUI- vs. CUI/CLI-Programme**

| Merkmal               | GUI (Graphical User Interface)                 | CUI/CLI (Character User Interface / Command Line Interface) |
|-----------------------|------------------------------------------------|-------------------------------------------------------------|
| **Steuerungsprinzip** | Ereignissteuerung                              | Flusssteuerung                                              |
| **Eingabemethoden**   | - Tastendruck<br>- Mausklick<br>- Zeitablauf   | - Tastendrücke über die Kommandozeile                       |
| **Reaktionsmechanismen** | - Reaktion auf verschiedene Ereignisse (z.B. Tastendruck, Mausklick)<br>- Vervollständigung möglich | - Reaktion nur bei Eingabetaste ("Enter")                   |
| **Feldsteuerung**     | - Freie Wahl der Felder durch Mausklick / Tab  | - Feldreihenfolge bei Eingabe ist fest                      |
| **Sichtbarkeit der Eingaben** | - Einzelne Tastendrücke sind erkennbar und programmatisch nutzbar | - Einzelne Tastendrücke für das Programm unsichtbar         |
| **Programmierung**    | - Ideal mit objektorientierter Programmierung (OOP) umsetzbar | - Auch ohne OOP machbar                                     |

>**Grundsätzliches Vorgehen**
1. Ein Fenster braucht einen Rahmen: Neue Klasse erstellen, z.B. von JFrame ableiten
2. Ein Fenster braucht eine Scheibe: Ein JPanel als content pane
3. Auf die Scheibe kommt ein LayoutManager, der die Anordnung der Komponenten kontrolliert
4. Dann folgen die einzelnen Komponenten
5. Schließlich implementieren Sie für die Komponenten Reaktionen auf bestimmte Nutzeraktionen

### Layout mit Swing

>**Layout-Manager**
- „Write once“ erfordert eine Anpassung der Größen der Fensterelemente
- Größenanpassung erfolgt automatisch durch die Layout-Manager anhand der „natürlichen“ Größe
- Kenntnis der Dialog-Manager ist wichtig für die Konstruktion guter Dialoge

  ![](swing-2.png)

  ![](swing-3.png)

  ![](swing-4.png)

>**Border-Layout**
- Verwendung in Dialogen und in einfachen allgemeinen Programmen
- Beinhaltet 5 Zonen, deren Orientierung durch eine BorderLayout-Konstante definiert wird:


  - Oben (PAGE_START)
  - Mitte (CENTER)
  - Unten (PAGE_END)
  - Rechts (LINE_END)
  - Links (LINE_START)
  ![](Swing-5.png)
- Die PAGE_XX- und LINE_XX-Konstanten berücksichtigen die Schreibrichtung

>**Flow-Layout**

- Verwendet zur Aufreihung vieler Elemente
- Enthaltene Komponenten werden wie Text umgebrochen:
  ![](Swing-6.png)

  ![](Swing-7.png)

- Sinnvoll vor allem dort, wo die mangelnde Breite des Containers durch Höhe ersetzt werden kann
- Die Objekte können von links nach rechts oder von rechts nach links angeordnet werden
- Die Objekte können mit einem horizontalen oder vertikalen Rand umgeben werden

>**Box-Layout**
- Verwendet zur horizontalen oder vertikalen Anordnung von Komponenten in einer Reihe
  ![](Swing-8.png)

- Menüs nutzen dieses Layout, Basis-klasse von `DefaultMenuLayout`, 
- Die einzelnen Elemente werden nicht umgebrochen oder in der Größe verändert.
- „Überzählige“ Elemente werden am rechten bzw. linken Ende herausgeschoben
- Nicht zu verwechseln mit Box-Objekten, die Abstände zwischen Komponenten erzeugen

>**Card- und TabbedPane-Layout**
- Das Card-Layout ist optimal für die Gestaltung von Assistenten-Dialogen geeignet
- Die Selektion in der oberen Combobox bestimmt die sichtbare Seite unten
  ![](Swing-9.png)

- Das TabbedPane-Layout wird für Dialoge mit  mehreren „Seiten“ durch das JTabbedPane-Element genutzt.
- Das JTabbedPane-Element ist viel einfacher nutzbar
  ![](Swing-10.png)

>**Grid-Layout**
- Das Grid-Layout ordnet alle Elemente in einem 2-dimensionalen Gitter an und vergrößert die Komponenten falls notwendig
  ![](Swing-11.png)

- Wahlweise lassen sich die Zeilen- oder die Spaltenzahl definieren
- Zwischen den Komponenten können Zwischenräume eingefügt werden
- Das Grid-Layout ist für viele Anwendungen zu unflexibel, das GridBag-Layout wird bevorzugt

>**GridBag-Layout**
- Entspricht einem GridLayout, bei dem die Elemente mehrere Zellen umfassen können
- Die Zellen können gewichtet werden, um den Zuwachs an Platz zu verteilen.
  ![](Swing-12.png)

- Die Zellen können mit einem Abstand umgeben werden, um das Layout aufzulockern
- Wenn der Inhalt „zu klein“ ist, kann die Zelle um einen bestimmten inneren Abstand vergrößert werden

>**Absolute-, Spring- und Group-Layout**
- Das Absolute-Layout positioniert alle Elemente (wie der Name sagt) an einer absoluten Position. Es sollte nur für Experimente verwendet werden
- Das Spring-Layout positioniert die Elemente, als ob diese durch Federn verbunden wären
- Das Group-Layout positioniert die Elemente so, als wären sie durch Panel verbunden, ohne dass jedoch Panel vorhanden sind
- Spring- und Group-Layout werden für das Werkzeug-basierte Layout (Matisse) benutzt.
  ![](Swing-13.png)

>**Manuelles Dialog-Design**
- Um einen Dialog zu entwerfen, müssen die Elemente entsprechend ihrer Gruppierung in eine Baumstruktur umgewandelt werden.
- Durch verschachtelte Anordnung von Panel-Objekten können auch Dialoge mit speziellen Layouts entworfen werden
  ![](Swing-14.png)

- Bei diesem Taschenrechner, sind in der oberen Reihe die Tasten um 33% breiter 
  ![](Swing-15.png)

- Die Tasten in der oberen Reihe gehören zu einem Panel über 3 Zellen mit GridLayout im „inneren“ Panel

### Dialogelemente

Swing stellt Ihnen alle Dialogelemente zur Verfügung, die Sie aus Software und Webformularen kennen

- Textfelder (verschiedene Sorten)
- Buttons
- Auswahlbuttons (Radio-Button)
- Dropdown-Menüs (ComboBox)
- Checkbox zum Anhaken
- ...

>**JRadioButton und JCheckBox**

- JRadioButton imitiert die in Radio- oder Fernsehgeräten üblichen Wahlschalter:


  - Eine kleine Zahl von Knöpfen
  - Druck auf einen Knopf entriegelt alle anderen Knöpfe
  - Für den Entriegelungseffekt müssen JRadioButton-Objekte einer ButtonGroup zugeordnet sein

  ![](swing-16.png)

- JCheckBox imitiert eine binäre Ankreuzoption auf Formularen:

     ![](swing-17.png)

>**JButton und Aktionen**

- Die Klasse JButton legt klickbare Buttons an (z.B. OK-Button, Weiter-Button, ...)
- Wird der Button geklickt, muss diese Tatsache registriert und weitergegeben werden
- Dann kann auf den Button-Klick reagiert werden

>**Aktionen und Listener**

- Ein Klick auf einen Button erzeugt ein ActionEvent
- Andere Aktionen (z.B. Tippen, Maus bewegen) erzeugen ebenfalls Events
- Um auf Events zu reagieren, hängt man einen Listener an das Objekt, das Events erzeugen kann
- Wenn der Listener ein Event gemeldet bekommt, führt er seinen Code aus

ActionListener: Codebeispiel

```java
ActionListener al = new ActionListener() {
	public void actionPerformed(ActionEvent e) {
    		button1.setIcon(icon2);
    }
};

button1.addActionListener(al);
```
oder

```java
button1.addActionListener(e–>button1.setIcon(icon2));
```

>**Listener**
- Listener können, wie im Beispiel, als anonyme Klasse/Lambda-Ausdruck implementiert werden
- Alternativ kann man einen Listener schreiben, den man mehrfach in ähnlichen Situationen verwendet
- Dazu erstellt man eine neue Klasse, die das entsprechende Listener-Interface implementiert (z.B. `ActionListener`)
- An das Event-generierende Objekt wird dann eine neue Instanz dieser Listener-Klasse gehängt

>**Geteilte Arbeit: Model/View**

Viele Swing-Dialogelemente teilen die Arbeit auf zwei Ebenen auf:

- Die View-Ebene ist für die Darstellung zuständig
- Die Model-Ebene verantwortet die Fachfunktion

Beispiel JFormattedTextField für eine Datumseingabe:

- Die Anzeige stellt das Datum als 1.10.2012 dar
- Das Modell prüft, ob ein eingegebener Wert erlaubt ist und wechselt ggf. zum vorherigen Wert zurück

**Vorteile von Model/View**

- Eine Trennung von Modell und Darstellung bietet die Möglichkeit,


  - dieselbe Information auf verschiedene Arten zu  präsentieren, z.B. Zahlen binär, oktal oder dezimal,
  - oder in der Darstellung von den eigentlichen Daten abzuweichen, z.B. durch automatische Umbrüche
  - sowie Daten zu verwalten, die in der eigentlichen Information fehlen, z.B. die aktuelle Schreibmarke
- Bei den Textkomponenten heißen die Modelle XXDocument, sonst XXModel

>**JTextField, JTextArea & JTextPane**
Diese Klassen erben von JTextComponent:

- TextField stellt unformatierte einzeilige Texte dar
- JTextArea stellt unformatierte mehrzeilige Texte dar
- JTextPane stellt formatierte mehrzeilige Texte dar

Das zugehörige Modell erbt von Document:

- PlainDocument für unformatierte Texte
- DefaultStyledDocument für formatierte Texte

Alle Änderungen am Inhalt des Textes werden über das Document kommuniziert

>**Model/View-Aufgabenteilung**

Alle Methoden zur Ein-/Ausgabe werden für die jeweiligen Views aufgerufen:

- Setzen und Abfragen der Schreibmarke
- Setzen und Abfragen der Selektion
- Abfangen von Mausklicks und Tastatureingaben

Methoden, die den Dokumentinhalt betreffen, werden für das Modell aufgerufen:

- Setzen und Abfragen des Inhalts
- Setzen und Abfragen der Formatierung

>**Textein- und -ausgaben**

Für die Textausgabe gibt es in Swing JLabel

- Hat kein Modell, mehrzeilige Ausgaben (oder z.B. Farbe) durch HTML-Steuerzeichen (<br>)
- Alternativ auch mit einem Bild (Icon)
- Kann einer Komponente zur Navigation über Mnemonics zugeordnet werden

Für einzeilige Texteingaben existieren drei verschiedene GUI-Objekte:

- JTextField für „normale“ Eingaben
- JPasswordField für verdeckte Eingaben
- JFormattedTextField für formatierte Eingaben

>**Benutzung spezieller Texteingaben**

- JPasswordField sollte mit char[] getPassword() ausgelesen werden, da getText() einen String liefert, der u.U. sehr lange im Speicher steht
- JFormattedTextField kann für die Eingabe von formatierten Texten z.B. Mailadressen von HFT-Studierenden genutzt werden:

```java
MaskFormatter mf = new MaskFormatter("##LLLL#LLL@hft-...");
              mf.setPlaceholderChar('_');
              JFormattedTextField ftf = new JFormattedTextField(mf);
```

>**Formatierung mit MaskFormatter**
- Alle nicht zur Formatierung benutzten Zeichen werden in den Text übernommen
- Die Formatierungszeichen sind wie folgt:


  - `#`: Ziffer
  - `'`: Maskiert ein Formatierungszeichen
  - `U`: Großbuchstaben
  - `L`: Kleinbuchstaben
  - `A`: Buchstaben oder Ziffern
  - `?`: Beliebige Buchstaben
  - `*`: Beliebige Zeichen
  - `H`: Hex-Ziffern
