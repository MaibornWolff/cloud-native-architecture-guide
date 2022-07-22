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
Im Softwaredesign ist es in den allermeisten Fällen ein guter Ansatz sich an der fachlichen Domäne zu orientieren. bei einen Monolithen bestimmt die Struktur der Domäne den fachlichen Komponentenschnitt bei Microservices den Serviceschnitt. Ziel ist es, dass Services bzw. Komponenten fachlich so strukturiert sind, dass diese technisch möglich unabhängig agieren können. Bekannt als "High cohesion and low coupling". 
Auf dem folgenden  Bild ist ein klassischer Microservice approach abgebildet. Jeder Service ist für einen bestimmten abgrenzbaren Teil der Domäne zuständig und möglichst unabhängig von anderen Services. Jeder Service hat einen separierten Daten Layer und bietet je nach Bedarf verschiedene Kommunikationsschnittstellen an. Das können z.B. REST API Schnittstellen aber auch ...

![](./images/microservices.png)

![](./images/technical.png)

![](./images/virtual_component.png)

![](./images/multi_component.png)

![](./images/external_domain_core.png)

![](./images/folder_structure.png)

Oft wird Serverless fälschlicherweise mit der Notwendigkeit verbunden, nur noch sehr kleinteilige Applikationen zu bauen, und die gesamte Anwendung auf sehr viele isolierte Einheiten (Functions) zu verteilen. Aber nicht immer macht das für die entsprechende Domäne Sinn.

Genauso falsch ist allerdings, dass Serverless Functions nur dann genutzt werden können, wenn kleinteilige Applikationen gebaut werden.

![](./images/share_runtime.png)



## serverless container (container apps, cloud run, etc)
am ende genau das gleiche wie nur etwas mehr fokus auf und flexibilität
