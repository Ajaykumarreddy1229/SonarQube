# SonarQube 
## 1. What is SonarQube?

SonarQube is a tool used to check the quality of code.

It helps developers find problems in their code before releasing an application.

SonarQube can find:
- **Bugs:** Mistakes in the code.
- **Vulnerabilities:** Security problems in the code.
- **Code Smells:** Code that is difficult to understand or maintain.
- **Code Duplication:** The same code written in multiple places.
- **Code Coverage:** How much code is tested by test cases.

## 2. Why Do We Use SonarQube?

- To find mistakes in code.
- To improve code quality.
- To find security problems.
- To reduce duplicate code.
- To make code easier to maintain.
- To check code automatically during the CI/CD process.

## 3. What Is Static Code Analysis?

Static code analysis means checking the code without running the application.

SonarQube reads the code and finds possible problems.

**Example:** If a developer writes code that may cause an error, SonarQube can report that problem.

## 4. Install Docker on Ubuntu

First, update the packages:

```bash
sudo apt-get update
```

Install the required packages:

```bash
sudo apt-get install ca-certificates curl gnupg -y
```

Add the Docker key:

```bash
sudo install -m 0755 -d /etc/apt/keyrings

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

sudo chmod a+r /etc/apt/keyrings/docker.gpg
```

Add the Docker repository:

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Install Docker:

```bash
sudo apt-get update

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
```

Start Docker:

```bash
sudo systemctl enable --now docker
```

Check Docker:

```bash
sudo docker --version
```

## 5. Install SonarQube Using Docker

Run this command to start SonarQube:

```bash
docker run -d --name sonar -p 9000:9000 sonarqube:community
```

Check whether the container is running:

```bash
docker ps
```

Check the logs:

```bash
docker logs -f sonar
```

Open your browser and enter:

```text
http://<SERVER-IP>:9000
```

For your own computer, use:

```text
http://localhost:9000
```

Default login details:

- Username: `admin`
- Password: `admin`

Change the password when asked.

## 6. What Is Maven?

Maven is a tool used to build Java applications and manage their dependencies.

Maven helps to compile code, run tests, and create application files.

## 7. What Is JaCoCo?

JaCoCo is a Java code coverage tool.

It checks how much of the code is tested when test cases run.

Example:

If your application has 100 lines of code and tests cover 80 lines, the line coverage is 80%.

To generate a report, configure the JaCoCo plugin in your `pom.xml` and run:

```bash
mvn clean verify
```

The report is usually available at:

```text
target/site/jacoco/index.html
```

## 8. What Is Jenkins?

Jenkins is an automation tool used in CI/CD.

It can automatically build code, run tests, and start other tasks whenever developers update their code.

Jenkins can also run SonarQube analysis during the pipeline.

## 9. How Do Jenkins, Maven, and SonarQube Work Together?

The process is simple:

1. Developers upload code to GitHub.
2. Jenkins downloads the code.
3. Maven builds the application.
4. Maven runs the tests.
5. JaCoCo creates the code coverage report.
6. SonarQube checks the code quality.
7. Developers fix the reported problems.
8. The application can be deployed after the required checks pass.

## 10. What Is a Quality Gate?

A Quality Gate checks whether the code meets the required quality rules.

For example, a team may require a certain level of test coverage or no new critical security issues.

If the conditions are not met, the quality gate can fail. Jenkins can be configured to stop the pipeline when this happens.

## 11. Real-Time Example

Imagine a company is developing a website.

Several developers write code for the website. Sometimes, their code may contain bugs or security problems.

The company uses Jenkins and SonarQube.

- Jenkins builds the code automatically.
- Maven runs the tests.
- SonarQube checks the code.
- The team reviews and fixes the problems.
- The application is deployed after the required checks pass.

This helps the company maintain good code quality.

## 12. Important Commands

| Command | Use |
|---|---|
| `docker ps` | Check running containers |
| `docker ps -a` | Check all containers |
| `docker logs -f sonar` | View SonarQube logs |
| `docker stop sonar` | Stop SonarQube |
| `docker start sonar` | Start SonarQube |
| `docker restart sonar` | Restart SonarQube |
| `mvn clean` | Remove old build files |
| `mvn test` | Run tests |
| `mvn clean verify` | Build the project and run verification steps |
| `mvn sonar:sonar` | Run SonarQube analysis |

## 13. Quick Revision

- **SonarQube:** Checks code quality.
- **Docker:** Runs applications in containers.
- **Maven:** Builds Java applications.
- **JaCoCo:** Measures code coverage.
- **Jenkins:** Automates the build and testing process.
- **GitHub:** Stores and shares code.
- **Quality Gate:** Checks whether code meets the required quality rules.

### Conclusion

SonarQube helps developers find code problems early. When we use SonarQube with Maven and Jenkins, we can check code quality automatically during the CI/CD process.

**Topics:** SonarQube | Docker | Maven | JaCoCo | Jenkins | DevOps | CI/CD
