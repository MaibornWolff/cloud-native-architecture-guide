# Part 2 Build Applications on Serverless cloud services
{: .no_toc}
* TOC
{:toc}    


## What is the term "Serverless" about?
Früher hat man damit immer AWS lambdas oder Azure Functions mit in Verbindung gebracht.

Bei serverless drehte sich vor allem am Anfang alles um Architekturideen wie man Applikationen auf Basis einer vielzahl von kleinteiligen functions aufbauen kann. Entweder auf cloud provider nativen Umgebungen wie Lambda oder Frameworks wie Knative oder dem "serverless framework". (Links)

Das ist nicht falsch, allerdings ist Serverless inzwischen mehr und der gebrauch des Begriffs hat sich etwas verschoben. AWS hat als Beispiel auch den S3 Storage unter serverless laufen. Azure bezeichnet bei vielen services die einfache betriebsmodelle als "serverless" betriebsmodell, da es oft eine hohe abstraktstionsebene ist mit dem gerinsten kontakt zu operations.

Serverless bedeutet die betriebsaufwände für cloudnative apps auf ein minimum zu beschränken ohne die notwendigkeit zur verwaltung von einzelnen Hosts vms oder nodes. Die Entwicklung fokussiert auf inhalte und nicht betrieb. Ein Datenbankservice, wo es keine Rolle spielt auf wieviel verteilten host instanzen der Dienst läuft und nur noch nach Consumptions abgrechnet anstatt von Betriebsstunden ist genauso serverless wie ein Kubernetes Cluster, dass nur noch als Controllplane genutzt werden kann und einzelne nodes keine Rolle mehr spielen.

Cloud native Applikationen machen soviel Gebrauch wie nur möglich von serverless basierten Cloud Services um den Fokus auf die Entwicklung von fachlichen Use Cases zu legen anstatt in die Betriebnahme von infrastruktur viel Zeit in Konfufuration der richtigen Sklalierung. Eine Application startet in der Regel in der modernen Anwendungsentwicklung mit einem PoC aus dem dann ein MVP wird. Später mit wachsenden Bedarf von Anforderungen und User steigt der workload in dem System. Durch Consumption basierte Abrechnung sklalieren auch die Kosten mit der Größe der Anwendung. Serverless Services kosten in der Regel bei geringen Workload sehr wenig. Häufig sind sogar die ersten Milliionen Aufrufe kostenlos. Ein Upfront invest in Computing- oder Storage-Instanzen ist nicht notwendig. Noch krasser wird der unterschied, wenn das System mit wenig Last, aber über georegionen verteilt starten muss. Der Upfront invest in Instanzen wäre in diesen deutlich höher, wenn keine Nachteile durch Latenzen entstehen soll.

Ergänzend muss aber bedacht werden, dass es Situationen gibt, wo workload auf gekauften instanzen günstiger sein kann. Oft bei hoher gleichbleibener Last übersteigen irgendwann die Serverless Kosten die Kosten für Instanzen. Allerdings muss hier auch der erhöhte Betriebsaufwand kalkuliert werden.

## Was sind Servless Functions?
Serverless meets Functions - a perfect match

Als Serverless Functions bezeichnet man Services in der Cloud, die es Entwicklern ermöglicht in der Art und weise einer klassischen function einer beliebigen Hochsprache Code zu schreiben und zu deployen ohne dabei hostrelevante Aufgaben zu implementieren, wie zum Beispiel das Steuern eines Anwendungs-Lifecycles oder das listeings on ports.

Da man bei functions sich nicht mehr um das lifecycle management eines spezifischen Host kümmert, sind functions per design event getrieben. Es gibt immer irgendeine Art von Trigger um die function auszuführen. Das Event, das den Aufruf triggert, kann zum Beispiel eine Nachricht auf einem Message bus, ein Aufruf eines HTTP Endpunktes, ein neuer Datensatz in einem Storage oder auch ein Zeitlich gesteuertes Ereignis sein. Für viele verschiedene Triggertypen, ist es ein Einzeiler sich auf ein das Ergeignis als Empfänger zu binden.

