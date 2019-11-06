# Exercise Dockerized Pipeline

Here you can find some tasks you can do. There is no order to the tasks.

Its best to clone the repository from GitHub <https://github.com/cicdday/micro-dockerized>. You can either use https or ssh, depending on your setup with GitHub.

---

## Task - Run locally

Try to run the application locally. You need docker for that. If you have the make commandline tool it will make your life easier. If not you can execute the command defined in the makefile manually. But you will need a git bash.

Requirements:

- Java JDK
- Maven
- Docker
- make (optional)
- Git Bash

### Build the application

First you need to build the actual application. For this we use maven.

```sh
make app-build
```

or

```sh
mvn clean install -f application/addressbook/
```

### Build the docker images

First you need to build the actual application. For this we use maven

```sh
make docker-build
```

or

```sh
./docker-compose.sh build
```

### Startup container

After the images are build, you can startup the application

```sh
make docker-up-local
```

or

```sh
./docker-compose.sh -f docker-compose.yaml -f docker-compose-local.yaml up -d
```

### Test application

You can test the application by calling the rest api.

### Shutdown container

```sh
make docker-down
```

or

```sh
./docker-compose.sh down --rmi all --volumes
```

### Advantage of make

Instead of executing everything you need one after another, you can combine everything with make.

```sh
make app-build docker-build docker-up-local
```

---

## Task - create branch

To demonstrate the branch functionality with jenkins, lets create a new branch.

Requirements:

- Git Bash

```sh
git checkout -b <branchname>
git push --set-upstream origin <branchname>
```

Verify in GitHub that the new branch is available in GitHub.

Now verify in Jenkins that the new branch is also visible. It may take a little time to register. If it is not coming up, you can trigger a scan of the repository with ``Scan Repository Now`` on the left side.

Every commit on that branch will trigger the build pipeline for that branch.

---

## Task - change business code

You can extend the business application a little, possibilities would be:

- Additional Rest Service (get for all )
- Extend the database model to include more attributes for the entity

> Hint:
>
> - The database is automatically setup with JPA. You don't need to write any sql script yourself.
> - Don't forget to extend the tests!

Requirements:

- Git Bash
- Eclipse

---

## Task - change build pipeline

During development it can happen that additional steps are necessary in the build pipeline. We want to extend the stages now and include a dummy sonar stage for quality analysis.

Requirements:

- Git Bash
- Editor (e.g. VSCode)

Make sure you are on a branch, before you change your jenkinsfile.

---
