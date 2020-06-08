# Wconomy Bill Tracker

## Getting Started

### Running Latest Version

#### Prerequisites
- Install [Docker Desktop](https://docs.docker.com/docker-for-mac/install/).

#### Running
1. Pull Docker Image
```
$ docker pull pausehyeon/billtracker:latest
```

2. Run Docker Container
```
$ docker run -p 8080:8080 pausehyeon/billtracker:latest
```

3. Open a browser and Check http://localhost:8080


### Building And Running Locally

#### Prerequisites
- Install [Java SE Development Kit 8](https://www.oracle.com/java/technologies/javase-jdk8-downloads.html).
- Install [Docker Desktop](https://docs.docker.com/docker-for-mac/install/).
- Install [Git](https://git-scm.com/downloads).

#### Running
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
# /d/workspace/wconomy-bill-tracker/billtracker
$ cd wconomy-bill-tracker/billtracker && curl -s https://raw.githubusercontent.com/pausehyeon/devops-environment/master/java/v1/Dockerfile --output Dockerfile
```

3. Make executable JAR
```
# /d/workspace/wconomy-bill-tracker/billtracker
$ ./gradlew build

# (Optional) If you got error message about permission(e.g. The file './gradlew' is not executable by this user), Make the gradle wrapper executable and Try again.
$ chmod +x ./gradlew
```

4. Build Docker Image
```
# /d/workspace/wconomy-bill-tracker/billtracker
$ docker build -t pausehyeon/billtracker:latest .
```

5. Run Docker Container
```
$ docker run -p 8080:8080 pausehyeon/billtracker:latest
```

6. Open a browser and Check http://localhost:8080