Da die Natur einer Function in der Informatik aus input -> verarbeitung -> output besteht, ist es in diesem Kontext nicht nur möglich den Input an ein Event zu binden, sondern auch den Output direkt mit einer geeigneten Ausgaberesource wie zum Beispiel eine Datenbanktabelle oder eine Messagequeue.

![](./images/input_output.png)

Damit sind Functions sind ein perfekter match für Serverless, da keinerlei aufwände im Code entstehen um einen Host zu steuern und durch die einfachen input und output bindings auch kaum Querschnittscode. Es reduziert sich der Entwicklungsaufwand fast ausschließlich auf Fachlichkeit und nicht darauf wo diese läuft.

Natürlich läuft der code "irgendwo". Wie in dem Bild zu sehen ist, wird der Aufgerufene Code von einer Art Runtime umgeben, die sich nicht nur um lifecycle kümmert, sondern oft auch functionalität für logging, tracing oder Authentifzierung oder Transportverschlüsselung.

Es gibt verschiedene Möglichkeiten wo eine Function Runtime laufen kann.In Hinlick auf Serverless, macht es Sinn eine Umgebung auszuwählen die Betriebsaufwände für die Runtime selbst weitesgehend reduziert.

## Hosting Modelle für Serverless Functions

Beispiele für betriebsmodelle Für die Runtime.

- einzelne Functions nur dafür geigenet kleine Tasks zu erfüllen
- Knative
- KEDA
- Serverless framework
- Google cloudrun
- ...

## Wie designed man Software mit Serverless Functions

### Fachliche domain in klassischen Microservices
Im Softwaredesign ist es in den allermeisten Fällen ein guter Ansatz sich an der fachlichen Domäne zu orientieren. bei einen Monolithen bestimmt die Struktur der Domäne den fachlichen Komponentenschnitt bei Microservices den Serviceschnitt. Ziel ist es, dass Services bzw. Komponenten fachlich so strukturiert sind, dass diese technisch möglich unabhängig agieren können. Bekannt als "High cohesion and low coupling". 
Auf dem folgenden  Bild ist ein klassischer Microservice approach abgebildet. Jeder Service ist für einen bestimmten abgrenzbaren Teil der Domäne zuständig und möglichst unabhängig von anderen Services. Jeder Service hat einen separierten Daten Layer und bietet je nach Bedarf verschiedene Kommunikationsschnittstellen an, wie z.B. REST API Endpunkte oder das senden und empfangen asynchroner Nachrichten. 
Hier abgebildet ist ein Hexagonaler Architekturansatz, der die Domäne in den Mittelpunkt der Entwicklung von Microservices stellt. direkt um die Domain legt sich die Applikationsschicht, die keinerlei eigene Logik enthällt sondern ein Wrapper zum starten der Domain ist. Auf der äußersten Schicht befindet sich der Adapter layer, der die Domain mit konkreten externen ressourcen, wie zum Beispiel Datenbanken, Messagebroker oder anderen Microservices über Clients verbindet. Auch bereitgestellte API's werden über den Adapterlayer abgebildet. (Links zu div. Maibornwolff Blogs über DDD - Silas z.B.)

![](./images/microservices.png)

Pattern wie Domain Driven Design lassen sich besonders dann optimal anwenden, wenn der Serviceschnitt fachlich orentiert ist. Bei einem guten design verteilt sich die Weiterentwicklung auch bei Microservices nicht über mehrere Anwendungsteile. 
Technisch gesehen, ist der Schnitt allerdings eher suboptimal. Da die Skalierung gleichzeitig für mehrere Eingangs- und auch Ausgangskanäle passiert. Die richtige Anzahl gewählter Instanzen pro Microervice kann nicht spezifisch für eine Ressource gewählt werden, da jede Skalierungsconfiguration immer den gesamten Service betrifft.

