# Muster für microservicebasierte Webanwendungen

--------------------------------------------------------------------------------------
## Zentraler Zugangskontrolleur

### Kontext
%TODO: Aufschreiben :)

### Problem

### Zwänge

Folgende Zwänge wirken auf die Lösung ein:

* **:** 

### Lösung

### Konsequenzen

Folgende Erleichterungen bringt die Anwendung des Musters:

* **:** 

Das Muster bringt folgende Lasten:

* **:**

### Verwandte Muster

* 

--------------------------------------------------------------------------------------
## Geschütztes API-Gateway

Das **Geschützte API-Gateway** kontrolliert den Zugang auf eine Menge von Webservices.

### Kontext

Eine Webanwendung, die zur Bereitstellung der Funktionalität schützenswerte Webservices verwendet.

### Problem

Wie können Webservices vor unbefugtem Zugriff geschützt werden?
In einer serviceorientierten Architektur bieten Webservice schützenswerte Schnittstellen an.
Zwischen den Webservices besteht eine Vertrauensbeziehung und nicht alle Schnittstellen werden von externen Services
genutzt.
Wie kann der Zugang auf die Webservices kontrolliert werden?

### Zwänge

Folgende Zwänge wirken auf die Lösung ein:

* **Sicherheit:** Die Webservices bieten schützenswerte Schnittstellen an. Nur befugte sollen Zugriff auf die
				Schnittstellen erhalten.
* **Performanz:** Der Zugriff auf die Schnittstellen soll möglichst performant möglich sein.
* **Skalierbarkeit:** Die Lösung soll mit der Zahl der schützenswerten Webservices und Anfragen an diese
				skalieren.
* **Betriebskosten:** Der Betrieb der Lösung soll möglichst geringe Kosten verursachen.
* **Redundanz:** Die Lösung soll wenig redundant sein und so den Wartungsaufwand gering halten.

### Lösung

Führe die Services in einem **geschützten Bereich** aus, so dass diese sich gegenseitig aufrufen können. Biete über ein **API-Gateway** Zugang auf **Schnittstellen** (APIs), die laut **Autorisationsbeschreibung** von **externen Services** aufgerufen werden können sollen. Jede Anfrage wird vom API-Gateway auf ihre Autorisation überprüft.

### Konsequenzen

Folgende Erleichterungen bringt die Anwendung des Musters:

* **Sicherheit:** Anfragen an Webservices werden an zentraler Stelle auf ihre Autorisation überprüft und ein Zugriff über andere Wege verhindert.
* **Performanz:** Webservices innerhalb des geschützten Bereichs können sich ohne zusätzlichen Aufwand gegenseitig aufrufen.
* **Skalierbarkeit:** Der Zugang auf neue Webservices kann auch durch das geschützte API-Gateway kontrolliert werden. Es können zudem neue Instanzen des API-Gateway betrieben werden, falls die Anzahl der Anfragen steigt.
* **Betriebskosten:** Durch das zentralisieren und wiederverwenden der Zugangskontrollfunktionalität ist die Menge an zu betreibenden Instanzen reduziert.
* **Redundanz:** Die Zugangskontrolle wird an zentraler Stelle umgesetzt und ist nicht über Webservices verteilt.

Das Muster bringt folgende Lasten:

* **Sicherheit:** Es muss sichergestellt werden, dass Anfragen an die Webservices ausschließlich über das API-Gateway möglich sind.
* **Fehlertoleranz:** Ein Fehler in der zentralen Komponente kann zu uneingeschränktem Zugriff auf die Webservices führen. Das API-Gateway ist ein sogenannter Single Point of Failure.
* **Autonomie:** Die Zugangskontrolle wird im Geschützten API-Gateway zentralisiert und es müssen spezielle Lösungen eingesetzt werden, falls jeder Webservice diese autonom verwalten können soll.

### Verwandte Muster

