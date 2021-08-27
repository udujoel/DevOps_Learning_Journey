## Installation
- https://docs.sonarqube.org/latest/setup/get-started-2-minutes/
- https://www.sonarqube.org/downloads/

or use a Docker Image
```docker
docker pull sonarqube:latest
```
- then 
```docker
docker run -d --name sonarqube -e -p 9000:9000 sonarqube
```
- open localhost:9000 to access interface

Clone sample project: 
git clone https://github.com/gouthanmchilakala/petclinic.git