### Use a more fine grained approach
Eine klassische Abbildung eines Microservies auf Serverless functions sieht oft so wie auf der nächsten Abbildung aus. Es gibt für jede Eingangsressource eine eigene Serverless Function und damit eine eigene Applikation. In diesem Beispiel eine Function, die auf eingehende Nachrichten auf einer Queue hört und eine andere Function die bei einer bestimmten HTTP Methode getriggert wird.

![](./images/technical.png)

Damit löst sich das Problem, der technischen Skalierung. Für jede Serverless Function, kann jetzt die Skalierung abhängig des jeweiligen eingangstriggers optimiert werden. Dafür sorgt im Standardfall die Hostumgebung der Functions. 

Allerdings ist es jetzt ein technischer Schnitt und kein Fachlicher mehr. Es gibt jetzt 2 Domain kerne. Lösen diese, die gleiche Aufgabe, wie vorher ein einzelner Microservice, gibt es jetzt einen Splitt in der Domain. Das hat zur Folge, dass automatisch Abhängigkeiten zwischen den beiden functions entstehen. Die Nutzung der selben Datenbank und damit auch sehr ähnlichen Datenmodellen, führt zu deutlich mehr Code duplizierungen als vorher. Zwar ist es natülich möglich, Datenmodelle über gesonderte shared libs mit eigener Versionierung zu extrahieren. Das ist bei Microservices nicht ohne Grund ein Antipattern. Es erzeugt wieder Komplexität und Abhängigkeiten. 

### Virtual Components
Patterns, die sich bei Microservices etabliert haben, wie z.B. dass jeder Service nur seine Datenbank im Zugriff haben darf, kann beim Einsatz von Serverless Functions rein technisch sinnvollerweise nicht durchgesetzt werden.

Es stellt sich die Frage, ist denn eine einzelne Serverless Function überhaupt ein in sich geschlosserener Fachlicher Kontext wie einem fachlichen domain schnitt? Nein - eine Serverless Function erfüllt meistens nur einen kleinen technischen Aspekt eines größeren fachlichen Services. Das heißt aber auch, dass die Summe aller technischen Eventtrigger, die vorher in einem Microservice vereinigt waren, zusammen schon eine Domain bilden. Nur eben virtuell. Das ist auf jeden Fall eine wichtige Erkenntnis. Wenn man sich eine große Anwendung mit unterschiedlichen Domains vorstellt, die nun durch eine vielzahl Serverless Functions abgebildet wird und jede Functions auf beliebige Ressourcen und Datenschichten zugreift, nur weil Functions technisch motiviert designed werden, ensteht ein über die Zeit eine unwartbare Gesamtanwendung. 

Auch bei Anwendungen mit serverless Functions ist es möglich seine Anwendung nach Fachlichen Komponenten zu designen, indem Virtuelle Komponenten um Fachliche Domänen bildet wie auf der nächsten Abbildung zu sehen.

![](./images/virtual_component.png)

Im ersten Schritt können Regeln und Kontrakte für die Kommunikation zwischen den fachlichen Komponenten festgelegt werden. Zum Beispiel kann festgelegt werden, Functions sollten nur innerhalb einer komponente mit einem gemeinsamen Datenlayer interagieren dürfen und für Component zu Component nur asnychron über einen Messagebus. Anders gesagt, damit können viele Patterns, die sich beim Design mit Microservices etabliert haben wiederverwendet werden, nur dass sich technische Verarbeitung einzelner Aspekte auf verschiedene Runtimes aufgeteilt haben (Siehe folgende Abbildung).

![](./images/multi_component.png)

### Extract an domain core for every virtual component
Auch wenn die Aufteilung auf virtuelle fachliche Componenten ein guter erster Schritt ist, bleibt das Problem des verteilten Domänenkerns.
Auch dafür hat ein Solutionpattern entwickelt. Es ist natürlich möglich sowas wie ein Hexagonales Pattern in jeder Serverless Function kleinteilig abzubilden. Aber im Kern ist eine Serverless Function nicht anderes als ein spezifischer Einstiegspunkt in eine Applikation. Statt also jede Function als einen kleineren ganzheitlichen teil einer Applikation zu sehen, kann auch der Domain Kern vom Trigger, für den die einzelne Function zuständig ist, einfach trennen. Fachlich gesehen, designed man so wieder einen Fachlichen Domänenkern wie einem klassischen Microservice, löst aber die Applikationsschicht in eine eigene Anwendungsinstanz heraus. 

