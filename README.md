# WebMatic
WebMatic ist eine browserbasierte Benutzeroberfl�che f�r HomeMatic. Die Elemente sind f�r eine Bedienung mit mobilen Endger�ten optimiert. WebMatic l�uft komplett auf der CCU.

## Haftungsausschluss
Der Autor dieser Software �bernimmt keinerlei Verantwortung f�r die Funktionsweise der Software und keinerlei Haftung f�r Sch�den, die aus der Benutzung dieser Software resultieren.


## Changelog
1.4
* Codereview
* Ger�te die als nicht sichtbar deklariert wurde, werden nicht mehr angezeigt
* Neue Ansicht "get.html" akzeptiert eine ID und zeigt nur den gew�nschten Raum oder Gewerk an "get.html?id=12345"
* Eingabe von HTML-Code in Textvariablen m�glich, wenn als Einheit 'html' eingegeben wird. JavaScript wird auch ausgef�hrt.
* Wenn eine Textvariable zu lang ist, erscheint eine Textarea anstatt eines Input-Feldes
* Startparameter werden in der Datei init.json eingegeben
* Nur ausf�hrbare Programme anzeigen
* Verschiedene Styles ausw�hlbar
* Installtionsroutine angepasst (Userfreundlichkeit)

1.1
* Anzeige f�r Ger�t: ALARMACTUATOR.
* Anzeige f�r Ger�t: SENSOR.
* Anzeige f�r Ger�t: TILT_SENSOR.
* Anzeige f�r Ger�te: RS485 und I/O-Module.
* Mit Ger�ten verkn�pfte Variablen auch beim Ger�t anzeigen.
* Falscher Wert bei Variablenanzeige im ReadOnly Mode f�r bool behoben (war umgekehrt).
* Update nach 60 Sekunden selber regeln: Wenn man iPad aufklappt kommt dann sofort ein Update und nicht erst nach 1 Minute, da Safari im iOS den Timer nach dem Aufwachen neu startet.
* Update Probleme mit IE und Android -> Nur IE und Android (zumindest 2.2 getestet) cachen die Werte, die im Hintergrund geholt werden. Deswegen gibts bei diesen Browsern keine Updates mehr auf Werte, die einmal angezeigt wurden. Cache jetzt explizit abgeschaltet, damit funktioniert es in allen Browsern.
* Da bei einem Update webmatic deinstalliert werden muss, w�rden auch die eigenen ID Grafiken verloren gehen. Deswegen liegen diese ab sofort in einem eigenen addons Verzeichnis: webmatic_user. Dieses wird nicht installiert, und deswegen auch bei deinstallation nicht gel�scht. Also vor der Deinstallation euer img/ids Verzeichnis per FTP nach webmatic_user kopieren (Verzeichnis muss angelegt werden). Die Idee ist auch, dass man sich dort kleine HTML Seiten anlegen kann, wenn man diese als IFrame f�r ReadOnly Variablen braucht, da sie eben bei Installation von neuer Version erhalten bleiben.
* Fix f�r iPhone 5 Bildschirmformat -> Keine schwarzen Balken mehr wenn �ber HomeScreen Button gestartet. Wichtig -> Homescreen Icon muss neu angelegt werden!
* Englischer Text in Filtern ersetzt -> "Daten filtern...".
* Fehlertexte bei Ger�ten anzeigen, daf�r "Kein Fehler" nicht mehr anzeigen, braucht nur Platz und ist �berfl�ssige Information. Ein paar Ger�te fehlen noch (Rauchmeler, CO Melder, ...), dort wird Fehler anzeigt, aber nur mit Nummer.

1.0
* Refresh Timer bei jedem Laden einer Seite neu starten.
* Haftungsausschluss in About.
* Installer.
* CGIs durchschauen und unn�tiges rauswerfen.

