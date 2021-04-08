M300 - LB02
====

## Docker

#### Übersicht

Docker ist eine Software zur Containevirtualisierung von Anwendungen. Mithilfe der Containevirtualisierung können Anwendungen unabhängig vom unterliegenden Betriebsystem verwendet werden. Die Container sind auch abgeschottet von anderen Container, die auf dem Betriebsystem laufen.

#### Wissensstand

Ich habe grundlegende Kenntnisse von Linux und bereits erste Erfahrungen zum Thema Vagrant gesammelt. Ich habe bereits zuvor von Docker gehört, allerdings noch nie damit zu tun gehabt.


#### Befehle
                            
							
| Befehl                       | Effekt                         |
| ---------------------------- |:------------------------------:|
| docker stats | Zeigt ressourcennutzung der Container in Echtzeit |
| docker info | Zeigt Informationen zum System |
| docker login | Im Docker Hub anmelden |

                                        
| Befehl                       | Effekt                         |
| ---------------------------- |:------------------------------:|
| docker pull *imagename* | Lädt das Image vom Docker Hub herunter  |
| docker run --name *imageID* | Startet ein bestimmtes Image |
| docker run -it *imageID* | Startet ein bestimmtes Image und zeigt die Befehlszeile an |
| docker build -t *imagename* | Erstellt ein Image vom Dockerfile mit dem festgelegten Namen im Verzeichnis |
| docker images | Zeigt eine Übersicht der Images an |
| docker image rm *imagename* | Löscht das Image |
| docker image rmi *imagename* | Löscht das Image |
| docker rmi `docker images -q -f dangling=true` | Zwischenimages löschen |

                                                
| Befehl                       | Effekt                         |
| ---------------------------- |:------------------------------:|
| docker start *ContainerID* | Startet den Container |
| docker container ls | Zeigt alle laufenden Container an. |
| docker container start -i *containername* | Startet einen gestoppten Container |
| docker container stop *containername* | Stoppt den laufenden Container. |
| docker kill | Stop den Hauptprozess des Containers |
| docker network ls | Zeit alle Netzwerke an. |
| docker rm -f $(docker ps -aq) | Löscht alle laufenden und gestoppten Container |
| docker logs --tail 100 *containername* | Zeigt die 100 letzten Zeilen des Container logs an. |
| docker ps  | Zeigt alle aktiven Container an |
| docker ps -a | Zeigt alle Container an |
| docker run --rm -d -p 3306:3306 mysql | Mysql an port 3306 binden für Internetzugriff |
| docker inspect *containername* | Zeigt Infos zum Container an |


#### Mögliche Angriffe

- Kernel Exploit
- Denial-of-Service (DoS)
- Container Breakouts
- Vergiftete/manipulierte Images


#### Massnahmen zur Containersicherheit

- Least Privilege
- Ressourcen begrenzen
- Container nach Host trennen
- Container absichern


## Kubernetes

#### Einführung

Kubernetes ist ein Open-Source system zur Bereitstellung, Skalierung und Verwaltung von Container-Anwendungen. Docker ist dabei nur eines der Container-Tools, die von Kubernetes unterstützt werden.
Da es Umgebungen geben kann, in denen zwei Container miteinander Kommunizieren müssen, werden Container in Kubernetes in Pods zusammengefasst, selbst wenn es sich nur um einen Container handelt.
Innerhalb eines Pods können die Container mittels eines 
Pods können untereinander kommunizieren und werden von sogenannten "Worker Nodes" verwaltet.
Mittels eines "Service" kann dann von aussen auf die Umgebung zugegriffen werden und er kümmert sich um das Load Balancing.
Mittels "Deployments" können ganze Umgebungen schnell und einfach aufgesetzt werden. Zudem stellt bei Deployments der Master sicher,dass das Deployments im "Desired state" bleibt. Wenn Pods direkt deployed werden, werden sie vom Master nicht wieder repariert.


#### Befehle

| Befehl                       | Effekt                         |
| ---------------------------- |:------------------------------:|
| kubectl create -f *datei* | Erstellt eine Ressource von einer Datei |
| Kubectl expose | ? |
| kubectl run *imagename*  | Startet das angegebene Image in einem Container und legt ihn in ein Pod |
| kubectl set | Updaten und Bearbeiten von Images, Environment variables, resources, usw. |
| kubectl explain *api-resource*  | Zeigt Details zu einer Ressource an. |
| kubectl delete *ressource name* | Löscht die angegebene Ressource. |
|  |  |