![](./images/external_domain_core.png)

Wie hier auf der Abbildung zu sehen ist, ist der Domainkern wieder vereint. Technisch wird je nach gewählter Sprache ein Package ohne Applikationsschicht gebaut. Auch der Adapterlayer bleibt um die Domäne gespannt und wird teil von diesem Package. So bleiben Zugriffe auf Datenbanken oder externen Ressourcen rein logisch an einer Stelle.
Die Serverless Functions wiederum referenzieren dieses Domainenpackage lediglich und sind technisch weiterhin auf 2 (oder mehr)Anwendungsruntimes aufgeteilt.  

Natürlich ist es möglich das domänen package als einzelnes Artefakt zu verstehen mit eigeigener pipeline und package versionierung. Allerdings ist das ein schon bei Microservices ein Antipattern gewesen, da shared libs oder models zwischen verschiedenen Services durch die unterschiedlichen Lifecycles unnötige Abhängigkeiten und die Komplextität erhöht haben. 
Hier geht es zwar nicht darum Abhängigikeiten zu reduzieren, da anders als Microservices alles Scope einer virtuellen Komponente ist, die Komplexität steigt aber trotzdem durch die unabhängige Versionierung.

Eine Alternative, die sich bei Serverless Functions bewährt hat, ist die folgende Projektstruktur (Siehe Bild). pro  virtuelle Business component gibt es eine Ordner top Level struktur. Darunter gibt es dann jeweils einen Ordner oder ein losgelöstes entkoppeltes Package für die Domäne und einen Ordner für jede Serverless Function Applikation. 
Jede Applikation referenziert das Domainpackage jetzt nicht über irgendeinen Artefaktstore, sondern direkt über die Ordnerstruktur zu buildzeit. Es gibt dann eine Pipeline pro virtuell Component, war bedeutet, dass jeder Change on der Komponente, egal ob an der Domain oder den Serverless Functions einen Build triggert. Die Anzahl der Artefakte, ist dann abhängig von der Anzahl der Functions.

![](./images/folder_structure.png)

### Finegrained vs coarse grained Application design

Oft wird Serverless fälschlicherweise mit der Notwendigkeit verbunden, nur noch sehr kleinteilige Applikationen zu bauen, und die gesamte Anwendung auf sehr viele isolierte Einheiten (Functions) zu verteilen. Aber nicht immer macht das für die entsprechende Domäne Sinn.

Mit dem Ansatz die Domäne unhabhängig von den Functions zu entwickeln, ist es möglich die Gesamtapplikation auch bei Serverless Functions zu fachlich zu designen. 
Trotzdem schließt das bei den meisten Serverless functions Frameworks keinen technischen Schnitt aus. Functions lassen in den gleichen Runtimes zusammenfassen oder gruppieren. So können zum Beispiel, alle Http Trigger für eine virtuelle Komponente in einer Runtime instanz bereitgestellt werden (siehe Bild). 
Alle Functions die zusammen gruppiert in einer Runtime laufen skalieren technisch jetzt wieder gemeisam. Das kann abhängig von gewählten Hosting umgebung vorteile beim Computebedarf, und somit kosten, oder auch latenzen haben. Theroretisch könnte man alle serverless functions einer virtuellen component zusammen über eine Runtime laufen lassen und z.B. Asynchrone Nachrichten Trigger zusammen mit HTTP Triggern. Dann hätte man wieder einen Microservice, nur mit Serverless Function gebaut. Oft macht deshalb einfach eine gruppierung der HTTP Functions sinn.

![](./images/share_runtime.png)

## Serverless Container