0.6
* Eingeben von <img src='blabla'/> in Textvariablen bringt Fehler. Korrigiert. Es kann jetzt eigentlich alles eingef�gt werden. Nur werden " durch ' ersetzt, sonst gibt es Probleme. Au�erdem ist <SCRIPT> leider nicht m�glich.
* Bei SetPoint nicht Seite neu laden, sondern Text mit Hinweis schreiben, dass der Wert nicht sofort �bernommen wird.
* Variablen ReadOnly, wenn in Beschreibung (r) oder (R) steht.
* Beschreibung von Variablen mit anzeigen.
* Nachkommastellen bei Zahlen abschneiden, wenn es 0en sind.
* Werte bei (r) mit gew�hltem Inhalt anzeigen und nicht nur true/false.
* JS, CSS und HTML aufteilen, CGIs in Unterverzeichnisse.
* Pfad bei Bildern noch mit angeben bei den Grafik IDs.
* Setzen von Kommazahlen bei Variablen. Geht nicht dynamisch, ist jetzt auf zwei Nachkommastellen.
* Name auf WebMatic umgestellt (inkl. Icons, muss man auf iOS neu auf Desktop anlegen).

0.5
* Bool und Wertelisten �ber Buttongroups -> Wertelisten und Alarmzone hat Zustand.
* 20/40/60/80% Schnellzugriffe bei Jalousien, WinMatic und Dimmern.
* jQuery und LazyLoader lokal mit ausliefern.
* Bei 20/40/60/80 Schnellzugriffen auch Button Group und aktuell eingestelltes markieren.
* Kleineres Layout f�r Phones bzw. Menu und Daten jeweils Vollbild (primary / secondary content). Erst mal einfache Variante mit Menu dar�ber.
* Thermostate Schnellzugriff +* 3� in ganzen Grad Schritten.
* Nach dem Setzen eines Wertes Refresh. Position wird gemerkt und scrollt wieder dahin. Nach Refresh Button gehts auch zur�ck zur alten Position. Vor�bergehende L�sung, sp�ter nur den ge�nderten Wert neu lesen.
* W�hrend Update l�uft auch Animated Icon in Toolbar anzeigen. Denn jetzt kann ein Update ja auch laufen, wenn man nach unten gescrollt ist, dann sieht man das Loading oben nicht.
* Image Verzeichnisse umsortieren. User Grafiken sind jetzt in Unterverzeichnissen favorites/functions/rooms.
* Reihenfolge Favoriten / R�ume / Gewerke auch in der Bild ID Seite rein.
* Titel linksb�ndig, weil sonst von Icons �berdeckt auf Mobile.
* Automatischen Update alle 60 Sekunden inkl. Servicemeldungen. Fest eincodiert f�rs erste, der Timer l�uft immer wieder von vorne los. Sp�ter Timer reseten, wenn man eine Seite von Hand geladen hat.

0.4
* "Lade..." jetzt auch bei Variablen, Programmen etc.
* Bei Servicemeldungen wird der Rest vom Bildschirm abgedunkelt, damit klar ist, dass man da nichts ausw�hlen kann.
* Schlie�en Knopf links oben bei Servicemeldungen.
* Die HTML Seiten haben jetzt ein no-cache Metatag, damit der Browser die Seite immer neu l�dt. Das passiert eh nur beim Start, weil
  danach passiert alles innerhalb der Webseite. Aber ohne das Tag habe ich das Problem, dass manche Browser nach einem Update der HTML
  erst nach einer Weile die HTML neu laden. Passiert z.B. auf dem iPad.
* ERROR_REDUCED, ERROR_OVERLOAD und ERROR_OVERHEAT rausgenommen aus der Anzeige, da wohl nicht gebraucht.
* Zusammenfassen von zus�tzlichen Buttons z.B. bei Jalousie, dass da nicht jeder sein eigenes "Vor x Stunden" hat -> WinMatic, KeyMatic und Dimmer noch sch�ner sortieren.
* Zentralennetzteil sch�n machen.
* Manchmal doppelte Favoriten -> HomeMatic legt manchmal Referenzen zwischen Favoriten intern an, diese werden jetzt �bersprungen.
* Bool und Wertelisten �ber Buttongroups -> Noch nicht ganz fertig, geht noch nicht f�r Wertelisten und Alarmzone hat keinen Zustand.

