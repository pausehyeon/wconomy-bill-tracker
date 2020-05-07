# Wconomy Bill Tracker

## Getting Started
### Prerequisites
- Install [Java SE Development Kit 8](https://www.oracle.com/java/technologies/javase-jdk8-downloads.html).
- Install [Docker Desktop](https://docs.docker.com/docker-for-mac/install/).
- Install [Git](https://git-scm.com/downloads).

### Running
Make a new workspace(e.g. /d/workspace).
Right click from the workspace directory; then you will see 'Git Bash Here'.
Now, Follow next steps from git bash.

1. Download Project Source Files
```
# /d/workspace/
$ git clone https://github.com/pausehyeon/wconomy-bill-tracker.git
```

2. Download A Dockerfile
```
# /d/workspace/devops
$ mkdir devops && cd devops && curl -s https://raw.githubusercontent.com/pausehyeon/devops-environment/master/java/v1/Dockerfile --output Dockerfile
```

3. Make executable JAR
```
# /d/workspace/wconomy-bill-tracker/billtracker
$ cd ../wconomy-bill-tracker/billtracker/ && ./gradlew build
```

4. Build Docker Image
```
# /d/workspace/devops
$ cd ../../devops && docker build --build-arg JAR_FILE=../wconomy-bill-tracker/billtracker/build/libs/*.jar -t wconomy.pe.kr/billtracker .
```

5. Run Docker Container
```
$ docker run -p 8080:8080 wconomy.pe.kr/billtracker
```

6. Open a browser and Check http://localhost:8000