* Das **API-Gateway** ([Ri16]) bietet die Basis für das Geschützte API-Gateway} und bietet eine Lösung für fachliche Anforderungen an eine Microservice-Architektur. Das vorliegende Muster ergänzt das API-Gateway um den **Autorisationsdurchsetzer**.
* Das **Geschützte API-Gateway** ist eine Spezialisierung des **Autorisationsdurchsetzers**. Die Lösung ist angepasst an die besonderen Zwänge von Webservices.
* Die **Haustür (Front Door)** ([Fe13]) ist eine generellere Variante des Musters, das den Zugriff auf eine Menge von Webservices über die Haustür beschreibt. Im Vergleich zu dem vorliegenden Muster werden in der Haustür Schnittstellen nicht speziell betrachtet.
* Die **entmilitarisierte Zone (engl. demilitarized zone, DMZ)** ([Fe13]) ist ein Weg, die Webservices vor externem Zugriff auf Netzwerkebene zu schützen und so das Geschützte API-Gateway zu dem einzigen Einstiegspunkt zu machen. Hierfür sieht das Muster die Verwendung zweier Netzwerke und einer Firewall vor.

--------------------------------------------------------------------------------------
## Lokaler Zugangskontrolleur

### Kontext
%TODO: Aufschreiben :)

### Problem

### Zwänge

Folgende Zwänge wirken auf die Lösung ein:

* **:** 

### Lösung

### Konsequenzen

Folgende Erleichterungen bringt die Anwendung des Musters:

* **:** 

Das Muster bringt folgende Lasten:

* **:**

### Verwandte Muster

* 

--------------------------------------------------------------------------------------
## Abfangender Anwendungsserver}

### Kontext
%TODO: Aufschreiben :)

### Problem

### Zwänge

Folgende Zwänge wirken auf die Lösung ein:

* **:** 

### Lösung

### Konsequenzen

Folgende Erleichterungen bringt die Anwendung des Musters:

* **:** 

Das Muster bringt folgende Lasten:

* **:**

### Verwandte Muster

* 

--------------------------------------------------------------------------------------
## Microservice-Zugangskontrolleur}

### Kontext
%TODO: Aufschreiben :)

### Problem

### Zwänge

Folgende Zwänge wirken auf die Lösung ein:

* **:** 

### Lösung

### Konsequenzen

Folgende Erleichterungen bringt die Anwendung des Musters:

* **:** 

Das Muster bringt folgende Lasten:

* **:**

### Verwandte Muster

* 

--------------------------------------------------------------------------------------
# Zugriffskontrollmuster

--------------------------------------------------------------------------------------
## Webservice-Zugriffskontrolleur

% TODO: Muster wurde in Kontrolleur umbenannt

Der \textsc{Webservice-Autorisationsdurchsetzer} setzt die Autorisation lokal am Webservice durch.

### Kontext

Eine Webanwendung, die zur Bereitstellung der Funktionalität einen schützenswerten Webservice verwendet.

### Problem

Wie kann die (feingranulare) Autorisation für einen Webservice und dessen Daten durchgeführt werden?
Über einen Webservice werden schützenswerte Schnittstellen angeboten.
Wie kann die missbräuchliche Interaktion mit dem Webservice verhindert werden?

### Zwänge

Folgende Zwänge wirken auf die Lösung ein:


* Autonomie:} Der Webservice soll autonom ausgeführt werden können und von wenigen anderen Webservices
				abhängen.
* Sicherheit:} Die Schutzziele des Webservices und der von diesem bearbeiteten Daten sollen gewahrt werden.


### Lösung

Fange Anfragen an Webservices ab und prüfe deren Autorisation. Gewähre den Zugang auf den Webservice oder lehne Anfragen
ab, je nach Ergebnis der Autorisationsprüfung.

### Lösungsvarianten}

Die Prüfung der Autorisation kann entweder invasiv bei der Ausführung des Webservices oder ausgelagert vor der
Ausführung des Webservices stattfinden.

Als nicht-invasive Variante kann der Autorisationsdurchsetzer auf Ebene des Applikationsservers eingesetzt werden.
Diese Variante wird oft als Zugangskontrolle umgesetzt und durch eine Zugriffskontrolle im Webservice ergänzt,
da bei feingranularer Autorisation Daten des Webservice benötigt werden könnten.