V0.3
* Neue hochaufl�sende Grafiken f�r Retina Display (160x160).
* HomeMatic Forum wird im About Dialog verlinkt.
* Shutter Kontakt Offen = rot, Geschlossen = gr�n.
* Jalousie 0-1 -> 0-100.
* Automatisches hochscrollen bei Klick auf Menu.
* Aktuell gew�hlten Listeintrag im Menu links visualisieren.
* Refresh Knopf aktualisiert auch die Servicemeldungen.
* Visualisierungen f�r bekannte Ger�te (Screenshots Alen).
* Debug abschalten oder IDs auf ungef�hrlichen Wert oder 0 und abfangen.
* Dimmer bedienbar.
* �berschriften auf primary content nicht immer korrekt bzw. bleiben stehen. Z.B. bei Umschaltung von Grafik IDs zu Programme.
* "Loading..." w�hrend Liste geladen wird.

0.2
* Erste M�glichkeit zum Setzen von Werten bei Thermostaten.
* Animation w�hrend Servicemeldungen geladen werden. Farbig, wenn Meldungen vorhanden. Datum der Meldung anzeigen.
* Versionsnummer in Titelleiste anzeigen.
* Update Button, sp�ter dann durch automatische Updates erg�nzen. Momentan nur Update auf aktuelle Seite, keine Servicemeldungen.
* Programmliste unter Sonstiges.
* Servicemeldungen sch�ner stylen.
* Filter auf rechter Seite hinzugef�gt.
* Paralleles Laden der Daten beim Start.
* Texte von Servicemeldungen sch�ner.
* Grafik-ID Liste unter Sonstiges.
* Variablenliste unter Sonstiges.
* Farben in Servicemeldungen (Je nachdem ob Info, Warnung oder Fehler).
* Umbruch in Menu erzwungen, wenn Text keinen Platz mehr hat.
* Farbiger Status f�r Werte.
* LazyLoading von Grafiken mit jquery-lazyloading.js Library, wenn keine User GFX da, dann Standard anzeigen f�r R�ume, Gewerke und Favoriten.
* 3D Grafiken f�r gro�e Icons.
* "Vor 43 Jahren" ersetzen durch "Noch nicht ver�ndert".
* Tastendr�cke Lang und Kurz bedienbar.
* Min/Max und Einheiten dazuschreiben.
* Programme ausf�hren.
* Favoriten in Liste nach oben.
* Bedienen von Zahlen, Bool und Texten in Variablen.
* Bezeichnungen bei Bool verwenden statt true/false.
* Wertelisten setzbar machen.

0.1
* rooms.cgi, functions.cgi und favorites.cgi f�r �bersichten.
* channels.cgi f�r Ger�te pro Gew�hltem Raum/Gewerk/Favorit.
* jQuery Mobile Seite mit links R�umen/Gewerken/Favoriten und rechts dann Ger�te des gew�hlten Menus.
* Erste Grafiken f�r Temperatur und Feuchte.
* Datum / Uhrzeit mit in JSON schreiben f�r korrekten Zeitvergleich.
* On/Off steht falsch!
* iPad HomeScreen enabled.
* Channelnamen vollst�ndig anzeigen.
* Bilder aus img/ids/<nr>.png lesen. User k�nnen damit eigene Bilder f�r R�ume, Gewerke und Favoriten anlegen. 
* Variablen lesen und anzeigen.
* _USER1004, PC (202) und PDA(203) rausnehmen. USER an Name, PC und PDA an Nummer.
* Icon in richtiger Gr��e f�r Retina etc.
* Gerendertes Icon.
* Menu immer nur ein Unterbereich aufklappbar.
* Sonstiges mit vereinfachtem Programme und SysVars eingef�gt.
* Was passiert bei Separator oder Programmen in den Favoriten -> Separator kommt gar nicht an, Program kommt an, eingef�gt.
* "About"-Dialog.
* Servicemeldungen.
* Fixed Titlebar.
* Datum bei Programmliste (Vereinfacht, sp�ter sch�ner).
* Datum bei Variablenliste (Vereinfacht, sp�ter sch�ner).