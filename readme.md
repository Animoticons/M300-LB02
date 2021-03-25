M300 - LB02
====

## Docker

#### Übersicht

Docker ist eine Software zur Containevirtualisierung von Anwendungen. Mithilfe der Containevirtualisierung können Anwendungen unabhängig vom unterliegenden Betriebsystem verwendet werden. Die Container sind auch abgeschottet von anderen Container, die auf dem Betriebsystem laufen.

#### Wissensstand

Ich habe grundlegende Kenntnisse von Linux und bereits erste Erfahrungen zum Thema Vagrant gesammelt. Ich habe bereits zuvor von Docker gehört, allerdings noch nie damit zu tun gehabt.


#### Befehle

### Docker Allgemeine Befehle                                                 
| Befehl                       | Effekt                         |
| ---------------------------- |:------------------------------:|
| docker stats | Zeigt ressourcennutzung der Container in Echtzeit |
| docker info | Zeigt Informationen zum System |
| docker login | Im Docker Hub anmelden |


### Docker Build Befehle                                          
| Befehl                       | Effekt                         |
| ---------------------------- |:------------------------------:|
| docker build -t *imagename* | Erstellt ein Image vom Dockerfile mit dem festgelegten Namen im Verzeichnis |
| docker images | Zeigt eine Übersicht der Images an |
| docker image rm *imagename* | Löscht das Image |
| docker image rmi *imagename* | Löscht das Image |
| docker rmi `docker images -q -f dangling=true` | Zwischenimages löschen |


### Docker Run Befehle                                                  
| Befehl                       | Effekt                         |
| ---------------------------- |:------------------------------:|
| docker run --name *containername* *imagename* | Startet ein bestimmtes Image |
| docker container ls | Zeigt alle laufenden Container an. |
| docker container stop *containername* | Stoppt den laufenden Container. |
| docker kill | Stop den Hauptprozess des Containers |
| docker network ls | Zeit alle Netzwerke an. |
| docker rm -f $(docker ps -aq) | Löscht alle laufenden und gestoppten Container |
| docker logs --tail 100 *containername* | Zeigt die 100 letzten Zeilen des Container logs an. |
| docker ps  | Zeigt alle aktiven Container an |
| docker ps -a | Zeigt alle Container an |



## Vagrantfile

#### Festlegen der Box, welche die Maschine nutzen soll:

`config.vm.box = "ubuntu/xenial64"`

#### VM Name in VirtualBox festlegen:

`config.vm.provider "virtualbox" do |v|
  v.name = "VagrantLinuxVM" #VM Name setzen
end`

#### Es besteht auch die Möglichkeit, Linux-Befehle nach der Installation automatisch ausführen zulassen. Dafür wird folgende Struktur verwendet:

`config.vm.provision "shell", inline: <<-SHELL
 *Befehle Hier*
SHELL`

## Sicherheit

	

## Reflexion

Dieses Modul war für mich sehr Aufschlussreich. Endlich weiss ich, wie GitHub genau funktioniert und wie ich eine Vorlage für virtuelle Maschinen schreibe und mit ihr dann viele VMs mit einem einzigen Befehl hochziehe. Während Vargant abgesehen von der verwirrenden und unübersichtlichen Syntax des Vagrantfile sehr hilfreich ist, finde ich die Git-Befehle nicht hilfreich, da ich auf einem Betriebsystem mit GUI und Browser einfach die Dateien via Drag-and-Drop hochladen kann, was wesentlich intuitiver ist.