### Konsequenzen

Folgende Erleichterungen bringt die Anwendung des Musters:


* Autonomie:} Der Webservice hat durch die Implementierung des Autorisationsdurchsetzers die Kontrolle
				über die Implementierung der Zugangs- und Zugriffskontrolle.
* Sicherheit:} Die spezifizierte Autorisation wird durch die Anwendung des Musters durchgesetzt.


Das Muster bringt folgende Lasten:


	\item	Skalierbarkeit:} Die Autorisation jedes Webservices wird dezentral gespeichert und verwaltet oder
				muss von zentraler Stelle geladen werden. Dies schränkt die Skalierbarkeit ein.
* Performanz:} Durch die dezentrale Autorisationsprüfung ist die Verwendung eines performanten Caches
				erschwert.
* Ressourcenauslastung:} Jeder Webservice bringt seinen eigenen Autorisationsdurchsetzer mit.


### Verwandte Muster


* Das Geschützte API-Gateway} ist eine Spezialisierung des Webservice-Autorisationsdurchetzers}s.
				Die Lösung ist angepasst an die besonderen Zwänge von Webservices.
* Der Intercepting Web Agent} \cite{SN06} ist eine Variante des Webservice-Autorisationsdurchetzers},
				der eine nicht-invasive Durchsetzung der Autorisation vorsieht.

--------------------------------------------------------------------------------------
## Lokaler Zugriffskontrolleur}
\label{pat:local_dac}

### Kontext
%TODO: Aufschreiben :)

### Problem

### Zwänge

Folgende Zwänge wirken auf die Lösung ein:


* **:** 


### Lösung

### Konsequenzen

Folgende Erleichterungen bringt die Anwendung des Musters:


* **:** 


Das Muster bringt folgende Lasten:


* **:**


### Verwandte Muster


* 


## Abfangender Webagent}
\label{pat:intercepting_dac}

### Kontext
%TODO: Aufschreiben :)

### Problem

### Zwänge

Folgende Zwänge wirken auf die Lösung ein:


* **:** 


### Lösung

### Konsequenzen

Folgende Erleichterungen bringt die Anwendung des Musters:


* **:** 


Das Muster bringt folgende Lasten:


* **:**


### Verwandte Muster


* 

--------------------------------------------------------------------------------------
## Lokaler Zugiffskontrolleur}
\label{pat:ms_dac}

### Kontext
%TODO: Aufschreiben :)

### Problem

### Zwänge

Folgende Zwänge wirken auf die Lösung ein:


* **:** 


### Lösung

### Konsequenzen

Folgende Erleichterungen bringt die Anwendung des Musters:


* **:** 


Das Muster bringt folgende Lasten:


* **:**


### Verwandte Muster

* 

--------------------------------------------------------------------------------------
# Authentifizierungsmuster
--------------------------------------------------------------------------------------

## Anwendungslokale Authentifizierung



### Kontext

### Problem

### Zwänge

Folgende Zwänge wirken auf die Lösung ein:

* **:**

### Lösung

### Konsequenzen

Folgende Erleichterungen bringt die Anwendung des Musters:

* **:**

Das Muster bringt folgende Lasten:

* **:** 

### Verwandte Muster

*


--------------------------------------------------------------------------------------
# Administrationsmuster
--------------------------------------------------------------------------------------

%<<<<<<<<<<<<<<<<<<<<< MUSTERVORLAGE =====================
%## 
%
%### Kontext
%
%### Problem
%
%### Zwänge
%
%Folgende Zwänge wirken auf die Lösung ein:
%
%* **:**
%
%### Lösung
%
%### Konsequenzen
%
%Folgende Erleichterungen bringt die Anwendung des Musters:
%
%* **:**
%
%Das Muster bringt folgende Lasten:
%
%* **:** 
%
%### Verwandte Muster
%
%*
%
%===================== MUSTERVORLAGE >>>>>>>>>>>>>>>>>>>>>>>>>


[Ri16]: Ri16